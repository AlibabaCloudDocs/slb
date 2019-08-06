# Upload a certificate {#task_ayx_qqn_vdb .task}

Before you create an HTTPS listener, you must upload the required server certificate and CA certificate to SLB. You no longer need to configure certificates on backend servers after uploading the certificates to SLB.

-   A server certificate is purchased.
-   A CA certificate and a client certificate are generated. For more information, see [Generate a CA certificate](intl.en-US/Certificate management/Generate a CA certificate.md#).

Before you upload a certificate, note the following:

-   If you want to use a certificate in multiple regions, you must select all the required regions.
-   Up to 100 certificates can be uploaded under one account.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb). 
2.  In the left-side navigation pane, choose **Certificates**. 
3.  Click **Create Certificate**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15677/15645484617477_en-US.png)

4.  On the Create Certificate page, upload the certificate and then click **OK**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Certificate Name**| Enter a name for the certificate to be uploaded.

 The name must be 1 to 80 characters in length, and can only contain letters, numbers, and the following special characters:

 \_ / . -

 |
    |**Regions**| Select one or more regions to which the certificate to be uploaded belongs.

 A certificate cannot be used across regions. If you need to use a certificate in multiple regions, select all the required regions.

 |
    |**Certificate Type**|Select the type of the certificate to be uploaded:    -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS mutual authentication, both the server certificate and the CA certificate are required.
|
    |**Certificate Content**| Paste the certificate content in the editor.

 Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate in the editor.Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/Certificate management/Certificate requirements.md#).

**Note:** A private key is required only when you upload a server certificate.

|

    To delete expired certificates in batches, click **Remove All Expired Certificates**.


