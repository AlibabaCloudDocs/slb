# Configure health checks {#concept_iz4_ypn_vdb .concept}

You can configure the health check function when you add a listener. Generally, the default settings can meet your requirements.

## Configure health checks {#section_rsr_4cb_wdb .section}

You can configure the health check function of a listener through the Server Load Balancer \(SLB\) console or APIs. For more information, see [Health check overview](intl.en-US/Health check/Health check overview.md#) and [Health check FAQ](../intl.en-US/FAQ/Health check FAQ.md#).

To configure the health check function, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  On the **Instance Details** page, click the **Listeners** tab.
5.  Click **Add Listener**, or find the target listener and click **Configure** in the Actions column.
6.  On the Health Check page, configure the health check function.

    We recommend that you use the default values when you configure the health check function.

    |Configuration|Description|
    |:------------|:----------|
    |**Health Check Protocol**| For TCP listeners, both TCP health checks and HTTP health checks are supported.

    -   TCP health checks are based on network layer detection.
    -   HTTP health checks are performed by sending HEAD requests.
 |
    |**Health Check Method** \(HTTP and HTTPS health checks only\)

 |Health checks of Layer-7 listeners \(HTTP and HTTPS listeners\) support both the HEAD and the GET request methods. The HEAD request method is used by default. Therefore, if your backend servers do not support the HEAD request method or the HEAD request method is disabled, health checks may fail. To resolve this issue, you can choose to use the GET request method for health checks.

 However, only the India \(Mumbai\) region supports the GET request method. Support for other regions is in development.

 **Note:** When the GET method is used, if the response length exceeds 8 KB, it is truncated, but the health check result is not affected.

 |
    |**Health Check Path and Domain Name** \(HTTP health checks only\)

 |By default, SLB sends an HTTP HEAD request to the default homepage configured on the application server through the intranet IP address of the backend ECS instance to do health checks. If you do not use the default homepage of the application server to do health checks, you must specify the URL for health checks.

 Some application servers verify the host field in a request. Therefore, the request header must contain the host field. If a domain name is configured in the health check function, SLB adds the domain name to the host field when forwarding a request to the backend server. If no domain name is configured, no host field will be contained in the request, the health check request will be denied by the server, and the health check may fail. Therefore, if your application server verifies the host field in the request, you must configure a domain name to make sure the health check works.

 |
    |**Normal Status Code** \(HTTP health checks only\)

 |Select the HTTP status code that indicates normal health checks. The default values are http\_2xx and http\_3xx.

 |
    |**Health Check Port**|The detection port used by health checks to access backend servers. By default, the backend port configured in the listener is used.

 **Note:** If a VServer group or an active/standby server group is configured for the listener, and the ECS instances in the group use different ports, leave this parameter empty. SLB uses the backend port of each ECS instance to do health checks.

 |
    |**Response Timeout**|The length of time to wait for the response from a health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails. Value range: 1 to 300. Unit: seconds. Default value for UDP listeners: 10. Default value for HTTP, HTTPS, and TCP listeners: 5.

 |
    |**Health Check Interval**|The time interval between two consecutive health checks. All node servers in the LVS cluster independently and concurrently perform health checks on backend ECS instances according to the interval. The statistics from a health check request on a single ECS instance cannot reflect the health check interval because the health check time of each node server is not synchronized.

 Value range: 1 to 50. Unit: seconds. Default value for UDP listeners: 5. Default value for HTTP, HTTPS, and TCP listeners: 2.

 |
    |**Unhealthy Threshold**|The number of consecutive failures of health checks performed by the same LVS node server on the same ECS instance before the ECS instance is declared as unhealthy \(from success to failure\). Value range: 2 to 10. Default value: 3.

 |
    |**Healthy Threshold**|The number of consecutive successes of health checks performed by the same LVS node server on the same ECS instance before the ECS instance is declared as healthy \(from failure to success\). Value range: 2 to 10. Default value: 3.

 |
    |**Health Check Requests and Results**|When you configure health checks for UDP listeners, you can enter the request contents \(such as **youraccountID**\) in **Health Check Request** and the expected response \(such as **slb123**\) in **Health Check Response**. Add the corresponding health check response logic to the application logic of the backend server. For example, return slb123 when youraccountID is received.

 If SLB receives the expected response from the backend server, the health check succeeds. Otherwise, the health check fails. This method can guarantee the reliability of health checks.

 |

7.  SLB supports health check diagnostics on backend servers.
    1.  Click **Health Check Diagnostics** in the **Advanced** section.

        **Note:** If you log on as a RAM user, you must grant permissions to the RAM user before it can use the health check diagnostics function. Click [here](http://icms.alibaba-inc.com/document/content/5266?topic=15664) to grant permissions to a RAM user.

    2.  Find the target backend server, and click **Diagnose** in the **Actions** column.

        To check multiple backend servers at a time, select target backend servers and click **Batch**. Up to five backend servers can be selected at the same time. If the number of backend servers is larger than five, check the backend servers in batches.

    3.  Click **OK**.

## Example of the health check response timeout and health check interval {#section_krm_4gb_wdb .section}

Take the following health check configurations as the example:

-   **Response Timeout: 5 seconds**
-   **Health Check Interval: 2 seconds**
-   **Healthy Threshold: 3 times**
-   **Unhealthy Threshold: 3 times**

Health check failure time window = Response Timeout × Unhealthy Threshold + Health Check Interval × \(Unhealthy Threshold - 1\). That is, 5 × 3 + 2 × \(3 - 1\) = 19s.

The following figure shows the process to declare an unhealthy backend server:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4138/15645484122816_en-US.png)

Health check success time window = Health check response time × Healthy Threshold + Health Check Interval × \(Healthy Threshold - 1\). That is, \(1 × 3\) + 2 × \(3 - 1\) = 7s.

**Note:** Health check response time is the duration from the time when the health check request is sent to the time when the response is received. When the TCP health check is used, the time is very short and almost negligible because the health check only detects whether the port is alive. When the HTTP health check is used, the response time depends on the performance and load of the application server and is usually within seconds.

The following figure shows the process to declare a healthy backend server \(assume that it takes one second for the backend server to respond to the health check request\):

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4138/15645484122820_en-US.png)

## Configure a domain name in HTTP health checks {#section_yft_fhb_wdb .section}

When the HTTP health check is used, you can set a domain name for the health check, but it is not required. Some application servers verify the host field in the request. Therefore, the request header must contain the host field. If a domain name is configured in the health check function, SLB adds the domain name to the host field when forwarding the request to the backend server. If not, the health check request will be denied by the server and the health check may fail. Therefore, if your application server verifies the host field in the request, you must configure a domain name to make sure the health check works.

