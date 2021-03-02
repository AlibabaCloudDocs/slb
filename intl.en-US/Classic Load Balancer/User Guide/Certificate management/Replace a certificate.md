# Replace a certificate

This topic describes how to replace a certificate with a new certificate. We recommend that you replace certificates before they expire to avoid service interruption.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  Click the ID of the Server Load Balancer \(SLB\) instance for which you want to replace the certificate and select the Listener tab.

3.  Find the HTTPS listener for which you want to replace the certificate and click **Manage Certificate** in the **Actions** column.

4.  On the Manage Certificate page, select Add Server Certificate.

    You can also select **Create Server Certificate** or **Purchase Certificate**. For more information about how to create a server certificate, see [Certificate overview](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Create a certificate/Certificate overview.md).

5.  On the Advanced Settings tab, click **Modify** and select whether to enable mutual authentication and TLS security policy. For more information, see [Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md).

6.  Click **OK**.

7.  On the Certificates page, find the expired certificate and click **Delete**.

8.  In the message that appears, click **OK**.

    **Note:** If the certificate is associated with another listener, it cannot be deleted.


**Related topics**  


[Add an HTTPS listener](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Add an HTTPS listener.md)

[Replace multiple certificates](/intl.en-US/Classic Load Balancer/User Guide/Certificate management/Replace multiple certificates.md)

