# Add an HTTPS listener \(one-way authentication\) {#concept_apn_dj5_vdb .concept}

To add an HTTPS listener with one-way authentication, you only need to upload a server certificate to SLB when configuring the listener.

## Step 1 Upload the server certificate {#section_tqs_yw5_vdb .section}

Before configuring the HTTPS listener \(one-way authentication\), you must buy a server certificate and upload the server certificate to the certificate management system of SLB. You no longer need to maintain the certificate on the backend server after uploading it to SLB.

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  In the left-side navigation pane, click Certificates, and then click **Create Certificate**.
3.  Configure the server certificate as follows:
    -   Regions: Select China \(Hangzhou\).

        **Note:** The region of the certificate must be the same as that of the SLB instance to use the certificate.

    -   Certificate Type: Select **Server Certificate**.
    -   Certificate Content and Private Key: Copy the content and private key of the server certificate. Click **Import Sample** to view the valid certificate format. The certificate to be uploaded must be in the PEM format. For more information, see [Certificate formats](reseller.en-US/Archives/User Guide (Old Console)/Certificate management/Certificate requirements.md#).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15562489407324_en-US.png)

4.  Click **OK**.

## Step 2 Configure the SLB instance {#section_rc5_sx5_vdb .section}

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Server Load Balancer page, click **Create SLB Instance**.
3.  Configure the instance and then click **Buy Now**.

    **Note:** In this tutorial, the instance type is **Internet** and the region is **China \(Hangzhou\)**. For more information, see [Create an SLB instance](reseller.en-US/Archives/User Guide (Old Console)/SLB instances/Create an instance.md#).

4.  Go back to the Server Load Balancer page and select the **China \(Hangzhou\)** region.
5.  Click the ID of the created SLB instance or click **Configure Listener**.
6.  Click the Listeners tab and then click **Add Listener**.
7.  In the Protocol and Listener tab, configure the listener.

    -   **Select Listener Protocol**: HTTPS
    -   **Listening Port**: 443
    -   **Scheduling Algorithm**: Round Robin \(RR\)
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15562489407325_en-US.png)

8.  Click **Next**. Under the SSL Certificates tab, select the uploaded server certificate.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15562489427326_en-US.png)

9.  Click **Next**. On the displayed page, click Default Server Group and then click **Add**. Add ECS instances and set the backend port to 80.
10. In the left-side navigation pane, click **Servers** \> **Backend Servers**, and then click **Add Backend Servers** to add ECS instances.

## Step 3 Test the SLB service {#section_jcf_4y5_vdb .section}

1.  Go back to the Server Load Balancer page to view the health check status.

    When the status is **Normal**, the backend servers can receive requests forwarded by SLB listeners.

2.  Enter the public IP of the Server Load Balancer instance in the web browser.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15562489427447_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15658/15562489437448_en-US.png)


