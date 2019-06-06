# SetLoadBalancerHTTPSListenerAttribute {#doc_api_Slb_SetLoadBalancerHTTPSListenerAttribute .reference}

Modifies the configurations of an HTTPS listener.

Modifies the configurations of an HTTPS listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerHTTPSListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerHTTPSListenerAttribute|The name of this action. Value:**SetLoadBalancerHTTPSListenerAttribute**

 |
|ListenerPort|Integer|Yes|80|The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|139a00604ad-cn-east-hangzhou-01|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call the [DescribeRegions](~~25609~~) API.

 |
|AclId|String|No|56565|Optional. The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off|Optional. Indicates whether to enable access control.

 Valid values: **on | off**

 |
|AclType|String|No|white|Optional. The access control type:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable a whitelist without adding any IP addresses to the list, no requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|Bandwidth|Integer|No|-1|Optional. The peak bandwidth of the listener. Valid values:**-1 | 1 to 5120**

 -   **-1**: The peak bandwidth is not limited.
-   **1 to 5120**: the peak bandwidth of the listener. The sum of the peak bandwidth values of all listeners cannot surpass the peak bandwidth of the instance.

 |
|CACertificateId|String|No|139a00604ad-cn-east-hangzhou-01|Optional. The ID of the CA certificate.

 If both the CA certificate and the server certificate are uploaded, mutual authentication is established. If only the server certificate is uploaded, one-way authentication is established.

 |
|Cookie|String|No|B490B5EBF6F3CD402E515D22BCDA1598|Optional. The cookie configured on the backend server.

 The cookie must be 1 to 200 characters in length and can only contain ASCII English letters and numbers. It cannot contain commas \(,\), semicolons \(;\), or spaces, nor can it begin with $.

 When the value of **StickySession** is **on** and the value of **StickySessionType** is **server**, this parameter is required.

 |
|CookieTimeout|Integer|No|500|Optional. Timeout period of the cookie.

 Value range:**1 to 86400**. Unit: seconds

 **Note:** This parameter is required when the value of **StickySession** is **on** and the value of **StickySessionType** is **insert**.

 |
|Description|String|No|A description of the listener|Optional. A description of the listener.

 |
|EnableHttp2|String|No|off|Optional. Indicates whether to enable the HTTP/2 feature.

 Valid values: **on | off**

 |
|Gzip|String|No|on|Optional. Indicates whether to enable Gzip compression to compress a specific file type.

 Valid values:**on | off**. Default value: off

 |
|HealthCheck|String|No|on|Optional. Indicates whether to enable the health check function.

 Valid values: **on | off**

 |
|HealthCheckConnectPort|Integer|No|8080|Optional. The port used for health checks.

 Value range:**1 to 65535**

 |
|HealthCheckDomain|String|No|$\_ip|Optional. The domain name used for health checks. Valid values:

 -   **$\_ip**: the private IP address of the backend server. When the IP address is specified or this parameter is not specified, SLB uses private IP addresses of backend servers as the domain names for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|Optional. The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by using commas \(,\).

 Valid values: **http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 |
|HealthCheckInterval|Integer|No|5|Optional. The time interval between two consecutive health checks.

 Value range:**1 to 50**. Unit: seconds

 |
|HealthCheckTimeout|Integer|No|3|Optional. The amount of time to wait for the response from the health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckTimeout** is smaller than that of **HealthCheckInterval**, the parameter **HealthCheckTimeout** is invalid, and the timeout is set to the value of **HealthCheckInterval**.

 |
|HealthCheckURI|String|No|/test/index.html|Optional. The URI used for health checks.

 |
|HealthyThreshold|Integer|No|4|Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(from **failure** to **success**\).

 Value range: **2 to 10**

 |
|IdleTimeout|Integer|No|23|Optioinal. The idle connection timeout in seconds. Value range: 1 to 60. Default value: 15.

 If no request is received during the specified timeout period, SLB will temporarily terminate the connection and restart the connection when the next request is received.

 |
|RequestTimeout|Integer|No|223|Optional. The request timeout. Value range: 1 to 180. Default value: 60. Unit: seconds.

 If no response is received from the backend server during the specified timeout period, SLB will stop waiting and send an HTTP 504 error to the client.

 |
|Scheduler|String|No|wrr|Optional. The algorithm used to distribute traffic. Valid values:

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight will receive more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 |
|ServerCertificateId|String|No|idkp-123-cn-test-01|Optional. The ID of the server certificate.

 |
|StickySession|String|No|on|Optional. Indicates whether to enable session persistence. Valid values: **on | off**

 |
|StickySessionType|String|No|on|Optional. The method used to handle the cookie. Valid values:

 -   **insert**: Insert a cookie.

SLB adds a cookie to the first response from the backend server \(that is, it inserts SERVERID in the HTTP/HTTPS response packet\). Then, the next request will contain the cookie and the listener will distribute the request to the same backend server.

-   **server**: Rewrite the cookie.

SLB will overwrite the original cookie when a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the previously recorded backend server.


 **Note:** If the value of **StickySession** is **on**, this parameter is required.

 |
|TLSCipherPolicy|String|No|tls\_cipher\_policy\_1\_2|You can only specify the TLSCipherPolicy parameter for guaranteed-performance instances. Each security policy includes the TLS protocol versions that can be selected by HTTPS and the supported cipher suites.

 Currently, the following four security policies are supported:

 -   **tls\_cipher\_policy\_1\_0**:
    -   Supported TLS versions: TLSv1.0, TLSv1.1, and TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_1**:
    -   Supported TLS versions: TLSv1.1 and TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_2** 
    -   Supported TLS version: TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_2\_strict** 
    -   Supported TLS version: TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA.

 |
|UnhealthyThreshold|Integer|No|4|Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from **success** to **failure**\).

 Value range:**2 to 10**

 |
|VServerGroup|String|No|on|Optional. Indicates whether to use a VServer group. Valid values: **on | off**

 |
|VServerGroupId|String|No|rsp-cige6j5e7p|Optional. The ID of the VServer group.

 |
|XForwardedFor|String|No|on|Optional. Indicates whether to use the X-Forwarded-For header field to obtain the real IP address of a client.

 Valid values: **on | off**

 |
|XForwardedFor\_SLBID|String|No|on|Optional. Indicates whether to use the `SLB-ID` header field to obtain the SLB instance ID.

 Valid value: **on | off**. Default value: off

 |
|XForwardedFor\_SLBIP|String|No|on|Optional. Indicates whether to use the `SLB-IP` header field to obtain the real IP address of a client request.

 Valid values:**on | off**. Default value: off

 |
|XForwardedFor\_proto|String|No|on|Optional. Indicates whether to use the `X-Forwarded-Proto` header field to obtain the listening protocol used by the SLB instance.

 Valid values:**on | off**. Default value: off

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerHTTPSListenerAttribute
&ListenerPort=80 
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerHTTPSListenerAttributeResponse> 
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId> 
</SetLoadBalancerHTTPSListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

## Additional instructions {#docSupplement .section}

Hahaha

|Tables

|Are

|Cool

|
|--------|-----|------|
|col 3 is

|aligned

|$1600

|
|col 2 is

|centered

|$12

|
|zebra stripes

|are neat

|$1

|

