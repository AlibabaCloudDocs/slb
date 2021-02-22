# Configure access logging

This topic describes how to configure Server Load Balancer \(SLB\) access logging. If you use a RAM user, the user must be assigned the required RAM role before SLB can write logs to Log Service.

Before you configure access logging, make sure that the following prerequisites are met:

1.  A Layer 7 SLB instance is created.
2.  Log Service is activated.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Logs** \> **Access Logs**.

    **Note:** After the access log is configured, it cannot be closed temporarily.

3.  Select the region where the instance is deployed.

4.  Click **Authorize**. In the dialog box that appears, click **Confirm Authorization Policy** to authorize SLB to write logs to Log Service.

    If you log on to the console as a RAM user, you must first use your Alibaba Cloud account to authorize the RAM user. For more information, see [Authorize a RAM user to use access logs](/intl.en-US/User Guide/Log management/Access logs/Authorize a RAM user to use access logs.md).

    **Note:** If you have authorized SLB, skip this step.

5.  On the Access Logs page, find the instance for which you want to configure access logs and click **Configuring Logging** in the **Actions** column.

6.  In the **Configure Logging** panel, select a project and a Logstore.

    -   **Project**: the resource management unit in Log Service. It is used to isolate and control resources.
    -   **Logstore**: a unit in Log Service. It is used to collect, store, and query log data.
    **Note:** Make sure that the name of the project is globally unique and the region of the project is the same as that of the SLB instance.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8110561851/p65895.png)

    After you configure SLB access logging, you can query and search for logs by using the fields listed in the following table.

    |Field|Description|
    |:----|:----------|
    |body\_bytes\_sent|The size of the HTTP message body that is sent to the client. Unit: bytes.|
    |client\_ip|The IP address of the client that sends the request.|
    |host|The host header in the request.|
    |http\_user\_agent|The received http\_user\_agent header in the request.|
    |request\_length|The length of the request message, which includes the startline, HTTP headers, and HTTP body.|
    |request\_method|The request method.|
    |request\_time|The time interval between the first request received by SLB and the response sent by SLB.|
    |request\_uri|The received request URI.|
    |slbid|The ID of the SLB instance.|
    |status|The status code of the response from SLB.|
    |upstream\_addr|The IP address and port number of the backend server.|
    |upstream\_response\_time|The time between establishing a connection and receiving the last byte of the response body from the backend server.|
    |upstream\_status|The status code of the response obtained by SLB from the backend server.|

7.  Click **OK**.


