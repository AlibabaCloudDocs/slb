# 生成CA证书 {#concept_f44_jqn_vdb .concept}

在配置HTTPS监听时，您可以使用自签名的CA证书，并且使用该CA证书为客户端证书签名。

## 使用Open SSL生成CA证书 {#section_bsx_2pb_wdb .section}

1.  执行如下命令，在/root目录下新建一个ca文件夹，并在ca文件夹下创建四个子文件夹。

    ``` {#codeblock_529_4tp_efb}
     $ sudo mkdir ca
     $ cd ca
     $ sudo mkdir newcerts private conf server
    ```

    -   newcerts目录将用于存放CA签署过的数字证书。
    -   private目录用于存放CA的私钥。
    -   conf目录用于存放一些简化参数用的配置文件。
    -   server目录存放服务器证书文件。
2.  在conf目录下新建一个包含如下信息的openssl.conf文件。

    ``` {#codeblock_izz_ue5_8et}
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

3.  执行如下命令，生成私钥key文件。

    ``` {#codeblock_9tm_7t2_3o0}
    $ cd /root/ca
     $ sudo openssl genrsa -out private/ca.key
    ```

    执行结果如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15610871532841_zh-CN.png)

4.  执行如下命令，按照提示输入所需信息，然后按下回车键生成证书请求csr文件。

    ``` {#codeblock_vcb_di2_als}
    $ sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **说明：** Common Name需要输入负载均衡的域名。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15610871542842_zh-CN.png)

5.  运行以下命令生成凭证crt文件。

    ``` {#codeblock_u4d_sd4_q88}
    $ sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  运行以下命令为CA的key设置起始序列号，可以是任意四个字符。

    ``` {#codeblock_ni4_bxg_akk}
    $ sudo echo FACE > serial
    ```

7.  运行以下命令创建CA键库。

    ``` {#codeblock_ufp_9v4_y1j}
    $ sudo touch index.txt
    ```

8.  运行以下命令为移除客户端证书创建一个证书撤销列表。

    ``` {#codeblock_evh_cf9_0de}
    $ sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    输出为：

    ``` {#codeblock_jir_vxc_jqk}
    Using configuration from /root/ca/conf/openssl.conf
    ```


## 为客户端证书签名 {#section_rxk_5rb_wdb .section}

1.  运行以下命令在ca目录内创建一个存放客户端key的目录users。

    ``` {#codeblock_tgh_cg3_qp3}
    $ sudo mkdir users
    ```

2.  运行以下命令为客户端创建一个key。

    ``` {#codeblock_woe_rmg_yl0}
    $ sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **说明：** 创建key时要求输入pass phrase，这个是当前key的口令，以防止本密钥泄漏后被人盗用。两次输入同一个密码。

3.  运行以下命令为客户端key创建一个证书签名请求csr文件。

    ``` {#codeblock_6e1_1e4_ygn}
    $ sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    输入该命令后，根据提示输入上一步输入的pass phrase，然后根据提示输入对应的信息。

    **说明：** A challenge password是客户端证书口令。注意将它和client.key的口令进行区分。

4.  运行以下命令使用CA证书的key为客户端key签名。

    ``` {#codeblock_sgy_u6v_bh8}
    $ sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    当出现确认是否签名的提示时，两次都输入y。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15610871542846_zh-CN.png)

5.  运行以下命令将证书转换为PKCS12文件。

    ``` {#codeblock_psw_iyn_pko}
    $ sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    按照提示输入客户端client.key的pass phrase。再输入用于导出证书的密码。这个是客户端证书的保护密码，在安装客户端证书时需要输入这个密码。

6.  运行以下命令查看生成的客户端证书。

    ``` {#codeblock_oji_1bb_z7h}
     cd users
     ls
    ```


