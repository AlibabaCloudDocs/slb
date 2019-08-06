# Generate a CA certificate {#concept_f44_jqn_vdb .concept}

When configuring HTTPS listeners, you can use self-signed CA certificates. Follow the instructions in this document to generate a CA certificate and use the CA certificate to sign a client certificate.

## Generate a CA certificate by using Open SSL {#section_bsx_2pb_wdb .section}

1.  Run the following commands to create a ca folder in the /root directory and then create four sub folders under the ca folder.

    ```
     $ sudo mkdir ca
     $ cd ca
     $ sudo mkdir newcerts private conf server
    ```

    -   newcerts is used to store the digit certificate signed by a CA certificate.
    -   private is used to store the private key of the CA certificate.
    -   conf is used to store the configuration files.
    -   server is used to store the server certificate.
2.  Create an openssl.conf file that contains the following information in the conf directory.

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
     commonName = supplied
     emailAddress = optional
    ```

3.  Run the following command to generate a private key.

    ```
    $ cd /root/ca
     $ sudo openssl genrsa -out private/ca.key
    ```

    The following figure is an example of key generation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15645484492841_en-US.png)

4.  Run the following command and input the required information according to the prompts. Press Enter to generate a csr file.

    ```
    $ sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **Note:** Common Name is the domain name of the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15645484492842_en-US.png)

5.  Run the following command to generate a crt file.

    ```
    $ sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  Run the following command to set the start sequence number for the private key, which can be any four characters.

    ```
    $ sudo echo FACE > serial
    ```

7.  Run the following command to create a CA key library.

    ```
    $ sudo touch index.txt
    ```

8.  Run the following command to create a certificate revocation list for removing the client certificate.

    ```
    $ sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    The response is as follows:

    ```
    Using configuration from /root/ca/conf/openssl.conf
    ```


## Sign the client certificate {#section_rxk_5rb_wdb .section}

1.  Run the following command to generate a users folder under the ca directory to store the client key.

    ```
    $ sudo mkdir users
    ```

2.  Run the following command to create a key for the client certificate.

    ```
    $ sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **Note:** Enter a pass phrase when creating the key. It is the password to protect the private key from unauthorized access. The pass phrase entered is the password for this key.

3.  Run the following command to create a csr file for requesting certificate sign.

    ```
    $ sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    Enter the pass phrase set in the previous step when prompted.

    **Note:** A challenge password is the password of the client certificate. Note that it is not the password of the client key.

4.  Run the following command to sign the client key.

    ```
    $ sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    Enter y twice when prompted.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4143/15645484492846_en-US.png)

5.  Run the following command to convert the certificate to a PKCS12 file.

    ```
    $ sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    Enter the password of the client key when prompted. Then, enter the password used for exporting the client certificate. This password is used to protect the client certificate, which is required when installing the client certificate.

6.  Run the following command to view the generated client certificate.

    ```
     cd users
     ls
    ```


