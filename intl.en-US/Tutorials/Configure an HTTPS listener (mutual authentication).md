# Configure an HTTPS listener \(mutual authentication\)

To add an HTTPS listener with mutual authentication enabled, you must upload a server certificate and a CA certificate when you configure the listener.

A self-signed CA certificate is used in this topic to sign the client certificate. Perform the following steps:

1.  [Prepare a server certificate](#section_klf_y5z_vdb).
2.  [Generate a CA certificate by using OpenSSL](#section_cqz_pvz_vdb).
3.  [Generate a client certificate](#section_jbr_hyz_vdb).
4.  [Upload the server and CA certificates](#section_mdg_411_wdb).
5.  [Install the client certificate](#section_cts_cd1_wdb).
6.  [Configure an HTTPS listener \(mutual authentication\)](#section_p5w_zd1_wdb).
7.  [Test the SLB service](#section_q3q_r21_wdb).

## Step 1: Prepare a server certificate

A server certificate is used by the client browser to check whether the certificate sent by the server is signed and issued by a trusted authority. You can purchase a server certificate from [Alibaba Cloud Security Certificate Service](https://www.aliyun.com/product/cas?spm=a2c4g.11186623.2.11.nw2Pcs), or from other service providers.

## Step 2: Generate a CA certificate by using Open SSL

1.  Run the following commands to create a ca folder in the /root directory and then create four subfolders in the ca folder:

    ```
    sudo mkdir ca
     cd ca
     sudo mkdir newcerts private conf server
    ```

    -   newcerts is the certificate backup directory that stores the digital certificates signed by the CA.
    -   private is used to store the private key of the CA certificate.
    -   conf is used to store the configuration files used for simplifying parameters.
    -   server is used to store the server certificate.
2.  Create an openssl.conf file that contains the following information in the conf directory:

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

3.  Run the following commands to generate a private key:

    ```
      cd /root/ca
       sudo openssl genrsa -out private/ca.key
    ```

    A similar output is displayed.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2750.png)

4.  Run the following command and specify the required information based on the prompts. Press Enter to generate the csr file, which is used to generate the certificate.

    ```
      sudo openssl req -new -key private/ca.key -out private/ca.csr
    ```

    **Note:** Common Name is the domain name of the SLB instance.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2753.png)

5.  Run the following command to generate the crt file:

    ```
      sudo openssl x509 -req -days 365 -in private/ca.csr -signkey private/ca.key -out private/ca.crt
    ```

6.  Run the following command to set the start sequence number for the CA key. The key can be any four characters:

    ```
      sudo echo FACE > serial
    ```

7.  Run the following command to create a CA key library:

    ```
      sudo touch index.txt
    ```

8.  Run the following command to create a certificate revocation list for removing the client certificate:

    ```
      sudo openssl ca -gencrl -out /root/ca/private/ca.crl -crldays 7 -config "/root/ca/conf/openssl.conf"
    ```

    Output:

    ```
    Using configuration from /root/ca/conf/openssl.conf
    ```


## Step 3: Generate a client certificate

1.  Run the following command to create the users directory in the ca directory to store client keys:

    ```
      sudo mkdir users
    ```

2.  Run the following command to create a client key:

    ```
      sudo openssl genrsa -des3 -out /root/ca/users/client.key 1024
    ```

    **Note:** When you create the key, enter a passphrase as the key password to prevent unauthorized use if the key leaks. Enter the same password twice.

3.  Run the following command to create a csr file for the client key:

    ```
      sudo openssl req -new -key /root/ca/users/client.key -out /root/ca/users/client.csr
    ```

    Enter the passphrase set in the previous step and required information based on the prompts.

    **Note:** `A challenge password` is the client certificate password. You must distinguish it from the password of `client.key`. In this topic, the password is test. It can be the same as that of the root certificate or server certificate.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2757.png)

4.  Run the following command to sign the client key by using the generated CA key.

    ```
      sudo openssl ca -in /root/ca/users/client.csr -cert /root/ca/private/ca.crt -keyfile /root/ca/private/ca.key -out /root/ca/users/client.crt -config "/root/ca/conf/openssl.conf"
    ```

    Enter y when you are prompted to confirm the following two operations.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2758.png)

5.  Run the following command to convert the certificate to a PKCS12 file that can be recognized by most browsers:

    ```
      sudo openssl pkcs12 -export -clcerts -in /root/ca/users/client.crt -inkey /root/ca/users/client.key -out /root/ca/users/client.p12
    ```

    Enter the passphrase of the client key and press Enter.

    Then, enter the password used to export the client certificate. This password is used to protect the client certificate and is required when the client certificate is installed.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2759.png)

6.  Run the following commands to view the generated client certificate:

    ```
    cd users
     ls
    ```

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p2760.png)


## Step 4: Upload the server and CA certificates

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).
2.  On the Instances page, click **Create Instance**.
3.  Configure the parameters, click **Buy Now**, and complete the payment.

    Set Instance Type to **Internet** and Region to **China \(Hangzhou\)**. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

4.  Go back to the Instances page and find the instance. Move the pointer over the instance name and click the icon next to the instance name to modify the instance name.
5.  In the left-side navigation pane, click Certificates.
6.  Click **Create Certificate**.
7.  On the Create Certificate page, configure the following parameters and click **OK**.
    -   **Region**: Select **China \(Hangzhou\)** for this example.

        **Note:** The region of the certificate must be the same as that of the SLB instance that uses the certificate.

    -   **Certificate Type**: Select **Server Certificate**.
    -   **Public Key Certificate and Private Key**: Copy the public key and private key.

        **Note:** Before you copy the keys, you can click **Example** to view the valid certificate format. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).

