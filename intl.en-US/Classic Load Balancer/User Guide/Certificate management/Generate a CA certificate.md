Generate a CA certificate 
==============================================

When you configure an HTTPS listener, you can use a self-signed CA certificate. This topic describes how to generate a CA certificate and use the CA certificate to sign a client certificate.

Generate a CA certificate by using Open SSL 
----------------------------------------------------------------

1. Run the following commands to create a *ca* folder in the */root* directory and then create four subfolders under the *ca* folder. 

       sudo mkdir ca
       cd ca
       sudo mkdir newcerts private conf server

   

   * *newcerts* is used to store the digital certificate signed by the CA certificate.

     
   
   * *private* is used to store the private Key of the CA certificate.

     
   
   * *conf* is used to store the configuration files used for simplifying parameters.

     
   
   * *server* is used to store the server certificate.

     
   

   

2. Create an *openssl.conf* file that contains the following information in the *conf* directory. 

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

   

3. Run the following command to generate a private Key. 

       cd /root/ca
       sudo openssl genrsa -out private/ca.key

   

   The following figure is an example of the key generation.

   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9313359951/p2841.png)
   

4. Run the following command and input the required information according to the prompts. Press Enter to generate a *csr* file. 

       sudo openssl req -new -key private/ca.key -out private/ca.csr

   

   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9313359951/p2842.png)
   **Note**

   Common Name is the domain name of the SLB instance.
   

5. Run the following command to generate a *crt* file: 

       sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt

   

6. Run the following command to set the start sequence number for the private Key, which can be any four characters. 

       sudo echo FACE > serial

   

7. Run the following command to create a CA Key library: 

       sudo touch index.txt

   

8. Run the following command to create a certificate revocation list for removing the client certificate: 

       sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"

   

   The output is:
   

   

       Using configuration from /root/ca/conf/openssl.conf

   

   




Sign the client certificate 
------------------------------------------------

1. Run the following command to generate a *users* folder under the *ca* directory to store the client Key. 

       sudo mkdir users

   

2. Run the following command to create a Key for the client certificate: 

       sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024

   
   **Note**

   Enter a pass phrase when creating the Key. It is the password to protect the private Key from unauthorized access. Enter the same password twice.
   

3. Run the following command to create a *csr* file for the client Key. 

       sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr

   

   Enter the pass phrase set in the previous step and other required information when prompted.
   **Note**

   A challenge password is the password of the client certificate. Note that it is not the password of the client Key.
   

4. Run the following command to sign the client Key. 

       sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"

   

   Enter *y* twice when prompted to confirm the operation.

   ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9313359951/p2846.png)
   

5. Run the following command to convert the certificate to a *PKCS12* file. 

       sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12

   

   Follow the prompts to enter the pass phrase of client Key. Then enter the password used for exporting the client certificate. This password is used to protect the client certificate, which is required when you install the client certificate.
   

6. Run the following commands to view the generated client certificate: 

        cd users
        ls

   



