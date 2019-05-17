# Configure health checks {#concept_iz4_ypn_vdb .concept}

You can configure health check settings when adding a listener. In general, the default settings can meet your requirements.

## Configure health checks {#section_rsr_4cb_wdb .section}

You can configure the health check function of a listener in the console or through APIs. For more information, see [Health check overview](intl.en-US/User Guide/Health check/Health check overview.md#) and [Health check FAQ](../../../../intl.en-US/FAQ/Heath check FAQs.md#).

To configure the health check function, complete these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select a region and all SLB instances in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  On the **Instance Details** page, click the **Listeners** tab.
5.  Click **Add Listener** or the **Configure** option of the target listener.
6.  On the Health Check page, configure the health check function.

    We recommend that you use the default values when you configure the health check function.

    |Configuration|Description|
    |:------------|:----------|
    |**Health Check Protocol**| For TCP listeners, both TCP health checks and HTTP health checks are supported.

    -   TCP health check is based on network layer detection.
    -   HTTP health check is performed by sending head requests.
 |
    |**Health Check Method** \(HTTP and HTTPS health checks only\)|Health checks of Layer-7 listeners \(HTTP and HTTPS listeners\) support both the HEAD and the GET request methods. The HEAD request method is used by default. Therefore, if your backend servers do not support the HEAD request method or the HEAD request method is disabled, health checks may fail. To resolve this issue, you can choose to use the GET request method for health checks. However, only the India \(Mumbai\) region supports the GET request method. Support for other regions is in development.

 When the GET request method is used, response packets may be truncated if the response packets exceed 8 KB. However, the results of health checks are not affected.

 |
    |**Health Check Path and Domain Name** \(HTTP health checks only\)

 |By default, SLB sends an HTTP head request to the default homepage configured on the application server through the intranet IP address of the backend ECS instance to do the health check. If you do not use the default homepage of the application server to do health checks, you must specify the URL for health checks.

 Some application servers verify the host field in the request. Therefore, the request header must contain the host field. If a domain name is configured in the health check, Server Load Balancer adds the domain name to the host field when forwarding the request to the backend server. If not, the health check request will be denied by the server and the health check may fail. Therefore, if your application server verifies the host field in the request, you must configure a domain name to make sure the health check works.

 |
    |**Normal Status Code** \(HTTP health check only\)

 |Select the HTTP status code indicating that the health check is normal. The default values are http\_2xx and http\_2xx.

 |
    |**Health Check Port**|The detection port used by the health check to access the backend ECS instances. By default, the backend port configured in the listener is used.

 **Note:** If a VServer group or an active/standby server group is configured for the listener, and the ECS instances in the group use different ports, leave this option empty. SLB uses the backend port of each ECS instance to do health checks.

 |
    |**Response Timeout**|The amount of time in seconds to wait for the response from a health check. If the backend ECS instance does not respond correctly within the specified time, the health check fails. The timeout range is 1 to 300 seconds. The default value is 10 seconds for UDP listeners and 5 seconds for HTTP/HTTPS/TCP listeners.

 |
    |**Health Check Interval**|The time interval between two consecutive health checks. All node servers in the LVS cluster independently and concurrently perform health checks on backend ECS instances according to the interval. The statistics from a health check request on a single ECS instance cannot reflect the health check interval because the health check time of each node server is not synchronized.

 The time range is 1 to 50 seconds. The default value is 5 seconds for UDP listeners, and 2 seconds for HTTP/HTTPS/TCP listeners.

 |
    |**Unhealthy Threshold**|The number of consecutive failures of health check performed by the same LVS node server on the same ECS instance \(from success to failure\). Value range: 2 to 10. Default value: 3.

 |
    |**Healthy Threshold**|The number of consecutive successes of health check performed by the same LVS mode server on the same ECS instance \(from failure to success\). Value range: 2 to 10. Default value: 3.

 |
    |**Health Check Requests and Results**|When configuring health checks for UDP listeners, you can enter the request contents \(such as **youraccountID**\) in **Health Check Request** and the expected response \(such as **slb123**\) in **Health Check Response**. Add the corresponding health check response logic to the application logic of the backend server. For example, return slb123 when youraccountID is received.

 If SLB receives the expected response from the backend server, the health check succeeds. Otherwise, the health check fails. This method can maximally guarantee the reliability of health checks.

 |

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15664/15580601517332_en-US.png)


## Example of health check response timeout and health check interval {#section_krm_4gb_wdb .section}

Take the following health check configurations as the example:

-   **Response Timeout: 5 seconds**
-   **Health Check Interval: 2 seconds**
-   **Healthy Threshold: 3 times**
-   **Unhealthy Threshold: 3 times**

Health check failure time window = Response Timeout × Unhealthy Threshold + Health Check Interval × \(Unhealthy Threshold - 1\). That is, 5 3 + 2 × \(3 - 1\) = 19s.

The following figure shows the process to declare an unhealthy backend server:

![](images/31894_en-US_source.png)

Health check success time window = Health check response time × Healthy Threshold + Health Check Interval × \(Healthy Threshold - 1\). That is, \(1 × 3\) + 2 × \(3 - 1\) = 7s.

**Note:** Health check response time is the duration from the time when the health check request is sent to the time when the response is received. When the TCP health check is used, the time is very short and almost negligible because the health check only detects whether the port is alive. When the HTTP health check is used, the response time depends on the performance and load of the application server and is usually within seconds.

The following figure shows the process to declare a healthy backend server \(Assume that it takes 1 second for the backend server to respond to the health check request\):

![](images/11917_en-US_source.png)

## Configure a domain name in HTTP health checks {#section_muy_e2q_xkj .section}

When the HTTP health check is used, you can set a domain name for the health check, but it is not a required option. Some application servers verify the host field in the request. Therefore, the request header must contain the host field. If a domain name is configured in the health check, Server Load Balancer adds the domain name to the host field when forwarding the request to the backend server. If not, the health check request will be denied by the server and the health check may fail. Therefore, if your application server verifies the host field in the request, you must configure a domain name to make sure the health check works.

