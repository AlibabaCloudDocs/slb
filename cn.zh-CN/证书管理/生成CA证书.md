# 生成CA证书 {#task_1597671 .task}

在配置HTTPS监听时，您可以使用自签名的CA证书，并且使用该CA证书为客户端证书签名。

## 使用Open SSL生成CA证书 {#section_1ei_mfm_gya .section}

1.  执行如下命令，在/root目录下新建一个ca文件夹，并在ca文件夹下创建四个子文件夹。 

    ``` {#codeblock_m2u_yeh_dv7}
     $ sudo mkdir ca
     $ cd ca
     $ sudo mkdir newcerts private conf server
    ```

    -   newcerts目录将用于存放CA签署过的数字证书。
    -   private目录用于存放CA的私钥。
    -   conf目录用于存放一些简化参数用的配置文件。
    -   server目录存放服务器证书文件。
2.  在conf目录下新建一个包含如下信息的openssl.conf文件。 

    ``` {#codeblock_yk1_s9b_44x}
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

    ``` {#codeblock_9fb_dej_41d}
    $ cd /root/ca
     $ sudo openssl genrsa -out private/ca.key
    ```

    执行结果如下图所示。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15676492022841_zh-CN.png)

4.  执行如下命令，按照提示输入所需信息，然后按下回车键生成证书请求csr文件。 

    ``` {#codeblock_x5u_v5k_k39}
    $ sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **说明：** Common Name需要输入负载均衡的域名。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15676492032842_zh-CN.png)

5.  执行如下命令，生成凭证crt文件。 

    ``` {#codeblock_ykl_0e3_ep7}
    $ sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  执行如下命令，为CA的key设置起始序列号，可以是任意四个字符。 

    ``` {#codeblock_p70_de8_92d}
    $ sudo echo FACE > serial
    ```

7.  执行如下命令，创建CA键库。 

    ``` {#codeblock_7x2_dc9_djj}
    $ sudo touch index.txt
    ```

8.  执行如下命令，为移除客户端证书创建一个证书撤销列表。 

    ``` {#codeblock_f83_l5a_4xm}
    $ sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    输出为：

    ``` {#codeblock_gis_3of_xtn}
    Using configuration from /root/ca/conf/openssl.conf
    ```


## 为客户端证书签名 {#section_i07_uea_1to .section}

1.  执行如下命令，在ca目录内创建一个存放客户端key的目录users。 

    ``` {#codeblock_j7h_z1s_pil}
    $ sudo mkdir users
    ```

2.  执行如下命令，为客户端创建一个key。 

    ``` {#codeblock_3ku_ocq_a7c}
    $ sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **说明：** 创建key时要求输入pass phrase，这个是当前key的口令，以防止本密钥泄漏后被人盗用。两次输入同一个密码。

3.  执行如下命令，为客户端key创建一个证书签名请求csr文件。 

    ``` {#codeblock_wuj_ob9_pl4}
    $ sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    输入该命令后，根据提示输入上一步输入的pass phrase，然后根据提示输入对应的信息。

    **说明：** A challenge password是客户端证书口令。注意将它和client.key的口令进行区分。

4.  执行如下命令，使用CA证书的key为客户端key签名。 

    ``` {#codeblock_pdb_e26_ysp}
    $ sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    当出现确认是否签名的提示时，两次都输入y。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15676492032846_zh-CN.png)

5.  执行如下命令，将证书转换为PKCS12文件。 

    ``` {#codeblock_7yy_7vz_rvy}
    $ sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    按照提示输入客户端client.key的pass phrase。再输入用于导出证书的密码。这个是客户端证书的保护密码，在安装客户端证书时需要输入这个密码。

6.  执行如下命令，查看生成的客户端证书。 

    ``` {#codeblock_3hf_vgo_7si}
     cd users
     ls
    ```


