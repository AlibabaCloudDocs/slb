# Create a certificate {#concept_ekm_gj1_dfb .concept}

To configure an HTTPS listener, you can directly use a certificate from Alibaba Cloud SSL Certificate Service or upload a third-party server certificate and CA certificate to Server Load Balancer \(SLB\). After you upload the certificate to SLB, you do not need to configure certificates on backend servers.

SLB supports certificates from the following two sources:

-   Certificates issued or hosted by Alibaba Cloud SSL Certificate Service: You can select the required certificate from Alibaba Cloud SSL Certificate Service. When the certificate is about to expire, Alibaba Cloud will send alerts notifying you to renew the certificate to ensure its validity.

    Currently client CA certificates are not supported.

-   Third-party certificates: To upload a third-party certificate, you must have the public key and private key files of the certificate.

    HTTPS server certificates and client CA certificates are supported.


Before you create a certificate, note the following:

-   If you need to use a certificate in multiple regions, you must select all the required regions when creating the certificate.
-   Each Alibaba Cloud account can create up to 100 certificates.

## Select a certificate from SSL Certificate Service {#section_i3q_gm1_dfb .section}

Alibaba Cloud SSL Certificate Service issues digital certificates of a variety of authorities to provide HTTPS services. Additionally, Alibaba Cloud SSL Certificate Service can uniformly manage the life cycles of certificates to simplify certificate deployment. For more information, see [SSL certificate service](https://www.alibabacloud.com/product/certificates?spm=a2c5t.11065253.1996646101.searchclickresult.62967fdeLutlDg).

To use a certificate in SSL Certificate Service, you must log on to the [SSL Certificate console](https://yundun.console.aliyun.com/?spm=5176.2020520001.106.d20cas.3c474bd31n23aP&p=cas#/cas/home) to buy a certificate or upload a third-party certificate to SSL Certificate Service.

To use a certificate from SSL Certificate Service, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, click **Certificates**.
3.  Click **Create Certificate**. On the Create Certificate page, select **Select Certificate From SSL Certificate Service**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21331/156595043611881_en-US.png)

4.  Click **Next**. On the Select Certificate From SSL Certificate Service page, select the region to deploy the certificate and then select the SSL certificate to use from the certificate list.

    A certificate cannot be used across regions. If you need to use a certificate in multiple regions, you must select all the required regions.

5.  Click **OK**.

## Upload a third-party certificate {#section_q2y_kj1_dfb .section}

Before you upload a third-party certificate, make sure that the following conditions are met:

-   A server certificate is purchased.
-   A CA certificate and a client certificate are generated. For more information, see [Generate a CA certificate](intl.en-US/Certificate management/Generate a CA certificate.md#).

To upload a third-party certificate to SLB, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com).
2.  In the left-side navigation pane, click **Certificates**.
3.  Click **Create Certificate**.
4.  On the Create Certificate page, select **Upload Third-Party Certificate**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/21331/156595043611880_en-US.png)

5.  Click **Next**. On the Upload Third-Party Certificate page, upload the certificate content.

    |Configuration|Description|
    |:------------|:----------|
    |**Certificate Name**| Enter a name for the certificate to be uploaded.

 The name must be 1 to 80 characters in length, and can contain letters, numbers, and the following special characters:

 \_ / . -

 |
    |**Regions**| Select one or more regions to which the certificate to be uploaded belongs.

 A certificate cannot be used across regions. If you need to use a certificate in multiple regions, you must select all the required regions.

 |
    |**Certificate Type**|Select the type of the certificate to be uploaded:     -   **Server Certificate**: For HTTPS one-way authentication, only the server certificate and the private key are required.
    -   **CA Certificate**: For HTTPS mutual authentication, both the server certificate and the CA certificate are required.
 |
    |**Certificate Content**| Paste the certificate content into the text editor.

 Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/Certificate management/Certificate requirements.md#).

 |
    |**Private Key**|Paste the private key of the server certificate into the text editor. Click **View Sample Certificate** to view the valid certificate formats. For more information, see [Certificate requirements](intl.en-US/Certificate management/Certificate requirements.md#).

 SLB supports the following two private key formats:

    ``` {#codeblock_rs3_vc0_97t}
-----BEGIN RSA PRIVATE KEY-----
Private key content (BASE64 encoding)
-----END RSA PRIVATE KEY-----
    ```

 or

    ``` {#codeblock_umm_vxo_ibo}
-----BEGIN EC PARAMETERS-----
Private key content (BASE64 encoding)
-----END EC PARAMETERS-----
-----BEGIN EC PRIVATE KEY-----
Private key content (BASE64 encoding)
-----END EC PRIVATE KEY-----
    ```

 **Note:** 

    -   A private key is required only when you upload a server certificate.
    -   Currently, EC private keys are supported only in the UK \(London\) region.
 |

6.  Click **OK**.

