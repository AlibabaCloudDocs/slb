# Upload a third-party certificate

This topic describes how to upload a third-party certificate. You must obtain the public key or private key file of the certificate to upload a third-party certificate.

Before you upload a third-party certificate, make sure that the following conditions are met:

-   A server certificate is purchased.
-   A CA certificate and a client certificate are generated. For more information, see [Generate a CA certificate](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Generate a CA certificate.md).

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, click **Certificates**.

3.  On the page that appears, click **Create Certificate**.

4.  In the Create Certificate panel, select **Upload Third-party Certificate**.

    ![Create a certificate](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4556209951/p11880.png)

5.  After you select Upload Third-party Certificate, configure the certificate.

    |Parameter|Description|
    |:--------|:----------|
    |**Certificate Name**|Enter a name for the certificate.

The name must be 1 to 80 characters in length, and can contain only letters, digits, colons \(:\), underscores \(\_\), forward slashes \(/\), periods \(.\), and hyphens \(-\). |
    |**Resource Group**|Select the resource group to which the certificate belongs.|
    |**Region**|The region where the certificate is used.

Certificates cannot be used across regions. If you need to use a certificate in multiple regions, you must select all of the required regions. |
    |**Certificate Type**|Select the type of the certificate to be uploaded.     -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS mutual authentication, both the server certificate and the CA certificate are required. |
    |**Public Key Certificate**|Paste the contents of the server certificate or CA certificate into the field. The public key certificate contains the public key and signature information.

SLB instances use NGINX certificates obtained from a certificate provider. Most of the NGINX certificates are suffixed with .pem, and some certificates may be suffixed with .crt.

Click **Example** to view the valid certificate formats. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md). |
    |**Private Key**|Paste the private key of the server certificate into the field. Most of the NGINX certificates are obtained from a certificate provider and are suffixed with .key. Click **Example** to view the valid certificate formats. For more information, see [Certificate requirements](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Certificate requirements.md).

SLB supports the following private key formats:

    ```
-----BEGIN RSA PRIVATE KEY-----
Private key (Base64 encoded)
-----END RSA PRIVATE KEY-----
    ```

or

    ```
-----BEGIN EC PARAMETERS-----
Private key (Base64 encoded)
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
Private key (Base64 encoded)
-----END EC PRIVATE KEY-----
    ```

**Note:**

    -   A private key is required only when you upload a server certificate.
    -   Keys in the EC format are supported in the following regions:
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
        -   UAE \(Dubai\) |

6.  Click **Create**.


**References**  


[UploadCACertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/UploadCACertificate.md)

[UploadServerCertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/UploadServerCertificate.md)

