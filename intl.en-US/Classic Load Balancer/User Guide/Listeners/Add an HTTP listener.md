# Add an HTTP listener

This topic describes how to add an HTTP listener to a Server Load Balancer \(SLB\) instance. HTTP is applicable to applications that need to identify data from different users, such as web applications and mini mobile games. You can add an HTTP listener to forward HTTP requests.

An SLB instance is created. For more information, see [Create an SLB instance]().

## Step 1: Configure the listener

Perform the following steps to configure the listener.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  Select the region where the SLB instance is deployed.

4.  Use one of the following methods to open the listener configuration wizard:

    -   On the Instances page, find the SLB instance and click **Configure Listener** in the Actions column.
    -   On the Instances page, click the ID of the SLB instance. On the Listener tab, click **Add Listener**.
5.  Set the following parameters.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select the protocol of the listener. In this example, **TCP** is selected. |
    |**Listening Port**|Set the listening port used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** You can apply for **the permissions to set the same port for TCP and UDP listeners in the same SLB instance** on the [Quota Management](https://slb.console.aliyun.com/slb/quota) page. This feature is in public preview and is supported in the following regions. In other cases, the listening ports must be unique.

    -   UAE \(Dubai\)
    -   Australia \(Sydney\)
    -   UAE \(Dubai\)
    -   UK \(London\)
    -   Germany \(Frankfurt\)
    -   US \(Silicon Valley\)
    -   US \(Virginia\)
    -   Indonesia \(Jakarta\)
    -   Japan \(Tokyo\)
    -   India \(Mumbai\)
    -   Singapore \(Singapore\)
    -   Malaysia \(Kuala Lumpur\)
    -   China \(Hong Kong\)
    -   China \(Shenzhen\)
    -   China \(Hohhot\)
    -   China \(Qingdao\)
    -   China \(Chengdu\)
    -   China \(Zhangjiakou\)
    -   China \(Shanghai\)
    -   China \(Beijing\)
    -   China \(Hangzhou\) |
    |**Advanced**|
    |**Scheduling Algorithm**|SLB supports the following scheduling algorithms: RR, WRR, WLC, and CH.     -   **Weighted Round-Robin \(WRR\)**: Backend servers with a higher weight receive more requests than those with a lower weight.
    -   **Round-Robin \(RR\)**: Requests are sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the combination of the weights and active connections of backend servers. If two backend servers have the same weight, the backend server with fewer connections is expected to receive more requests.
    -   **Consistent Hash \(CH\)**:

        -   **Source IP**: the source IP address hash. Requests from the same source IP address are scheduled to the same backend server.
        -   **Tuple**: a quadruple hash that consists of the source IP address, destination IP address, source port number, and destination port number. Requests with the same quadruple are scheduled to the same backend server.
**Note:** The CH algorithm can be used only by guaranteed-performance instances. |
    |**Enable Session Persistence**|Specify whether to enable session persistence. After session persistence is enabled, the listener forwards all requests from the same client to a specific backend server for the duration of a session.

For TCP listeners, session persistence is implemented based on IP addresses. Requests from the same IP address are forwarded to the same backend server. |
    |**Enable Access Control**|Specify whether to enable access control.|
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or CIDR blocks in the specified access control list \(ACL\) are forwarded. You can use the whitelist feature when you want to allow access from specified IP addresses.

Using the whitelist feature may pose risks to your services. After the whitelist is enabled, only the IP addresses in the ACL can access the SLB listener. If the whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are not forwarded. You can use the blacklist feature when you want to deny access from specified IP addresses.

If the blacklist is enabled without any IP addresses specified, the SLB listener forwards all requests. |
    |**Access Control List**|Select an ACL that is used as the whitelist or blacklist of the listener. **Note:** IPv6 instances can be associated only with IPv6 ACLs, while IPv4 instances can be associated only with IPv4 ACLs. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md). |
    |**Enable Connection Draining**|When connection draining is enabled, connections to the backend server can function as expected for a specific time period after they are removed or fail the health check.|
    |**Connection Draining Timeout**|After you enable connection draining, you can specify the maximum timeout period to keep connections alive before a backend server is removed from an SLB server group. After the backend server is removed or remains unhealthy for the specified time period, SLB terminates the connections to the backend server. Value values: 10 to 900.

Unit: seconds. |
    |**Enable Peak Bandwidth Limit**|Specify whether to set a bandwidth limit for the listener.

