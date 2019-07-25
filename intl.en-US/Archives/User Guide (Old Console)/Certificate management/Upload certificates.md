# Upload certificates {#task_ayx_qqn_vdb .task}

Before creating HTTPS listeners, you must upload the server certificate and CA certificate \(if required\) to SLB. You no longer need to configure certificates on the backend servers after uploading certificates to SLB.

-   You have purchased a server certificate.
-   You have generated a CA certificate and client certificate. For more information, see [Generate CA certificates](intl.en-US/User Guide/Certificate management/Generate CA certificates.md#).

Note the following before uploading certificates:

-   Certificates in SLB are regional resources. If you want to use a certificate in multiple regions, you must upload the certificate to all these regions.
-   Up to 100 certificates can be uploaded per account.

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=5176.2020520102.1002.d10slb.Nu53OX#/list/cn-hangzhou). 
2.  In the left-hand navigation pane, click **Certificates**. 
3.  Click **Upload Certificate**. 
4.  On the Upload Certificate page, upload the certificate content and then click **Confirm**. 

    |Configuration|Description|
    |:------------|:----------|
    |**Certificate Name**| Enter a certificate name.

 The name must be 1-80 characters in length, including letters, numbers and the following special characters:

 \_/. -

 |
    |**Certificate Region**| Select one or more regions where the certificate is uploaded.

 The region is where the HTTPS listener is located. Certificates cannot be used across regions.

 |
    |**Certificate Type**|Select a certificate type.    -   **Server Certificate**: For one-way authentication, only server certificate is required. The client uses it to check whether the certificate sent by the server is issued by a trusted center.
    -   **CA Certificate**: For two-way authentication, a CA certificate is required in addition to a server certificate. The server uses the CA certificate to authenticate the CA signature on the client certificate, as part of the authorization before launching a secure connection.
|
    |**Certificate Content**| Paste the certificate content in the editor.

 Click **Import Sample** to view the valid certificate formats. Only certificates in the PEM format are supported. For more information, see [Certificate requirements](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate in the editor.Click **Import Sample** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/User Guide/Certificate management/Certificate requirements.md#).

**Note:** A private key is required when uploading a server certificate.

|


