# Add an HTTPS listener \(one-way authentication\) {#concept_apn_dj5_vdb .concept}

To add an HTTPS listener with one-way authentication, you only need to upload a server certificate to SLB when configuring the listener.

## Step 1 Upload the server certificate {#section_tqs_yw5_vdb .section}

Before configuring the HTTPS listener \(one-way authentication\), you have to upload the server certificate to SLB. You no longer need to maintain the certificate on the backend server after uploading it to SLB.

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=5176.2020520101.1002.d10slb.2kxze4#/list/cn-hangzhou).
2.  In the left-side navigation pane, click **Certificates**, and then click **Upload Certificate**.
3.  Configure the server certificate as follows:
    -   Certificate Region: select **China \(Hangzhou\)**.

        **Note:** The region of the certificate must be the same as that of the SLB instance to use the certificate.

    -   Certificate Type: Select **Server Certificate**.
    -   Certificate Content and Private Key: Copy the content and private key of the server certificate. Click **Import Sample** to view the valid format of the certificate. The certificate to be uploaded must be in the PEM format. For more information, see [Certificate formats](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4132/2640_en-US.png)

4.  Click **Confirm**.

## Step 2 Configure the SLB instance {#section_rc5_sx5_vdb .section}

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=5176.2020520101.1002.d10slb.2kxze4#/list/cn-hangzhou).
2.  On the Instances page, click **Create Server Load Balance**.
3.  Configure the instance and then click **Buy Now**.

    **Note:** In this tutorial, the network type is **Internet** and region is **China \(Hangzhou\)**. For more information, see [Create an SLB instance](intl.en-US/User Guide/SLB instances/Create an SLB instance.md#).

4.  On the Instances page, select the **China \(Hangzhou\)** region, and then click the ID of the created instance.
5.  In the left-side navigation pane of the Details page, click **Listeners**, and then click **Add Listener**
6.  In the Add Listener dialog, configure the listener. The listener configuration used in this tutorial is as follows:
    -   **Front-end Protocol \[Port\]**: HTTPS 443
    -   **Backend Protocol \[Port\]**: HTTP 80
    -   **Scheduling Algorithm**: Round Robin
    -   **Server Certificate**: Select the uploaded server certificate.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4132/2645_en-US.png)

7.  In the left-side navigation pane, click **Servers** \> **Backend Servers**, and then click **Add** of the target ECS instance to add backend servers.

## Step 3 Test the load balancing service {#section_jcf_4y5_vdb .section}

1.  Go back to the Instances page and check the health status of the backend servers. When the status is **Normal**, the listener is working normally.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4132/2649_en-US.png)

2.  Enter the public IP of the Server Load Balancer instance in the web browser, check if the requests are handled correctly over the SSL protocol.

    **Note:** Because a self-signed certificate is used, the certificate is not trusted in the following image.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4132/2660_en-US.png)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4132/2661_en-US.png)