For a pay-by-bandwidth SLB instance, you can set different maximum bandwidth values for different listeners to limit listener traffic. The sum of maximum bandwidth values of all listeners that belong to the same SLB instance cannot exceed the bandwidth of this SLB instance.

By default, the bandwidth limit is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** A pay-by-data-transfer SLB instance does not impose limits on its maximum bandwidth. |
    |**Idle Timeout**|Specify the idle timeout for TCP connections. Unit: seconds. Valid values: 10 to 900.|
    |**Listener Name**|Enter a name for the listener.|
    |**Obtain Client Source IP Address**|For Layer 4 listeners, backend servers can directly obtain the actual IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Specify whether to start the listener immediately after it is configured. By default, the listener is started after it is configured.|

6.  Click **Next**.


## Step 2: Configure an HTTP listener

To configure an HTTP listener, perform the following operations:

1.  On the Protocol and Listener wizard page, set the following parameters.

    |Parameter|Description|
    |:--------|:----------|
    |**Select Listener Protocol**|Select a protocol for the listener. **HTTP** is selected in this example. |
    |**Listening Port**|Specify the listening port that is used to receive requests and forward them to backend servers. Valid values: 1 to 65535.

**Note:** You must not specify the same listening port for listeners that are associated with the same SLB instance. |
    |**Advanced**|
    |**Scheduling Algorithm**|SLB supports three scheduling algorithms: round robin \(RR\), weighted round robin \(WRR\), and weighted least connections \(WLC\).     -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests.
    -   **Round-Robin \(RR\)**: Requests are sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: Requests are distributed based on the weights and active connections of backend servers. Requests are distributed to the backend server with the least number of active connections. If two backend servers have the same number of active connections, the backend server with a higher weight receives more requests. |
    |**Redirection**|Specify whether to redirect traffic from the HTTP listener to an HTTPS listener. **Note:** Before you enable redirection, make sure that you have created an HTTPS listener. |
    |**Enable Session Persistence**|Specify whether to enable session persistence.

After session persistence is enabled, SLB forwards all requests from a client to the same backend server.

SLB maintains the persistence of HTTP sessions based on cookies. SLB allows you to use the following methods to process cookies:

    -   **Insert cookie**: You only need to specify the timeout period of the cookie.

SLB inserts a cookie \(SERVERID\) into the first HTTP or HTTPS response packet that is sent to a client. The next request from the client contains this cookie and the listener distributes this request to the recorded backend server.

    -   **Rewrite cookie**: You can specify the cookie to be inserted into an HTTP or HTTPS response. You must specify the timeout period and lifecycle of this cookie on the backend server.

After you specify a cookie, SLB overwrites the original cookie with the specified cookie. The next time SLB receives a client request that carries the specified cookie, the listener distributes the request to the recorded backend server. For more information, see [Configure session persistence rules](/intl.en-US/Classic Load Balancer/FAQ/Configure cookie in the backend server.md). |
    |**Enable Access Control**|Specify whether to enable access control.|
    |**Access Control Method**|Select an access control method after you enable access control.

    -   **Whitelist**: Only the requests from the IP addresses or CIDR blocks in the specified access control list \(ACL\) are forwarded. You can choose this option if you want to allow requests from specified IP addresses.

Using the whitelist may pose risks to your services. After the whitelist is enabled, only IP addresses in the whitelist are forwarded by the SLB listener. If the whitelist does not contain any IP addresses, the SLB listener forwards all requests.

    -   **Blacklist**: Requests from the IP addresses or CIDR blocks in the specified ACL are blocked. You can choose this option if you want to block requests from specified IP addresses.

If the blacklist does not contain any IP addresses, the SLB listener forwards all requests. |
    |**Access Control List**|Select the ACL that is used as the whitelist or blacklist of the listener. **Note:** IPv6 instances can be associated with only IPv6 ACLs and IPv4 instances can be associated with only IPv4 ACLs. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md). |
    |**Enable Peak Bandwidth Limit**|Specify whether to enable bandwidth capping for the listener.

If an SLB instance is billed based on bandwidth, you can set different maximum bandwidth values for different listeners to limit the amount of traffic that flows through each listener. The sum of the maximum bandwidth values of all listeners that are added to an SLB instance cannot exceed the bandwidth of the SLB instance.

