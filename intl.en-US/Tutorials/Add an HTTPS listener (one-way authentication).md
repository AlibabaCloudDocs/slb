# Add an HTTPS listener \(one-way authentication\)

To add an HTTPS listener with one-way authentication, you need only to upload a server certificate to SLB when you configure the listener.

## Step 1: Upload a server certificate

Before you configure the HTTPS listener, you must buy a server certificate and upload the server certificate to the certificate management system of SLB. After that, you no longer need to make other certificate configurations on the backend server.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, click Certificates. Then, click **Create Certificate**.

3.  Click **Upload Third-party Certificate**.

4.  Configure the following parameters:

    -   Certificate Name: The name must be 1 to 80 characters in length and can contain letters, digits, hyphen \(-\), forward slashes \(/\), periods \(.\), underscores \(\_\), and asterisks \(\*\).
    -   Region: Select **China \(Hangzhou\)**.

        **Note:** The region of the certificate must be the same as that of the SLB instance that uses the certificate.

    -   Certificate Type: Select **Server Certificate**.
    -   Public Key Certificate and Private Key: Copy the public key and private key. Before you copy the keys, you can click **Example** to view the valid certificate format. The certificate to be uploaded must be in the PEM format. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).
5.  Click **OK**.


## Step 2: Create an SLB instance

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  On the Instances page, click **Create Instance**.

3.  Configure the parameters, click **Buy Now**, and complete the payment.

    Set Instance Type to **Internet** and Region to **China \(Hangzhou\)**. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

4.  Go back to the Instances page and select the **China \(Hangzhou\)** region.

5.  Find the instance and click its ID or click **Configure Listener** in the Actions column.

6.  The Listener tab appears. Click **Add Listener**.

7.  In the Protocol and Listener step, configure the following parameters:

    -   **Select Listener Protocol**: HTTPS
    -   **Listening Port**: 443
    -   **Scheduling Algorithm**: Round Robin \(RR\)
8.  Click **Next**. In the SSL Certificates step, select the uploaded server certificate and TSL security policy.

9.  Click **Next**. In the Backend Servers step, click Default Server Group and then click **Add More**. Add ECS instances and set the port to 80.

10. Use the default values for other parameters and click **Next** to go to the **Confirm** step. Click Submit to complete SLB instance configurations.


## Step 3: Test the SLB service

1.  Go back to the Instances page and view the health check status.

    If **Normal** is displayed, the backend servers can receive requests forwarded by SLB listeners.

2.  Enter the public IP of the SLB instance in the browser.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4013359951/p7447.png)

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4013359951/p7448.png)


