# DescribeLoadBalancerHTTPListenerAttribute {#doc_api_Slb_DescribeLoadBalancerHTTPListenerAttribute .reference}

Queries the configurations of an HTTP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerHTTPListenerAttribute| The name of this action.

 Value: **DescribeLoadBalancerHTTPListenerAttribute**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earr9g6d1l-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ListenerPort|Integer|80| The frontend port used by the SLB instance.

 |
|Bandwidth|Integer|-1| The peak bandwidth of the listener.

 |
|Status|String|stopped| The status of the listener.

 Valid values:**starting | running | configuring | stopping | stopped**

 |
|XForwardedFor|String|on| Indicates whether to use X-Forwarded-For to obtain the real IP address of a visitor.

 Valid values:**on | off**

 |
|Scheduler|String|wrr| The algorithm used to distribute traffic.

 Valid values:**wrr | wlc | rr**

 |
|StickySession|String|on| Indicates whether session persistence is enabled.

 Valid values:**on | off**. Default value: off

 |
|StickySessionType|String|on| The method used to handle the cookie.

 If the value of**StickySession** is**on**, this parameter is required.

 Valid values:**insert | server**

 |
|CookieTimeout|Integer|500| The timeout period of the cookie.

 |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598| The cookie configured on the backend server.

 |
|HealthCheck|String|on| Indicates whether the health check function is enabled.

 Valid values:**on | off**

 |
|HealthCheckDomain|String|$\_ip| The domain name used for health checks.

 |
|HealthCheckURI|String|/test/index.html| The URI used for health checks.

 |
|HealthyThreshold|Integer|4| The number of consecutive successes of health checks before a backend server is declared as healthy \(from failure to success\).

 |
|UnhealthyThreshold|Integer|4| The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from success to failure\)

 |
|HealthCheckTimeout|Integer|3| The maximum length of time \(in seconds\) to wait for the response from a health check.

 |
|HealthCheckInterval|Integer|5| The time interval between two consecutive health checks. Unit: seconds

 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx| The HTTP status code indicating that the health check is normal.

 |
|HealthCheckConnectPort|Integer|8080| The port used for health checks.

 |
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group associated with the listener.

 |
|Gzip|String|on| Indicates whether Gzip compression is enabled to compress a specific file type.

 Valid values:**on | off**

 |
|AclId|String|on| The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|off| Indicates whether access control is enabled.

 Valid values:**on | off**. Default value: off

 |
|AclType|String|white| The access control type:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a white access control list poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable a whitelist without adding any IP addresses to the list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is**on**, this parameter is required.

 |
|BackendServerPort|Integer|80| The backend port used by the SLB instance.

 |
|Description|String|test| A description of the HTTP listener.

 |
|ForwardPort|Integer|80| The port used for redirecting from HTTP to HTTPS.

 **Note:** If the value of**ListenerForward** is**off**, this parameter is not displayed.

 |
|IdleTimeout|Integer|2| The idle connection timeout. Value range: 1 to 60. Default value: 15. Unit: seconds

 If no request is received during the specified timeout period, SLB temporarily terminates the connection and restarts the connection when the next request is received.

 |
|ListenerForward|String|on| Indicates whether HTTP-to-HTTPS redirection is enabled.

 -   **on**: Enabled
-   **off**: Not enabled

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The request ID.

 |
|RequestTimeout|Integer|34| The request timeout. Value range: 1 to 180. Default value: 60. Unit: seconds.

 If the backend server does not send a correct response within the specified timeout period, SLB stops waiting and sends an HTTP 504 error code to the client.

 |
|Rules| | | A description of the forwarding rule.

 |
|└Domain|String|www.example.com| The domain name.

 |
|└RuleId|String|1234| The ID of the forwarding rule.

 |
|└RuleName|String|test| The name of the forwarding rule.

 |
|└Url|String|/example| The access path.

 |
|└VServerGroupId|String|123| The ID of the target VServer group of the forwarding rule.

 |
|SecurityStatus|String|on| The security status.

 |
|XForwardedFor\_SLBID|String|on| Indicates whether the `SLB-ID` header field is used to obtain the SLB instance ID.

 |
|XForwardedFor\_SLBIP|String|on| Indicates whether the SLB-IP header field is used to obtain the real IP address of a client request.

 |
|XForwardedFor\_proto|String|on| Indicates whether the X-Forwarded-Proto header field is used to obtain the listening protocol used by the SLB instance.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeLoadBalancerHTTPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l-cn-east-hangzhou-01
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeLoadBalancerHTTPListenerAttributeResponse>
  <ForwardPort>443</ForwardPort>
  <ListenerPort>80</ListenerPort>
  <Status>stopped</Status>
  <RequestId>99439CEF-192C-4B01-A45A-2D5BD5BCDA62</RequestId>
  <ListenerForward>on</ListenerForward>
</DescribeLoadBalancerHTTPListenerAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"Status":"stopped",
	"RequestId":"99439CEF-192C-4B01-A45A-2D5BD5BCDA62",
	"ForwardPort":443,
	"ListenerForward":"on",
	"ListenerPort":80
}
```

## Error codes {#section_70a_wui_1b1 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

