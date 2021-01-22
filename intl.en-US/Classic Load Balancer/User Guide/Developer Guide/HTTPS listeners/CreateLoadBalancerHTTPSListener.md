# CreateLoadBalancerHTTPSListener

You can also call this operation to create an HTTPS listener.

**Note:** The newly created listener is in the Stopped state. After the listener is created, you must call the [StartLoadBalancerListener](~~27597~~) operation to enable the listener to forward traffic.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerHTTPSListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoadBalancerHTTPSListener|The operation that you want to perform.

 Set the value to **CreateLoadBalancerHTTPSListener**. |
|Bandwidth|Integer|Yes|-1|The peak bandwidth of the listener. Unit: Mbit/s.

 Valid values: **-1 or 1 to 5120**.

 -   **-1**: For a pay-by-traffic Internet-facing SLB instance, you can set the peak bandwidth to **-1**. This indicates that the peak bandwidth is not limited.
-   **1 to 5120**: For a pay-by-bandwidth Internet-facing SLB instance, you can specify the peak bandwidth for each listener. The sum of peak bandwidth values for all listeners cannot exceed the peak bandwidth of the SLB instance. |
|HealthCheck|String|Yes|on|Specifies whether to enable health check.

 Valid values: **on and off**. |
|ListenerPort|Integer|Yes|80|The listener port of the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earr\*\*\*\*\*|The ID of the SLB instance. |
|ServerCertificateId|String|Yes|idkp-123-cn-test-01\*\*|The ID of the server certificate. |
|StickySession|String|Yes|on|Specifies whether to enable session persistence.

 Valid values: **on and off**. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is deployed.

 You can retrieve the region ID from the [Regions and zones](~~40654~~) list or by calling the [DescribeRegions](~~25609~~) operation. |
|BackendServerPort|Integer|No|80|The backend port used by the SLB instance. Valid values: **1 to 65535**.

 If the VServerGroupId parameter is not specified, you must specify a value for this parameter. |
|XForwardedFor|String|No|on|Specifies whether to use`X-Forwarded-For` to obtain the real IP address of the client.

 Set the value to: **on**. |
|Scheduler|String|No|wrr|The scheduling algorithm. Default value: wrr. Valid values:

 -   **wrr**: A backend server with a higher weight is expected to receive more requests.
-   **wlc**: Requests are distributed based on the weight and load \(the number of connections\) of each backend server. If two backend servers have the same weight, the backend server with fewer connections is expected to receive more requests.
-   **rr**: Requests are distributed to each backend server on a rotation. |
|StickySessionType|String|No|insert|The method used to handle a cookie. If you set the StickySession parameter to **on**, you must specify this parameter.

 Valid values: **insert and server**.

 -   **insert**: Inserts a cookie.

SLB inserts a cookie \(SERVERID\) to the first HTTP or HTTPS response packet sent to a client. The next request from the client will contain the cookie, and the listener will deliver the request to the backend server with the specified SERVERID.

-   **server**: Rewrites a cookie.

When SLB detects a user-defined cookie, it overwrites the original cookie with the user-defined cookie. The next request from the client will contain the user-defined cookie, and the listener will distribute the request to the recorded backend server. |
|CookieTimeout|Integer|No|500|The cookie timeout period. Unit: seconds.

 Valid values: **1 to 86400**.

 **Note:** If you set the **StickySession** parameter to**on**and the **StickySessionType** parameter to **insert**, you must specify this parameter. |
|Cookie|String|No|B490B5EBF6F3CD402E515D22BCDA1598|The cookie configured on the backend server.

 The cookie must be 1 to 200 characters in length and can contain ASCII letters and digits. It cannot contain commas \(,\), semicolons \(;\), or spaces. It cannot start with a dollar sign \($\).

 **Note:** If you set the **StickySession** parameter to**on**and the **StickySessionType** parameter to **server**, you must specify this parameter. |
|HealthCheckDomain|String|No|172.16.\*. \*\*|The domain name used for health check. Valid values:

 -   **$\_ip**: The private IP address of the backend server. If the $\_ip parameter is specified or the HealthCheckDomain parameter is not specified, SLB uses the private IP addresses of backend servers as the domain names for health check.
-   **domain**: The domain name must be 1 to 80 characters in length. It can contain only letters, digits, periods \(.\), and hyphens \(-\).

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckURI|String|No|/test/index.html|The URI used for health check.

 The URL must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\). The URL must start with a forward slash \(/\).

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthyThreshold|Integer|No|4|The number of consecutive health check successes required before a backend server is declared healthy \(from **fail** to **success**\).

 Valid values: **2 to 10**.

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive health check failures required before a backend server is declared unhealthy \(from **success** to **fail**\).

 Valid values: **2 to 10**.

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckTimeout|Integer|No|3|The response timeout period. Unit: seconds. If the backend ECS instance does not send an expected response within the specified period of time, the health check fails. This parameter only takes effect when the **HealthCheck** parameter is set to **on**.

 Valid values: **1 to 300**.

 **Note:**

