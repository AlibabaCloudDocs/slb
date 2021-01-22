# DescribeLoadBalancerHTTPListenerAttribute

You can call this operation to query the configurations of an HTTP listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPListenerAttribute&type=RPC&version=2014-05-15)

## Request Parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeLoadBalancerHTTPListenerAttribute|The operation that you want to perform.

 Set the value to **DescribeLoadBalancerHTTPListenerAttribute**. |
|ListenerPort|Integer|Yes|80|The listener port of the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1o94dp5\*\*\*\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is deployed.

 You can retrieve the region ID from the [Regions and zones](~~40654~~) list or by calling the[DescribeRegions](~~25609~~) operation. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|ListenerPort|Integer|80|The listener port of the SLB instance. |
|Bandwidth|Integer|-1|The peak bandwidth of the listener. |
|Status|String|stopped|The status of the listener.

 Valid Values: **running and stopped**.

 -   **running**: Indicates that the listener is running normally.
-   **stopped**: Indicates that the listener is stopped. |
|XForwardedFor|String|on|Specifies whether to use the X-Forwarded-For header to obtain the real IP address of the client.

 Valid values: **on and off**. |
|Scheduler|String|wrr|The scheduling algorithm. Default value: wrr.

 Valid values: **wrr, wlc, and rr**.

 -   **wrr**: A backend server with a higher weight is expected to receive more requests.
-   **wlc**: Requests are forwarded based on the weight and load \(the number of connections\) of each backend server. If two backend servers have the same weight, the backend server with fewer connections is expected to receive more requests.
-   **rr**: Requests are distributed to each backend server on a rotation. |
|StickySession|String|on|Specifies whether to enable session persistence. Default value: off.

 Valid values: **on and off**. |
|StickySessionType|String|insert|The method used to handle a cookie.

 Valid values: **insert and server.**

 -   insert: Inserts a cookie.

SLB inserts a cookie \(SERVERID\) to the first HTTP or HTTPS response packet sent to a client. The next request from the client will contain the cookie, and the listener will deliver the request to the backend server with the specified SERVERID.

-   server: Rewrites a cookie.

When SLB detects a user-defined cookie, it overwrites the original cookie with the user-defined cookie. The next request from the client will contain the user-defined cookie, and the listener will distribute the request to the recorded backend server.


 **Note:** If you set the **StickySession** parameter to **on**, you must specify this parameter. |
|CookieTimeout|Integer|500|The timeout period of a cookie. Unit: seconds. |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|The cookie configured on the backend server. |
|HealthCheck|String|on|Specifies whether to enable health check.

 Valid values: **on and off**. |
|HealthCheckDomain|String|www.domain.com|The domain name used for health check. |
|HealthCheckURI|String|/test/index.html|The URI used for health check.

 The value must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\). The URI must not be a single forward slash \(/\) and it must start with a forward slash \(/\). |
|HealthyThreshold|Integer|4|The healthy threshold. |
|UnhealthyThreshold|Integer|4|The unhealthy threshold. |
|HealthCheckTimeout|Integer|3|The timeout period of each health check response. Unit: seconds. |
|HealthCheckInterval|Integer|5|The interval between two consecutive health checks. Unit: seconds. |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|The HTTP status code indicating that the health check is successful. |
|HealthCheckConnectPort|Integer|8080|The port used for health check.

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|VServerGroupId|String|rsp-cige6j\*\*\*\*|The ID of the VServer group. |
|Gzip|String|on|Specifies whether to enable Gzip compression to compress files of a specific type.

 Valid values: **on and off**. |
|AclId|String|on|The ID of the Access Control List \(ACL\) to which the listener is bound.

 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|off|Specifies whether to enable access control for the listener. Default value: off.

 Valid values: **on and off**. |
|AclType|String|white|The type of the ACL. Valid values: white and black.

 -   **white**: Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. The whitelist is used to allow only specified IP addresses to access an application.

Enabling the whitelist may pose risks to your workloads. After the whitelist is enabled, only the IP addresses in the ACL can access the SLB listener. If a whitelist is enabled and no IP address is specified, the SLB listener does not forward any requests.

-   **black**: All requests from the IP addresses or CIDR blocks in the ACL are denied. The blacklist is used to forbid specified IP addresses from accessing an application.

If a blacklist is enabled and no IP address is specified, the SLB listener forwards all requests.


 This parameter is required when the **AclStatus** parameter is set to **on**. |
|BackendServerPort|Integer|80|The backend port used by the SLB instance. |
|Description|String|test|The description of the HTTP listener. |
|ForwardPort|Integer|80|The port used to redirect HTTP requests to HTTPS.

 **Note:** If the value of the**ListenerForward** parameter is set to **off**, this parameter is not displayed. |
|IdleTimeout|Integer|2|The timeout period of an idle connection. Valid values: 1 to 60. Default value: 15. Unit: seconds.

 If no request is received during the specified timeout period, SLB closes the connection and starts a new connection when it receives a new connection request. |
|ListenerForward|String|on|Indicates whether HTTP-to-HTTPS redirection is enabled.

 -   **on**: enabled
-   **off**: disabled |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|RequestTimeout|Integer|34|The timeout period of a request. Valid values: 1 to 180. Unit: seconds. Default value: 60.

 If the backend server does not response within the specified timeout period, SLB returns an HTTP 504 error to the client. |
|Rules|Array| |The description of the forwarding rule. |
|Rule| | | |
|Domain|String|www.example.com|The domain name corresponding to the task that was queried. |
|RuleId|String|1234|The ID of the forwarding rule. |
|RuleName|String|test|The name of the forwarding rule. |
|Url|String|/example|The request URL. |
|VServerGroupId|String|123|The ID of the target VServer group in the forwarding rule. |
|SecurityStatus|String|on|The security status.

 Set the value to **on and off**. |
|XForwardedFor\_SLBID|String|on|Indicates whether the `SLB-ID` header is used to obtain the ID of the SLB instance. |
|XForwardedFor\_SLBIP|String|on|Indicates whether the SLB-IP header is used to obtain the real IP address of the client. |
|XForwardedFor\_proto|String|on|Indicates whether the X-Forwarded-Proto header is used to obtain the listener protocol of the SLB instance. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancerHTTPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1o94dp5*********
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeLoadBalancerHTTPListenerAttributeResponse>
    <ForwardPort>443</ForwardPort>
    <ListenerPort>80</ListenerPort>
    <Status>stopped</Status>
    <RequestId>99439CEF-192C-4B01-A45A-2D5BD5BCDA62</RequestId>
    <ListenerForward>on</ListenerForward>
</DescribeLoadBalancerHTTPListenerAttributeResponse>
```

`JSON` format

```
{
    "ForwardPort": 443, 
    "ListenerPort": 80, 
    "Status": "Stopped", 
    "RequestId": "99439CEF-192C-4B01-A45A-2D5BD5BCDA62", 
    "ListenerForward": "on"
}
```

## Error codes.

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

