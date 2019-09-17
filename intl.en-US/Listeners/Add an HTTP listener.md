# Add an HTTP listener {#task_1563673 .task}

This topic describes how to add an HTTP listener to a Server Load Balancer \(SLB\) instance. You can add an HTTP listener to forward requests from the HTTP protocol.

An SLB instance is created. For more information, see [Create an SLB instance](../reseller.en-US/Instance/Create an SLB instance.md#).

## Step 1 Open the listener configuration wizard {#section_zd7_xi8_xj0 .section}

To open the listener configuration wizard, follow these steps:

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select the region of the target SLB instance.
4.  Select one of the following methods to open the listener configuration wizard: 
    -   On the Server Load Balancer page, find the target SLB instance and then click **Configure Listener** in the **Actions** column.

        ![Listener configuration wizard](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/156870736510004_en-US.png)

    -   On the Server Load Balancer page, click the ID of the target SLB instance. On the Listeners tab, click **Add Listener**.

        ![Add listener](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16161/15687073657399_en-US.png)


## Step 2 Configure the HTTP listener {#section_k58_mb2_whz .section}

To configure the HTTP listener, follow these steps:

1.  On the Protocol and Listener page, configure the HTTP listener according to the following information: 

    |Configuration|Description|
    |:------------|:----------|
    |**Select Listener Protocol**|Select the protocol type of the listener. In this topic, select **HTTP**.

 |
    |**Listening Port**|The listening port used to receive requests and forward the requests to backend servers. Value range: 1 to 65535.

 **Note:** The listening port must be unique in an SLB instance.

 |
    |**Advanced configurations**|
    |**Scheduling Algorithm**|SLB supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).     -   **Weighted Round-Robin \(WRR\)**: A backend server with a higher weight receives more requests.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight receives more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
 |
    |**Redirection**|Select whether to forward traffic of the HTTP listener to an HTTPS listener. **Note:** Before you enable the redirection function, make sure that you have created an HTTPS listener.

 |
    |**Session Persistence**| Select whether to enable session persistence.

 After you enable session persistence, all session requests from the same client are sent to the same backend server.

 HTTP session persistence is based on cookies. The following two methods are supported:

     -   **Insert cookie**: You only need to specify the cookie timeout period.

SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP and HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

    -   **Rewrite cookie**: You can set the cookie to insert to the HTTP or HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server. For more information, see [Session persistence](../reseller.en-US/FAQ/Best practices/Configure cookie in the backend server.md#).

 |
    |**Enable Access Control**|Select whether to enable the access control function.|
    |**Access Control Method**| Select an access control method after you enable the access control function:

     -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control list are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

 |
    |**Access Control List**|Select an access control list as the whitelist or the blacklist. **Note:** An IPv6 instance can only be associated with IPv6 access control lists and an IPv4 instance can only be associated with IPv4 access control lists. For more information, see [Configure an access control list](reseller.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).

 |
    |**Enable Peak Bandwidth Limit**| Select whether to configure the listener bandwidth.

 If the SLB instance is charged based on bandwidth, you can set different peak bandwidth values for different listeners to limit the traffic passing through each listener. The sum of the peak bandwidth values of all listeners under an SLB instance cannot exceed the bandwidth value of that SLB instance.

 By default, all listeners share the bandwidth of the SLB instance.

 **Note:** SLB instances billed by traffic have no peak bandwidth limit by default.

 |
    |**Idle Timeout**|Specify the idle connection timeout period. Value range: 1 to 60. Unit: seconds. If no request is received during the specified timeout period, SLB temporarily terminates the connection and restarts the connection when the next request is received.

 Currently, this function is available in all regions.

**Note:** This function does not work for HTTP/2.0 requests.

 |
    |**Request Timeout**|Specify the request timeout period. Value range: 1 to 180. Unit: seconds. If no response is received from the backend server during the specified timeout period, SLB stops waiting and sends an HTTP 504 error code to the client.

 Currently, this function is available in all regions.

 |
    |**Enable Gzip Compression**|Choose whether to enable Gzip compression to compress files of specific formats. Now Gzip supports the following file types: text/xml, text/plain, text/css, application/javascript, application/x-javascript, application/rss+xml, application/atom+xml, and application/xml.

 |
    |**Add HTTP Header Fields**|Select the custom HTTP headers that you want to add:     -   Use the `X-Forwarded-For` field to retrieve client source IP addresses.
    -   Use the `X-Forwarded-Proto` field to retrieve the listener protocol used by the SLB instance.
    -   Use the `SLB-IP` field to retrieve the public IP address of the SLB instance.
    -   Use the `SLB-ID` field to retrieve the ID of the SLB instance.
 |
    |**Get Client Source IP Address**|HTTP listeners use X-Forwarded-For to obtain real IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Choose whether to start the listener after the listener is configured. The listener is started by default.|

2.  Click **Next**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15654/15687073657434_en-US.png)


## Step 3 Add backend servers {#section_2p9_p8x_lc1 .section}

After configuring the listener, you need to add backend servers to process requests. You can use the default server group configured for the SLB instance, or configure a VServer group or an active/standby server group for the listener. For more information, see [Backend server overview](../reseller.en-US/Backend servers/Backend server overview.md#).

In this example, use the default server group.

1.  Select **Default Server Group** and then click **Add More**. 

    ![Add default servers](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/156870736510030_en-US.png)

2.  Select the ECS instances to add, and then click **Next: Set Weight and Port**. 

    ![Configure weights](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15687073657499_en-US.png)

3.  Configure ports and weights for the added backend servers \(ECS instances\). 
    -   Port

        The port opened on the backend server to receive requests. The port number is in the range of 1 to 65535. Ports of backend servers can be the same in an SLB instance.

    -   Weight

        The weight of the backend server. A backend server with a higher weight receives more requests.

        **Note:** If the weight is set to 0, no requests are sent to the backend server.

        ![Set weights](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16139/15687073667504_en-US.png)

4.  Click **Next**.

## Step 4 Configure health checks {#section_gum_68h_177 .section}

SLB checks the service availability of backend servers by performing health checks. The health check function improves the overall availability of your services and avoids the impact of backend server failures. Click **Modify** to change health check configurations. For more information, see [Health check overview](../reseller.en-US/Health check/Health check overview.md#).

## Step 5 Submit the configurations {#section_n00_0iz_5ti .section}

To submit the listener configurations, follow these steps:

1.  On the Submit page, check the listener configurations. You can click **Modify** to change the configurations.
2.  Click **Submit**.
3.  On the Submit page, click **OK** after the configurations are successful. 

    After the configurations are successful, you can view the created listener on the **Listeners** page.


[Configure health checks](../reseller.en-US/Health check/Configure health checks.md#)

[Manage a default server group](../reseller.en-US//Manage a default server group.md#)

[Manage a VServer group](../reseller.en-US//Manage a VServer group.md#)

[Manage an active/standby server group](../reseller.en-US//Manage an active__standby server group.md#)

[Configure access control](../reseller.en-US//Configure access control.md#)

[Traffic forwarding based on domain names or URLs](../reseller.en-US/Tutorials/Traffic forwarding based on domain names or URLs.md#)

[Manage a domain name extension](../reseller.en-US/Listeners/Domain name extensions/Manage a domain name extension.md#)

[CreateLoadBalancerHTTPListener](../reseller.en-US/Developer Guide/HTTP listeners/CreateLoadBalancerHTTPListener.md#)

