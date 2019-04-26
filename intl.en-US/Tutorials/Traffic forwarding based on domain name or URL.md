# Traffic forwarding based on domain name or URL {#concept_sh5_nj5_vdb .concept}

SLB supports configuring domain name-based or URL-based forwarding rules. You can forward requests with different domain names or URLs to different backend servers by adding forwarding rules so as to well allocate server resources.

**Note:** Only Layer-7 listeners \(HTTPS/HTTP protocol\) support configuring forwarding rules.

## Introduction to domain name-based or URL-based forwarding rules {#section_hll_n31_wdb .section}

Layer-7 listeners support configuring domain name-based or URL-based forwarding rules to distribute requests with different domain names or URLs to different ECS instances.

URL-based forwarding rules support string matching and the rule with the longest matched prefix is applied. For example, if the two forwarding rules /abc and /abcd are created and a request with the prefix of /abcde is received, the rule /abcd is applied.

Domain name-based forwarding rules support exact match and wildcard match:

-   Exact domain name: www.aliyun.com
-   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

    When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

    |Type|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
    |:---|:----------|:--------------------------------|
    |:-------------|:------------|:-------------------|
    |Exact match|www.aliyun.com|✓|×|×|
    |Wildcard match|Market.aliyun.com|×|✓|×|
    |Wildcard match|info.market.aliyun.com|×|×|✓|


You can add different forwarding rules associated with different VServer groups to a Layer-7 listener \(A VServer group consists of multiple ECS instances\). For example, you can forward all read requests to a group of backend servers and forward all write requests to another group of backend servers to optimize resource usage.

After forwarding rules are configured, the sequence of request forwarding is as follows:

-   If the requests match a forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If not, but the listener is associated with a VServer group, the requests are distributed to the VServer group configured in the listener.
-   If none of the preceding conditions are met, the requests are forwarded to ECS instances in the default server group.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/15562639502798_en-US.png)

## Add a domain-name based or URL-based forwarding rule {#section_z1n_t1b_wdb .section}

Before adding the forwarding rule, make sure that the following conditions are met:

-   [Add an HTTP listener](../reseller.en-US/User Guide/Listeners/Add an HTTP listener.md#) or [Add an HTTPS listener](../reseller.en-US/User Guide/Listeners/Add an HTTPS listener.md#).
-   [Manage a VServer group](../reseller.en-US/User Guide/后端服务器/Manage a VServer group.md#).

To add a domain name-based or URL-based forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instances in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target HTTP/HTTPS listener and then click the **Add Forwarding Rules** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15562639507453_en-US.png)

6.  On the Add Forwarding Rules page, click **Add Forwarding Rules**.
7.  On the Add Forwarding Rules page, configure the forwarding rule according to the following information:

    1.  **Domain Name**: Enter the domain name of the request. It can only contain letters, numbers, dashes, or dots.
    2.  **URL**: Enter the path of the request. The URL must start with a slash \(/\), and can only contain letters, numbers, and the following special characters \(-. /%? \#&\).

        **Note:** If you only want to configure a domain name-based forwarding rule, leave the URL option empty.

    3.  **VServer Group**: Select the associated VServer group.
    4.  **Description \(optional\)**: Enter the description.
    5.  Click **OK**.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15562639517463_en-US.png)

8.  Click **Add Domain** or **Add Rule** to add another domain name-based or URL-based forwarding rule.

    For more information, see [Limits](../reseller.en-US/Limits/Limits.md#).


## Edit a forwarding rule {#section_gpm_gv4_42b .section}

You can change backend servers associated with the forwarding rule.

To edit a forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instances in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target Layer-7 listener and then click the **Add Forwarding Rules** option.
6.  In the **Forwarding Rules** area, find the target forwarding rule and then click the **Edit** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15562639517464_en-US.png)

7.  Edit the forwarding rule. Customize the scheduling algorithm, session persistence, health check and more of the forwarding rule according to the following information.

    **Note:** Currently customizing the advanced configurations of a forwarding rule is only supported in the following regions:

    -   China \(Beijing\)
    -   China \(Hangzhou\)
    -   China \(Shanghai\)
    -   China \(Zhangjiakou\)
    -   China \(Hohhot\)
    -   China \(Hong Kong\)
    -   Singapore
    -   Japan \(Tokyo\)
    |Advanced configurations|Description|
    |-----------------------|-----------|
    |**Scheduling Algorithm**|Server Load Balancer supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).    -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests than those with smaller weights.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to the backend servers.
    -   **Weighted Least Connections \(WLC\)**: A server with a higher weight will receive a larger percentage of live connections at any one time. When the weight value is the same, a backend server with a smaller number of connections is more frequently \(and probably\) accessed.
|
    |**Enable Session Persistence**| Select whether to enable session persistence.

 If session persistence is enabled, all session requests from the same client are sent to the same backend server.

 HTTP session persistence is based on cookies. The following two methods are supported:

     -   **Insert cookie**: You only need to specify the cookie timeout period.

SLB adds a cookie to the first response from the backend server \(insert SERVERID in the HTTP/HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

    -   **Rewrite cookie**: You can set the cookie to insert to the HTTP/HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server. For more information, see [Session persistence](../reseller.en-US/FAQ/Best practices/Configure cookie in the backend server.md#).

 |
    |**Enable Health Check**|     -   **Health Check Port**: The port used by health check to access backend servers.

By default, the backend port configured in the listener is used.

    -   **Health Check Path**: The URI of the health check page. We recommend that you check static pages.
    -   **Health Check Domain Name \(Optional\)**: The intranet IPs of backend servers are used as domain names by default.
    -   **Normal Status Code**: The HTTP status code that indicates a healthy server.

The default values are http\_2xx and http\_3xx.

    -   **Response Timeout**: The amount of time to wait for a response from a health check. If an ECS instance sends no response within the specified timeout period, the health check fails.
    -   **Health Check Interval**: The amount of time between two consecutive health checks.

The default value is 2 seconds.

    -   **Unhealthy Threshold**: The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\) before the ECS instance is declared unhealthy.

Valid value: 2-10. The default value is 3.

    -   **Healthy Threshold**: The number of consecutive successes of health check performed by the same LVS node server on the same ECS instance \(from failure to success\) before the ECS instance is declared healthy.

Valid value: 2-10. The default value is 3.

 |

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/155626395111504_en-US.png)

8.  Click **OK**.

## Delete a forwarding rule {#section_wsy_cw4_42b .section}

To delete a forwarding rule, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select a region and all SLB instance in this region are displayed.
3.  Click the ID of the SLB instance.
4.  Click the Listeners tab.
5.  Find the target Layer-7 listener, and then click the **Add Forwarding Rules** option.
6.  In the **Forwarding Rules** area, find the target forwarding rule and then click the **Delete** option.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15562639517465_en-US.png)


