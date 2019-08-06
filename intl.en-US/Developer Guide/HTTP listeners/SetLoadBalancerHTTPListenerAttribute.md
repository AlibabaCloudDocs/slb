# SetLoadBalancerHTTPListenerAttribute {#doc_api_Slb_SetLoadBalancerHTTPListenerAttribute .reference}

Modifies the configurations of an HTTP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerHTTPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerHTTPListenerAttribute| The name of this action.

 Value: **SetLoadBalancerHTTPListenerAttribute**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahltv0mw| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of[regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |
|AclId|String|No|123| Optional. The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off| Optional. Indicates whether to enable access control.

 Valid values:**on | off**

 |
|AclType|String|No|white| Optional. The access control method:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a white access control list poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is**on**, this parameter is required.

 |
|Bandwidth|Integer|No|-1| Optional. The peak bandwidth of the listener. Valid values:**-1 | 1 to 5120**. Unit: Mbit/s

 -   **-1**: Setting the peak bandwidth to **-1** for an Internet instance that is billed by traffic results in unlimited bandwidth.

 |
|Cookie|String|No|B490B5EBF6F3CD402E515D22BCDA1598| Optional. The cookie configured on the backend server.

 The cookie must be**1 to 200** characters in length and can only contain ASCII English letters and numbers. It cannot contain commas \(,\), semicolons \(;\), or spaces, nor can it begin with $.

 When the value of**StickySession** is**on** and the value of**StickySessionType** is**server**, this parameter is required.

 |
|CookieTimeout|Integer|No|500| Optional. Timeout period of the cookie.

 Value range:**1 to 86400**. Unit: seconds

 This parameter is required when the value of**StickySession** is**on** and the value of**StickySessionType** is**insert**.

 |
|Description|String|No|test| Optional. A description of the listener.

 |
|Gzip|String|No|on| Optional. Indicates whether to enable Gzip compression.

 |
|HealthCheck|String|No|on| Optional. Indicates whether to enable the health check function.

 Valid values:**on | off**

 |
|HealthCheckConnectPort|Integer|No|8080| Optional. The port used for health checks.

 Value range:**1 to 65535**

 |
|HealthCheckDomain|String|No|$\_ip| Optional. The domain name used for health checks. Valid values:

 -   **$\_ip**: private IP address of the backend server. If $\_ip is specified or HealthCheckDomain is not specified, SLB uses the private IP addresses of backend servers as the domain names for health checks.
-   **domain**: the domain name, which must be 1 to 80 characters in length and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx| Optional. The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by commas \(,\).

 Valid values:**http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 |
|HealthCheckInterval|Integer|No|5| Optional. The time interval between two consecutive health checks.

 Value range:**1 to 50**. Unit: seconds

 |
|HealthCheckTimeout|Integer|No|3| Optional. The length of time to wait for the response from the health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckTimeout** is smaller than that of **HealthCheckInterval**, the parameter **HealthCheckTimeout** is invalid, and the timeout is set to the value of **HealthCheckInterval**.

 |
|HealthCheckURI|String|No|/test/index.html| Optional. The URI used for health checks.

 |
|HealthyThreshold|Integer|No|4| Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to**success**\).

 Value range:**2 to 10**

 |
|IdleTimeout|Integer|No|12| Optional. The idle connection timeout. Value range: 1 to 60. Default value: 15. Unit: seconds

 If no request is received during the specified timeout period, SLB temporarily terminates the connection and restarts the connection when the next request is received.

 |
|RequestTimeout|Integer|No|3| Optional. The request timeout. Value range: 1 to 180. Default value: 60. Unit: seconds.

 If the backend server does not send a correct response during the specified timeout period, SLB stops waiting and sends an HTTP 504 error to the client.

 |
|Scheduler|String|No|wrr| Optional. The algorithm used to distribute traffic. Value values:

 -   **wrr**: A backend server with a higher weight is more likely to be polled.
-   **lc**: A server with a higher weight receives more requests.

When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.

-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 |
|StickySession|String|No|on| Optional. Indicates whether to enable session persistence.

 Valid values:**on | off**

 |
|StickySessionType|String|No|on| Optional. The method used to handle the cookie. Valid values:

 -   **insert**: Insert a cookie.

SLB adds a cookie to the first response from the backend server \(that is, it inserts SERVERID in the HTTP/HTTPS response packet\). Then, the next request contains the cookie and the listener distributes the request to the same backend server.

-   **server**: Rewrite the cookie.

SLB overwrites the original cookie when a new cookie is set. The next time the client carries the new cookie to access SLB, the listener distributes the request to the previously recorded backend server.

**Note:** If the value of**StickySession** is**on**, this parameter is required.


 |
|UnhealthyThreshold|Integer|No|4| Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success** to**failure**\).

 Value range:**2 to 10**

 |
|VServerGroup|String|No|on| Optional. Indicates whether to use a VServer group.

 Valid values:**on | off**

 |
|VServerGroupId|String|No|rsp-cige6j5e7p| Optional. The ID of the VServer group.

 |
|XForwardedFor|String|No|on| Optional. Indicates whether to get the real IP address of a client request through**X-Forwarded-For**.

 Valid values:**on | off**. Default value: on

 |
|XForwardedFor\_SLBID|String|No|on| Optional. Indicates whether to use the `SLB-ID` header field to obtain the SLB instance ID.

 Valid values:**on | off**. Default value: off

 If you do not set this parameter, the default value is used.

 |
|XForwardedFor\_SLBIP|String|No|on| Optional. Indicates whether to use the `SLB-IP` header field to obtain the real IP address of a client request.

 Valid values:**on | off**. Default value: off

 **Note:** If you do not set this parameter, the default value is used.

 |
|XForwardedFor\_proto|String|No|on| Optional. Indicates whether to use the `X-Forwarded-Proto` header field to obtain the listening protocol used by the SLB instance.

 Valid values:**on | off**. Default value: off

 If you do not set this parameter, the default value is used.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerHTTPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1qjwo61pqz3ahltv0mw
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerHTTPListenerAttributeResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</SetLoadBalancerHTTPListenerAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_ole_zp7_0ew .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