-   If the value of the **HealthCheckTimeout** parameter is smaller than that of the **HealthCheckInterval** parameter, the value of the **HealthCheckTimeout** parameter is ignored and the value of the **HealthCheckInterval** parameter is regarded as the timeout period.
-   This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckConnectPort|Integer|No|8080|The port number used for health check.

 Valid values: **1 to 65535**.

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckInterval|Integer|No|5|The time interval between two consecutive health checks. Unit: seconds.

 Valid values: **1 to 50** .

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|The HTTP status code indicating that a health check is successful. Separate multiple HTTP status codes with commas \(,\). Default value: **http\_2xx**.

 Valid values: **http\_2xx, http\_3xx, http\_4xx, and http\_5xx**.

 **Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|VServerGroupId|String|No|rsp-cige6j5e7p\*\*\*\*\*|The ID of the VServer group. |
|CACertificateId| String|No|139a00604ad-cn-east-hangzh\*\*\*\*\*|The ID of the CA certificate.

 If both the CA certificate and the server certificate are uploaded, two-way authentication is used.

 If you upload only the server certificate, one-way authentication is used. |
|XForwardedFor\_SLBIP|String|No|on|Specifies whether to use the SLB-IP header to obtain the real IP address of the client. Default value: off.

 Valid values: **on and off**. |
|XForwardedFor\_SLBID|String|No|on|Specifies whether to use the SLB-ID header to obtain the ID of the SLB instance.

 Valid values: **on and off**. |
|XForwardedFor\_proto|String|No|on|Specifies whether to use the X-Forwarded-Proto header to obtain the listener protocol of the SLB instance. Default value: off.

 Valid values: **on and off**. |
|Gzip|String|No|on|Specifies whether to enable Gzip compression to compress files of a specific type. Default value: on.

 Valid values: **on**and **off**. |
|AclId|String|No|123|The ID of the Access Control List \(ACL\) to which the listener is bound.

 **Note:** This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|white|The type of the ACL. Valid values: white and black.

 -   **white**: Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. The whitelist is used to allow only specified IP addresses to access an application.

Enabling the whitelist may pose risks to your workloads.

After the whitelist is enabled, only the IP addresses in the ACL can access the SLB listener.

If a whitelist is enabled and no IP address is specified, the SLB listener does not forward any requests.

-   **black**: All requests from the IP addresses or CIDR blocks in the ACL are denied. The blacklist is used to forbid specified IP addresses from accessing an application.

 If a blacklist is enabled and no IP address is specified, the SLB listener forwards all requests.

 **Note:** This parameter is required when the**AclStatus parameter** is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable access control for the listener. Default value: off.

 Valid values: **on and off**. |
|Description|String|No|Create a listener|The description of the listener.

 It must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |
|IdleTimeout|Integer|No|12|The timeout period of an idle connection. Valid values: 1 to 60. Default value: 15. Unit: seconds.

 If no request is received during the specified timeout period, SLB closes the connection and starts a new connection when the next request comes. |
|RequestTimeout|Integer|No|23|The timeout period of a request. Valid values: 1 to 180. Unit: seconds. Default value: 60.

 If no response is received from the backend server within the specified timeout period, SLB will send an HTTP 504 error to the client. |
|EnableHttp2|String|No|off|Specifies whether to enable HTTP/2. Default value: on.

 Valid values: **on** and **off**. |
|TLSCipherPolicy|String|No|tls\_cipher\_policy\_1\_1|You can specify the TLSCipherPolicy parameter only for a guaranteed-performance instance. Each security policy includes TLS protocol versions and cipher suites available for HTTPS.

 Currently, the following four security policies are supported. For more information, see the description of differences in TLS security policies.

 -   **tls\_cipher\_policy\_1\_0**:
    -   Supported TLS versions: TLSv1.0, TLSv1.1, and TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_1**:
    -   Supported TLS versions: TLSv1.1 and TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_2**
    -   Supported TLS version: TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.
-   **tls\_cipher\_policy\_1\_2\_strict**
    -   Supported TLS version: TLSv1.2.
    -   Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? &Action=CreateLoadBalancerHTTPSListener
&Bandwidth=-1
&HealthCheck=on
&ListenerPort=80
&LoadBalancerId=lb-bp1o94dp5i6earr*****
&ServerCertificateId=idkp-123-cn-test-01
&StickySession=on
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoadBalancerHTTPSListenerResponse>
	  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</CreateLoadBalancerHTTPSListenerResponse>
```

`JSON` format

```
"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
		}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