8.  In the left-side navigation pane, click **Certificates**. Then click **Create Certificate** to upload the CA certificate.
9.  On the Create Certificate page, configure the following parameters and click **OK**.
    -   **Region**: Select **China \(Hangzhou\)** for this example.

        **Note:** The region of the certificate must be the same as that of the SLB instance that uses the certificate.

    -   **Certificate Type**: Select **CA Certificate**.
    -   **Client CA Certificate**: copy the CA certificate.

        **Note:** Before you copy the certificate, you can click **Example** to view the valid certificate format. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).


## Step 5: Install the client certificate

Install the generated client certificates on the client. The Windows operating system and Internet Explorer browser are used for this example.

1.  Open Git Bash and run the following command to export the generated client certificate.

    ```
    scp root@IPaddress:/root/ca/users/client.p12 . /
    ```

    **Note:** IPaddress is the IP address of the server where the client certificate is generated.

2.  Import the certificate to the Internet Explorer browser.
    1.  Open Internet Explorer and choose **Settings icon** \> **Internet Options**.
    2.  Click the Content tab, and then click **Certificates** to import the downloaded client certificate. When you import the certificate, enter the password of the PKCS12 file.

## Step 6: Configure an HTTPS listener \(mutual authentication\)

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).
2.  On the Instances page, select the **China \(Hangzhou\)** region. Find the instance and click its ID or click **Configure Listener** in the Actions column.
3.  The Listener tab appears. Click **Add Listener**.
4.  In the Protocol and Listener step, configure the following parameters:

    -   **Select Listener Protocol**: HTTPS
    -   **Listening Port**: 443
    -   **Scheduling Algorithm**: Round Robin \(RR\)
    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10035.png)

5.  Click **Next**. In the SSL Certificates step, configure the certificates and turn on the Enable Mutual Authentication switch.
    -   **Select Server Certificate**: Select the uploaded server certificate.
    -   **Select CA Certificate**: Select the uploaded CA certificate.
6.  Click **Next**. In the Backend Servers step, click Default Server Group and then click **Add More**. Add ECS instances and set the port to 80.
7.  Click **Next** and turn on the Enable Health Check switch.
8.  Click **Next** and check the HTTPS listener configurations.
9.  Click **Submit** to submit the HTTPS listener configurations.
10. Click **OK**.

## Step 7: Test the SLB service

1.  On the Instances page, view the health check status. If **Normal** is displayed, the backend servers can receive requests forwarded by SLB listeners.
2.  Enter the public IP address of the SLB instance in the browser. Select Trust when you are prompted whether to trust the client certificate.
3.  Refresh the web page. You can find that the requests are evenly distributed to the backend servers.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p13780.png)

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6191019951/p13781.png)