By default, this feature is disabled and all listeners share the bandwidth of the SLB instance.

**Note:** If an SLB instance is billed based on the amount of data transfer, the bandwidth of its listeners is not limited by default. |
    |**Idle Timeout**|Specify the timeout period of idle connections. Unit: seconds. Valid values: 1 to 60. If no request is received within the timeout period, SLB closes the connection. SLB recreates the connection after it receives a new connection request.

This feature is available in all regions.

**Note:** This feature is unavailable for HTTP/2 requests. |
    |**Request Timeout**|Specify the request timeout period. Unit: seconds. Valid values: 1 to 180. If no response is received from the backend server within the request timeout period, SLB returns an HTTP 504 error to the client.

This feature is available in all regions. |
    |**Enable Gzip Compression**|Specify whether to enable compression for a specified file type. Gzip supports the following file types: text/xml, text/plain, text/css, application/javascript, application/x-javascript, application/rss+xml, application/atom+xml, and application/xml. |
    |**Add HTTP Header Fields**|You can add the following HTTP header fields:     -   Use the `X-Forwarded-For` header field to retrieve the IP addresses of clients.
    -   Use the `X-Forwarded-Proto` header field to retrieve the listener protocol used by the SLB instance.
    -   Use the `SLB-IP` header field to retrieve the public IP address of the SLB instance.
    -   Use the `SLB-ID` header field to retrieve the ID of the SLB instance. |
    |**Obtain Client Source IP Address**|HTTP listeners use the X-Forwarded-For header field to obtain the real IP addresses of clients.|
    |**Automatically Enable Listener After Creation**|Specify whether to immediately enable the listener after the listener is created. By default, the listener is enabled after it is created.|

2.  Click **Next**.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9113359951/p7434.png)


## Step 3: Add backend servers

After you configure the listener, you must add backend servers to process client requests. You can use the default server group that is configured for the SLB instance, or create a vServer group or a primary/secondary server group. For more information, see [Backend server overview](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Backend server overview.md).

Backend servers are added to the default server group in this example.

1.  Select **Default Server Group** and click **Add More**.

    ![Add backend servers to the default server group](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p10030.png)

2.  In the **My Servers** panel, select the Elastic Compute Service \(ECS\) instances that you want to add as backend servers and click **Next**.

    ![Configure weights](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2213359951/p7499.png)

3.  On the **Configure Ports and Weights** wizard page, specify the weights of the backend servers that you want to add. A backend server with a higher weight receives more requests.

    **Note:** If the weight of a backend server is set to 0, no request is distributed to the backend server.

4.  Click **Add**. On the Default Server Group tab, specify the ports that you want to open on the backend servers \(ECS instances\) to receive requests. Valid values: 1 to 65535.

    You can specify the same port on different backend servers that are connected to an SLB instance.

5.  Click **Next**.


## Step 3: Configure health checks

SLB checks the availability of Elastic Compute Service \(ECS\) instances that serve as backend servers by performing health checks. The health check feature improves the overall availability of your frontend business and mitigates the impacts of exceptions that occur on backend ECS instances. Click **Modify** to modify the configurations of health checks. For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

## Step 4: Confirm the configurations

Perform the following steps to confirm the configurations.

1.  In the Confirm step, check the configurations. You can click **Modify** to modify the configurations.

2.  After you confirm the configurations, click **Submit**.

3.  In the Configuration Successful message, click **OK**.

    You can check the created listener on the Listener tab.


**Documentation**  


[Add ECS instances to the default server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Default server groups/Add ECS instances to the default server group.md)

[Configure health check](/intl.en-US/Classic Load Balancer/User Guide/Health check/Configure health checks.md)

[Add ECS instances to a VServer group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/VServer groups/Add ECS instances to a VServer group.md)

[Add ECS instances to a primary/secondary server group](/intl.en-US/Classic Load Balancer/User Guide/Backend servers/Active/standby server groups/Add ECS instances to a primary/secondary server group.md)

[Overview](/intl.en-US/Classic Load Balancer/User Guide/Access control/Overview.md)

[Forward requests based on domain names or URLs](/intl.en-US/Tutorials/Forward requests based on domain names or URLs.md)

[Manage a domain name extension](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Domain name extensions/Manage a domain name extension.md)

[CreateLoadBalancerHTTPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP listeners/CreateLoadBalancerHTTPListener.md)

