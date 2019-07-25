# Upload a certificate {#task_ayx_qqn_vdb .task}

Before creating HTTPS listeners, you must upload the required server certificate and CA certificate to SLB.  You no longer need to configure certificates on the backend servers after uploading the certificates to SLB.

-   You have purchased a server certificate.
-   You have generated a CA certificate and client certificate. For more information, see [Generate a CA certificate](reseller.en-US/User Guide (New Console)/Certificate management/Generate a CA certificate.md#).

Note the following before uploading certificates:

-   If you want to use a certificate in multiple regions, you must upload the certificate to all these regions.
-   Up to 100 certificates can be uploaded per account.

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb). 
2.  In the left-side navigation pane, click **Certificates**. 
3.  Click **Create Certificate**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15677/15382911777477_en-US.png)

4.  On the Create Certificate page, upload the certificate content and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Certificate Name**| Enter a certificate name.

 The name must be 1-80 characters long, and can only contain letters, numbers and the following special characters:

 \_/. -

 |
    |**Regions**| Select one or more regions where the certificate is uploaded.

 A certificate cannot be used across regions. If a certificate is to be used in multiple regions, select all these regions.

 |
    |**Certificate Type**|Select a certificate type.    -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS two-way authentication, both the server certificate and the CA certificate are required.
|
    |**Certificate Content**| Paste the certificate content in the editor.

 Click **Import Sample** to view the valid certificate formats. Only certificates in the PEM format are supported. For more information, see [Certificate requirements](reseller.en-US/User Guide (New Console)/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate in the editor.Click **Import Sample** to view the valid certificate formats. For more information, see [Certificate requirements](reseller.en-US/User Guide (New Console)/Certificate management/Certificate requirements.md#).

**Note:** A private key is only required when uploading a server certificate.

|

    Click **Remove All Expired Certificates** to delete expired certificates in batches.


