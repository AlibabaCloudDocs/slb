# Traffic forwarding based on domain names or URLs {#concept_sh5_nj5_vdb .concept}

Server Load Balancer \(SLB\) supports domain name-based and URL-based forwarding rules. You can forward requests with different domain names or URLs to different backend servers so that you can optimize the utilization of your server resources.

**Note:** Only Layer-7 listeners \(HTTP/HTTPS protocol\) support forwarding rules.

## Introduction to domain name-based and URL-based forwarding rules {#section_hll_n31_wdb .section}

Layer-7 listeners support domain name-based and URL-based forwarding rules to distribute requests with different domain names or URLs to different ECS instances.

URL-based forwarding rules support string matching and the rule with the longest matched prefix is applied. For example, if the two forwarding rules /abc and /abcd are created and a request with the prefix of /abcde is received, the rule /abcd is applied.

Domain name-based forwarding rules support exact match and wildcard match.

-   Exact domain name: www.aliyun.com
-   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

    When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

    |Type|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
    |:---|:----------|:--------------------------------|
    |:-------------|:------------|:-------------------|
    |Exact match|www.aliyun.com|✓|×|×|
    |Wildcard match|market.aliyun.com|×|✓|×|
    |Wildcard match|info.market.aliyun.com|×|×|✓|


You can add different forwarding rules associated with different VServer groups to a Layer-7 listener \(a VServer group consists of multiple ECS instances\). For example, you can forward all read requests to a VServer group and forward all write requests to another VServer group to optimize resource usage.

After forwarding rules are configured, the sequence of request forwarding is as follows:

-   If the requests match a forwarding rule, the requests are distributed to the VServer group associated with the rule.
-   If not, but the listener is associated with a VServer group, the requests are distributed to the VServer group configured in the listener.
-   If none of the above conditions are met, the requests are forwarded to ECS instances in the default server group.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/15607374502798_en-US.png)

## Add a domain name-based or URL-based forwarding rule {#section_z1n_t1b_wdb .section}

Before you add a forwarding rule, make sure that the following conditions are met:

-   [Add an HTTP listener](../intl.en-US/User Guide/Listeners/Add an HTTP listener.md#) or [Add an HTTPS listener](../intl.en-US/User Guide/Listeners/Add an HTTPS listener.md#).
-   [Create a VServer group](intl.en-US/Archives/User Guide (Old Console)/Backend servers/Create a VServer group.md#).

To add a domain name-based or URL-based forwarding rule, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target HTTP or HTTPS listener and then click **Add Forwarding Rules**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15607374507453_en-US.png)

6.  On the Add Forwarding Rules page, configure the forwarding rule according to the following information and click **Add Forwarding Rules**.

    1.  **Domain Name**: Enter the domain name of the requests to be forwarded. The domain name can only contain letters, numbers, hyphens \(-\), or periods \(.\).
    2.  **URL**: Enter the path of the requests to be forwarded. The URL must start with a slash \(/\), and can only contain letters, numbers, and the following special characters: - . / % ? \# &

        **Note:** If you only want to configure a domain name-based forwarding rule, leave the URL empty.

    3.  **VServer Group**: Select the VServer group that you want to forward the requests to.
    4.  **Description \(optional\)**: Enter a description for the forwarding rule.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15607374507463_en-US.png)

7.  To add another domain name-based or URL-based forwarding rule, click **Add Domain** or **Add Rule**.

    For more information, see [Limits](../intl.en-US/Limits/Limits.md#).

8.  Click **OK**.

## Edit a forwarding rule {#section_gpm_gv4_42b .section}

You can change the backend servers associated with the forwarding rule.

To edit a forwarding rule, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target HTTP or HTTPS listener and then click **Add Forwarding Rules**.
6.  In the **Forwarding Rules** section, find the target forwarding rule and then click **Edit**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15607374517464_en-US.png)

7.  Edit the forwarding rule. Customize the advanced configurations such as scheduling algorithm, session persistence, and health checks according to the following information:

    **Note:** Currently, customizing the advanced configurations of a forwarding rule is only supported in the following regions:

    -   China \(Beijing\)
    -   China \(Hangzhou\)
    -   China \(Shanghai\)
    -   China \(Zhangjiakou\)
    -   China \(Hohhot\)
    -   Hong Kong
    -   Singapore
    -   Japan \(Tokyo\)
    |Advanced configurations|Description|
    |-----------------------|-----------|
    |**Scheduling Algorithm**|SLB supports three scheduling algorithms: round robin, weighted round robin \(WRR\), and weighted least connections \(WLC\).     -   **Weighted Round-Robin \(WRR\)**: Backend servers with higher weights receive more requests.
    -   **Round-Robin \(RR\)**: Requests are evenly and sequentially distributed to backend servers.
    -   **Weighted Least Connections \(WLC\)**: A backend server with a higher weight will receive more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
 |
    |**Enable Session Persistence**| Select whether to enable session persistence.

 After you enable session persistence, all session requests from the same client are sent to the same backend server.

 HTTP session persistence is based on cookies. The following two methods are supported:

     -   **Insert cookie**: You only need to specify the cookie timeout period.

SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP/HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

    -   **Rewrite cookie**: You can set the cookie to insert to the HTTP/HTTPS response according to your needs. You must maintain the timeout period and lifecycle of the cookie on the backend server.

SLB will overwrite the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server. For more information, see [Session persistence](../intl.en-US/FAQ/Best practices/Configure cookie in the backend server.md#).

 |
    |**Enable Health Check**|     -   **Health Check Port**: the port used by health checks to access backend servers.

By default, the backend port configured in the listener is used.

    -   **Health Check Path**: the URI of the health check web page. We recommend that you check a static web page.
    -   **Health Check Domain Name \(Optional\)**: The intranet IP addresses of backend servers are used as health check domain names by default.
    -   **Normal Status Code**: the HTTP status code that indicates a healthy server.

The default values are http\_2xx and http\_2xx.

    -   **Response Timeout**: the amount of time to wait for a response from a health check. If an ECS instance sends no response within the specified timeout period, the health check fails.
    -   **Health Check Interval**: the amount of time between two consecutive health checks.

The default value is 2 seconds.

    -   **Unhealthy Threshold**: the number of consecutive health check failures performed by the same LVS node server on the same ECS instance \(from success to failure\) before the ECS instance is declared unhealthy.

Value range: 2 to 10. Default value: 3.

    -   **Healthy Threshold**: the number of consecutive health check successes performed by the same LVS node server on the same ECS instance \(from failure to success\) before the ECS instance is declared healthy.

Value range: 2 to 10. Default value: 3.

 |

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/156073745111504_en-US.png)

8.  Click **OK**.

## Delete a forwarding rule {#section_wsy_cw4_42b .section}

To delete a forwarding rule, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Click the ID of the target SLB instance.
4.  Click the Listeners tab.
5.  Find the target HTTP or HTTPS listener, and then click **Add Forwarding Rules**.
6.  In the **Forwarding Rules** section, find the target forwarding rule and then click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15660/15607374517465_en-US.png)


