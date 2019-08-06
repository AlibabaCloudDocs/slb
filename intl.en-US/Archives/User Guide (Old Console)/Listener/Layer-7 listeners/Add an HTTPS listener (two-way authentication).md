# Add an HTTPS listener \(two-way authentication\) {#concept_mkk_3j5_vdb .concept}

To add an HTTPS listener with two-way authentication, you have to upload a server certificate and a CA certificate to SLB when configuring the listener.

A self-signed CA certificate is used to sign the client certificate in this tutorial. Complete these steps to add an HTTPS listener with two-way authentication:

1.  [Prepare a server certificate](#section_klf_y5z_vdb)
2.  [Generate a CA certificate using Open SSL](#section_cqz_pvz_vdb)
3.  [Generate a client certificate](#section_jbr_hyz_vdb)
4.  [Upload the server certificate and the CA certificate](#section_mdg_411_wdb)
5.  [Install the client certificate](#section_cts_cd1_wdb)
6.  [Configue the Server Load Balancer instance](#section_p5w_zd1_wdb)
7.  [Test the load balancing service](#section_q3q_r21_wdb)

## Step 1 Prepare the server certificate {#section_klf_y5z_vdb .section}

A server certificate is used by the client browser to check whether the certificate sent by the server is signed and issued by a trusted center. You can purchase a server certificate from [Alibaba Cloud Security](https://www.aliyun.com/product/cas?spm=a2c4g.11186623.2.11.nw2Pcs) Certificate Service, or from other service providers.

## Step 2 Generate a CA certificate by using Open SSL {#section_cqz_pvz_vdb .section}

1.  Run the following commands to create a ca folder under the /root directory and then create four sub folders under the ca folder.

    ```
    $ sudo mkdir ca
     $ cd ca
     $ sudo mkdir newcerts private conf server
    ```

    where:

    -   newcerts is used to store the digit certificate signed by a CA certificate.
    -   private is used to store the private key of the CA certificate.
    -   conf is used to store the configuration files.
    -   server is used to store the server certificate.
2.  Create an openssl.conf file with the following content under the conf folder.

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

3.  Run the following command to generate a private key file.

    ```
    $ cd /root/ca
     $ sudo openssl genrsa -out private/ca.key
    ```

    The following figure is an example of the key generation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2750_en-US.png)

4.  Run the following command and input the required information according to the prompts. Press Enter to generate the csr file used to generate the certificate.

    ```
    $ sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **Note:** Common Name is the domain name of the SLB instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2753_en-US.png)

5.  Run the following command to generate the crt file.

    ```
    $ sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  Run the following command to set the start sequence number for the private key, which can be any four characters.

    ```
    $ sudo echo FACE > serial
    ```

7.  Run the following command to create the CA key library.

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


## Step 3 Generate a client certificate {#section_jbr_hyz_vdb .section}

1.  Run the following command to generate a users folder under the ca folder to store the client certificate.

    ```
    $ sudo mkdir users
    ```

2.  Run the following command to create a key for the client key.

    ```
    $ sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **Note:** The pass phrase entered is the phrase for this key. Enter the same password twice.

3.  Run the following command to create a csr file for requesting certificate sign.

    ```
    $ sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    As prompted, input the pass phrase set in the previous step.

    **Note:** A challenge password is the client password \(Separate it from the password of `client.key`\). It can be same as that of the root certificate or server certificate.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2757_en-US.png)

4.  Run the following command to sign the client key.

    ```
    $ sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    Enter y when prompted to confirm the operation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2758_en-US.png)

5.  Run the following command to convert the certificate to the PKCS12 file that can be recognized by most browsers.

    ```
    $ sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    Follow the prompts to enter a pass for client. Key

    Enter the password of the client key when prompted. Enter the password used for exporting the client certificate.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2759_en-US.png)

6.  Run the following command to view the created certificate.

    ```
    cd users
     ls
    ```

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2760_en-US.png)


## Step 4 Upload the server certificate and the CA certificate {#section_mdg_411_wdb .section}

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.12.nw2Pcs#/list/cn-hangzhou).
2.  On the Instances page, click **Create Server Load Balance**.
3.  Configure the instance and then click **Buy Now**.

    In this tutorial, the network type is **Internet** and region is **China \(Hangzhou\)**. For more information on other instance configurations, see [Create an SLB instance](intl.en-US/User Guide/SLB instances/Create an SLB instance.md#).

4.  On the Instances page, hover the mouse to the ID of the SLB instance, and then click the pencil icon to change the instance name.
5.  On Server Load Balancer page, click **Certificates**, and then click **Upload Certificate**.
6.  On the Upload Certificate page, complete the following configurations and click **Confirm**.
    -   **Certificate Region**: **China \(Hangzhou\)** is selected in this tutorial.

        **Note:** The region of the certificate must be the same as that of the Server Load Balancer instance.

    -   **Certificate Type**: **Server Certificate** is selected in this tutorial.
    -   **Certificate Content and Private Key**: Copy the content and private key of the server certificate.

        **Note:** Click **Import Sample** to view the valid format of the certificate. For more information, see [Certificate formats](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2766_en-US.png)

7.  In the left-side navigation pane, click **Certificates**, and then click **Upload Certificate**.
8.  On the Upload Certificate page, complete the following configurations and click **Confirm**.
    -   **Certificate Region**: **China \(Hangzhou\)** is selected in this tutorial.

        **Note:** The region of the certificate must be the same as that of the Server Load Balancer instance.

    -   **Certificate Type**: **CA Certificate** is selected in this tutorial.
    -   **Certificate Content**: Copy the content of the CA certificate.

        **Note:** Click **Import Sample** to view the valid format of the certificate. For more information, see [Certificate formats](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2772_en-US.png)


## Step 5 Install client certificates {#section_cts_cd1_wdb .section}

Install the generated client certificates. The Windows operating system and IE web browser are used as examples in this tutorial.

1.  Open the Git Bash command line, run the following command to export the client certificate.

    ```
    scp root@IPaddress:/root/ca/users/client.p12 . /
    ```

    **Note:** IPaddress is the IP of the server where the client certificate is generated.

2.  Import the certificate to the IE web browser:
    1.  Open the IE web browser, click **Settings** \> **Internet Options**.
    2.  Click the **Content** tab, and then click **Certificates**. Import the PKCS12 file generated in step 3.

        ![](images/2781_en-US.png)


## Configure the SLB instance {#section_p5w_zd1_wdb .section}

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.16.nw2Pcs#/list/cn-hangzhou).
2.  On the Instancespage, select the **China \(Hangzhou\)** region, and then click the ID of the created instance.
3.  In the left-side navigation pane of the Details page, click **Listeners**, and then click **Add Listener**.
4.  In the Add Listener dialog, configure the listener.

    The listener configuration used in this tutorial is as follows: For more information, see [Layer-7 listener configurations](intl.en-US/User Guide/Listener/Layer-7 listeners/Layer-7 listener configurations.md#).

    -   **Front-end Protocol \[Port\]**: HTTPS 443
    -   **Backend Protocol \[Port\]**: HTTP 80
    -   **Scheduling Algorithm**: Round Robin
    -   **Mutual Authentication**: Enable
    -   **Server Certificate**: Select the uploaded server certificate.
    -   **CA Certificate**: Select the uploaded client certificate.
    -   Click **Next**, and then click **Confirm** to create the listener.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2785_en-US.png)

5.  In the left-side navigation pane, click **Servers** \> **Backend Servers**, and then click **Add** of the target ECS instance to add backend servers.

## Step 7 Test the load balancing service {#section_q3q_r21_wdb .section}

1.  Go back to the Instancespage and check the health status of the backend servers. When the status is **Normal**, the listener is working normally.
2.  Enter the public IP of the Server Load Balancer instance in the web browser, check if the requests are handled correctly over the SSL protocol.

    ![](images/2786_en-US.png)

3.  Refresh web page, you can find the requests are evenly distributed to the backend servers.

    **Note:** Because a self-signed certificate is used, the certificate is not trusted in the following image.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2787_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4133/2788_en-US.png)


