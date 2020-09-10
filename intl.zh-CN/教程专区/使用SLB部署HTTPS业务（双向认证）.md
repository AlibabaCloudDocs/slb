# 使用SLB部署HTTPS业务（双向认证）

要配置HTTPS双向认证的监听，您需要在配置监听时上传服务器证书和CA证书。

本指南中使用自签名的CA证书为客户端证书签名，完成以下操作配置HTTPS监听（双向认证）：

1.  [准备服务器证书](#section_klf_y5z_vdb)
2.  [使用OpenSSL生成CA证书](#section_cqz_pvz_vdb)
3.  [生成客户端证书](#section_jbr_hyz_vdb)
4.  [上传服务器证书和CA证书](#section_mdg_411_wdb)
5.  [安装客户端证书](#section_cts_cd1_wdb)
6.  [配置负载均衡双向认证监听](#section_p5w_zd1_wdb)
7.  [测试负载均衡服务](#section_q3q_r21_wdb)

## 步骤一：准备服务器证书

服务器证书用于用户浏览器检查服务器发送的证书是否是由自己信赖的中心签发的，服务器证书可以到阿里云云盾[证书服务](https://www.aliyun.com/product/cas?spm=a2c4g.11186623.2.11.nw2Pcs)购买，也可以到其他服务商处购买。

## 步骤二：使用OpenSSL生成CA证书

1.  运行以下命令在/root目录下新建一个ca文件夹，并在ca文件夹下创建四个子文件夹。

    ```
    sudo mkdir ca
     cd ca
     sudo mkdir newcerts private conf server
    ```

    其中：

    -   newcerts目录：用于存放CA签署过的数字证书（证书备份目录）。
    -   private目录：用于存放CA的私钥。
    -   conf目录：用于存放一些简化参数用的配置文件。
    -   server目录：存放服务器证书文件。
2.  在conf目录下新建一个包含如下信息的openssl.conf文件。

    ```
    [ ca ]
     default_ca = foo
     [ foo ] 
     dir = /root/ca
     database = /root/ca/index.txt
     new_certs_dir = /root/ca/newcerts
     certificate = /root/ca/private/ca.crt
     serial = /root/ca/serial
     private_key = /root/ca/private/ca.key
     RANDFILE = /root/ca/private/.rand
     default_days = 365
     default_crl_days= 30
     default_md = md5
     unique_subject = no
     policy = policy_any
     [ policy_any ]
     countryName = match
     stateOrProvinceName = match
     organizationName = match
     organizationalUnitName = match
     localityName = optional
     commonName      = supplied
     emailAddress    = optional
    ```

3.  运行以下命令生成私钥key文件。

    ```
      cd /root/ca
       sudo openssl genrsa -out private/ca.key
    ```

    运行结果如下图所示。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2750.png)

4.  运行以下命令并按命令后的示例提供需要输入的信息，然后回车，生成证书请求csr文件。

    ```
      sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **说明：** Common Name请输入您的负载均衡服务的域名。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2753.png)

5.  运行以下命令生成凭证crt文件。

    ```
      sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  运行以下命令为CA的key设置起始序列号，可以是任意四个字符。

    ```
      sudo echo FACE > serial
    ```

7.  运行以下命令创建CA键库。

    ```
      sudo touch index.txt
    ```

8.  运行以下命令为移除客户端证书创建一个证书撤销列表。

    ```
      sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    输出为：

    ```
    Using configuration from /root/ca/conf/openssl.conf
    ```


## 步骤三：生成客户端证书

1.  运行以下命令在ca目录内创建一个存放客户端key的目录users。

    ```
      sudo mkdir users
    ```

2.  运行以下命令为客户端创建一个key：

    ```
      sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **说明：** 创建key时要求输入pass phrase，这是当前key的口令，以防止本密钥泄漏后被人盗用。两次输入同一个密码。

3.  运行以下命令为客户端key创建一个证书签名请求csr文件。

    ```
      sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    输入该命令后，根据提示输入上一步输入的pass phrase，然后根据提示，提供对应的信息。

    **说明：** `A challenge password`是客户端证书口令（请注意将它和`client.key`的口令区分开，本教程设置密码为test），可以与服务器端证书或者根证书口令一致。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2757.png)

4.  运行以下命令使用步骤二中的CA Key为刚才的客户端key签名。

    ```
      sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    当出现确认是否签名的提示时，两次都输入y。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2758.png)

5.  运行以下命令将证书转换为大多数浏览器都能识别的PKCS12文件。

    ```
      sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    按照提示输入客户端client.key的pass phrase。

    再输入用于导出证书的密码。这个是客户端证书的保护密码，在安装客户端证书时需要输入这个密码。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2759.png)

6.  运行以下命令查看生成的客户端证书。

    ```
    cd users
     ls
    ```

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2760.png)


## 步骤四：上传服务器证书和CA证书

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。
2.  在实例管理页面，单击**创建负载均衡**。
3.  配置负载均衡实例，单击**立即购买**完成支付。

    本操作中网络类型选择**公网**，地域选择**华东1（杭州）**，详细配置信息请参见[创建负载均衡实例](/intl.zh-CN/用户指南/实例/创建负载均衡实例.md)。

4.  创建成功后，在实例管理页面，将鼠标移至实例名称区域，单击出现的铅笔图标，修改负载均衡实例名称。
5.  在选左侧导航栏，单击证书管理页签。
6.  单击**创建证书**。
7.  在创建证书页面，完成如下配置后，单击**确定**。
    -   **证书部署地域**：本教程中选择**华东1**。

        **说明：** 证书的地域和负载均衡实例的地域要相同。

    -   **证书类型**：选择**服务器证书**。
    -   **证书内容和私钥**：复制您的服务器证书内容和私钥。

        **说明：** 在复制内容前，您可以单击**导入样式**，查看正确的证书和私钥格式。更多详细信息请参见[证书要求](/intl.zh-CN/用户指南/证书管理/证书要求.md)。

8.  在负载均衡左侧导航栏，单击**证书管理**，然后单击**创建证书**，上传CA证书。
9.  在创建证书页面，完成如下配置后，单击**确定**。
    -   **证书部署地域**：本教程中选择**华东1（杭州）**。

        **说明：** 证书的地域和负载均衡实例的地域要相同。

    -   **证书类型**：选择**CA证书**。
    -   **证书内容**：复制您的CA证书内容。

        **说明：** 在复制内容前，您可以单击**导入样式**，查看正确的证书和私钥格式。更多详细信息请参见[证书要求](/intl.zh-CN/用户指南/证书管理/证书要求.md)。


## 步骤五：安装客户端证书

将生成的客户端证书安装到客户端。本教程以Windows客户端，IE浏览器为例。

1.  打开Git Bash命令行窗口，运行以下命令导出步骤三中生成的客户端证书。

    ```
    scp root@IPaddress:/root/ca/users/client.p12 ./
    ```

    **说明：** IPaddress是生成客户端证书的服务器的IP地址。

2.  在IE浏览器中导入下载的客户端证书。
    1.  打开IE浏览器，单击**设置** \> **Internet选项**。
    2.  单击内容页签，然后单击**证书**，导入下载的客户端证书。在导入证书时需要输入在步骤三时生成PKCS12文件的密码。

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2781.png)


## 步骤六：配置HTTPS双向认证监听

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。
2.  选择**华东1（杭州）**地域，单击已创建的负载均衡实例ID链接，或者单击**监听配置向导**。
3.  选择监听页签，单击**添加监听**。
4.  在协议&监听页签下，配置监听。

    -   **选择负载均衡协议**：HTTPS
    -   **监听端口**：443
    -   **调度算法**：轮询（RR）
    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/5772129951/p10035.png)

5.  单击**下一步**，在SSL证书页签下，配置SSL证书信息，启用双向认证。
    -   **服务器证书**：选择已上传的服务器证书。
    -   **CA证书**： 选择已上传的CA证书。
6.  单击**下一步**，选择默认服务器组页签，单击**添加**，添加ECS服务器，并将后端协议端口设置为80。
7.  单击**下一步**，开启健康检查。
8.  单击**下一步**，查看监听配置信息。
9.  单击**提交**，提交审核。
10. 单击**确定**。

## 步骤七：测试HTTPS双向认证

1.  在实例管理页面，查看健康检查状态。当状态为**正常**时，表示后端服务器可以正常接收处理负载均衡监听转发的请求。
2.  在浏览器中，输入负载均衡的公网服务地址，当提示是否信任客户端证书时，选择信任。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p2786.png)

3.  刷新浏览器，您可以观察到请求在两台ECS服务器之间转换。

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p13780.png)

    ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/zh-CN/6614029951/p13781.png)


