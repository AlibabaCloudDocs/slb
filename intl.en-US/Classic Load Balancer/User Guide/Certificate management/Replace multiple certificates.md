# Replace multiple certificates

This topic describes how to replace certificates for listeners and additional certificates.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, click **Certificates**.

3.  On the Certificates page, find the certificate that you want to replace, and then click **Replace** in the **Actions** column.

    **Note:** Only certificates associated with at least one listener or additional certificate can be replaced.

4.  On the Replace Server Certificate page, replace the certificate.

    The following table describes the parameters.

    |Parameter|Description|
    |---------|-----------|
    |Replace Mode: **Create and Replace Certificate**|
    |Select Certificate Source: **Alibaba Cloud Certificates**|Set **Region** and **Resource Group**, and then select a certificate from the drop-down list of **Certificates**.|
    |Select Certificate Source: **Upload Third-party Certificate**|Upload a third-party certificate. For more information, see [Upload a third-party certificate](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Create a certificate/Upload a third-party certificate.md).|
    |Replace Mode: **Replace with Saved Certificate**|
    |**Server Certificate for Replacement**|Select a server certificate from the list of existing certificates.|

5.  Click **Replace**.

6.  Click **View Certificate**. On the Certificates page, you can view that the certificate for the listeners and additional certificates are replaced with the new one.


