# Upload a third-party certificate {#task_1597568 .task}

Before you upload a third-party certificate, you must obtain the public and private key file of the certificate.

Before you upload a third-party certificate, make sure that the following conditions are met:

-   A server certificate is purchased.
-   A CA certificate and a client certificate are generated. For more information, see [EN-US\_TP\_15675.md\#](reseller.en-US/Certificate management/Generate a CA certificate.md#).

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  In the left-side navigation pane, choose **Certificates**.
3.  Click **Create Certificate**.
4.  On the Create Certificate page, select **Upload Third-Party Certificate**. 

    ![Create a certificate](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21331/156595052111880_en-US.png)

5.  Click **Next**. On the Upload Third-Party Certificate page, upload the certificate. 

    |Configuration|Description|
    |:------------|:----------|
    |**Certificate Name**| Enter a name for the certificate to be uploaded.

 The name must be 1 to 80 characters in length, and can only contain letters, numbers, and the following special characters:

 \_ / . -

 |
    |**Regions**| Select one or more regions to which the certificate to be uploaded belongs.

 A certificate cannot be used across regions. If you need to use a certificate in multiple regions, select all the required regions.

 |
    |**Certificate Type**|Select the type of the certificate to be uploaded:     -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS mutual authentication, both the server certificate and the CA certificate are required.
 |
    |**Certificate Content**| Paste the certificate content into the text editor.

 Click **View Sample Certificate** to view the valid certificate formats. For more information, see [EN-US\_TP\_15674.md\#](reseller.en-US/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate into the text editor. Click **View Sample Certificate** to view the valid certificate formats. For more information, see [EN-US\_TP\_15674.md\#](reseller.en-US/Certificate management/Certificate requirements.md#).

 SLB supports the following two private key formats:

    ``` {#codeblock_fs0_8mu_cen}
-----BEGIN RSA PRIVATE KEY-----
Private key content (BASE64 encoding)
-----END RSA PRIVATE KEY-----
    ```

 or

    ``` {#codeblock_gul_q0r_0iq}
-----BEGIN EC PARAMETERS-----
Private key content (BASE64 encoding)
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
Private key content (BASE64 encoding)
-----END EC PRIVATE KEY-----
    ```

 **Note:** 

    -   A private key is required only when you upload a server certificate.
    -   Currently, keys in the EC format are supported in the following regions:
        -   UK \(London\)
        -   China \(Qingdao\)
        -   China \(Hohhot\)
        -   China \(Chengdu\)
        -   Japan \(Tokyo\)
        -   India \(Mumbai\)
        -   Australia \(Sydney\)
        -   Malaysia \(Kuala Lumpur\)
        -   US \(Silicon Valley\)
        -   US \(Virginia\)
        -   Germany \(Frankfurt\)
        -   UAE \(Dubai\)
 |

6.  Click **OK**.

[UploadCACertificate](../reseller.en-US/Developer Guide/Server certificates/UploadCACertificate.md#)

[UploadServerCertificate](../reseller.en-US/Developer Guide/Server certificates/UploadServerCertificate.md#)

