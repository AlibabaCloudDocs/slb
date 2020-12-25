# CreateLoadBalancerHTTPListener

Creates an HTTP listener.

Newly created listeners are in the **Stopped** state.

After a listener is created, you must call the [StartLoadBalancerListener](~~27597~~) operation to enable the listener to forward traffic.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerHTTPListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoadBalancerHTTPListener|The operation that you want to perform.

Set the value to **CreateLoadBalancerHTTPListener**. |
|HealthCheck|String|Yes|on|Specifies whether to enable health checks.

Valid values: **on and off**. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the SLB instance.

Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1c9vixxjh92q83tw\*\*\*\*\*|The ID of the SLB instance. |
|StickySession|String|Yes|off|Specifies whether to enable session persistence.

Valid values: **on and off**. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is created.

You can query the region ID from the [Regions and zones](~~40654~~) list or by calling the [DescribeRegions](~~27584~~) operation. |
|Bandwidth|Integer|No|-1|The maximum bandwidth of the listener. Unit: Mbit/s. Valid values:

-   **-1**: specifies that the maximum bandwidth is not limited.
-   **1 to 5120**: the maximum bandwidth of the listener. The sum of maximum bandwidth values of all listeners cannot exceed the maximum bandwidth of the SLB instance.

**Note:** This parameter applies to only mainland China. |
|BackendServerPort|Integer|No|80|The backend port that is used by the SLB instance.

Valid values: **1 to 65535**.

**Note:** If the VServerGroupId parameter is not set, this parameter is required. |
|XForwardedFor|String|No|on|Specifies whether to use the X-Forwarded-For header to obtain the real IP address of the client.

Set the value to **on**. |
|Scheduler|String|No|wrr|The scheduling algorithm. Valid values:

-   **wrr**: Backend servers that have higher weights receive more requests than those that have lower weights. This is the default value.
-   **wlc**: Requests are distributed based on the combination of weights and connections to backend servers. If two backend servers have the same weight, the backend server that has fewer connections receives more requests.
-   **rr**: Requests are distributed to backend servers in sequence. |
|StickySessionType|String|No|insert|The method that is used to handle the cookie. Valid values:

-   **insert**: insets a cookie.

SLB inserts a cookie \(SERVERID\) into the first HTTP or HTTPS response packet that is sent to a client. The next request from the client will contain this cookie, and the listener will distribute this request to the recorded backend server.

-   **server**: rewrites a cookie.

When SLB detects a user-defined cookie, it overwrites the original cookie with the user-defined cookie. The next request from the client will contain the user-defined cookie, and the listener will distribute the request to the recorded backend server.

**Note:** If you set the **StickySession** parameter to **on**, you must specify a value for this parameter. |
|CookieTimeout|Integer|No|500|The timeout period of a cookie.

Valid values: **1 to 86400**. Unit: seconds.

**Note:** If you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **insert**, this parameter is required. |
|Cookie|String|No|B490B5EBF6F3CD402E515D22BCDA1598|The cookie to be configured on the backend server.

The name must be 1 to 200 characters in length, and can contain only ASCII letters and digits. It cannot contain commas \(,\), semicolons \(;\), or spaces. It cannot start with a dollar sign \($\).

**Note:** If you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **server**, this parameter is required. |
|HealthCheckDomain|String|No|172.16.\*\*. \*\*|The domain name that is used for health check. Valid values:

-   **$\_ip**: The private IP address of the backend server. If you do not set this parameter or set the parameter to $\_ip, the SLB instance uses the private IP address of each backend server as the domain name for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length. It can contain only letters, digits, periods \(.\), and hyphens \(-\).

**Note:** This parameter takes effect only when the **HealthCheck** parameter is set to **on**. |
|HealthCheckURI|String|No|/test/index.html|The URI that is used for health checks.

The URI must be 1 to 80 characters in length and can contain only letters, digits, and special characters. %? Supported special characters are " - / . % \# &. The URL must start with a forward slash \(/\) and must not contain only a forward slash.

**Note:** This parameter takes effect only when the **HealthCheck** parameter is set to **on**. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before a backend server is declared healthy \(from **fail** to **success**\).

Valid values: **2 to 10**.

**Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|UnhealthyThreshold|Integer|No|4|TThe number of consecutive failed health checks that must occur before a backend server is declared unhealthy. \(from **success** to **fail**\).

Valid values: **2 to 10**.

**Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckTimeout|Integer|No|3|The time period to wait for a health check response. If a backend server does not respond within the specified time period, the health check fails. This parameter only takes effect when the **HealthCheck** parameter is set to **on**.

Valid values: **1 to 300**.

**Note:** If the value of the **HealthCHeckTimeout** parameter is smaller than that of the **HealthCheckInterval** parameter, the value of the **HealthCHeckTimeout** parameter is ignored and the value of the **HealthCheckInterval** parameter is regarded as the waiting period. |
|HealthCheckConnectPort|Integer|No|80|The port of the backend server that is used for health check.

Valid values: **1 to 65535**.

**Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckInterval|Integer|No|5|The interval between two consecutive health checks.

Valid values: **1 to 50**. Unit: seconds.

**Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|The HTTP status code that indicates a successful health check. Separate multiple HTTP status codes with commas \(,\).

Default value: **http\_2xx**.

Valid values: **http\_2xx, http\_3xx, http\_4xx, and http\_5xx**.

**Note:** This parameter only takes effect when the **HealthCheck** parameter is set to **on**. |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*\*|The ID of the VServer group. |
|XForwardedFor\_SLBIP|String|No|on|Specifies whether to use the `SLB-IP` header to obtain the real IP address of the client.

Valid values: **on and off**. Default value: off. |
|XForwardedFor\_SLBID|String|No|on|Specifies whether to use the `SLB-ID` header to obtain the ID of the SLB instance.

Valid values: **on and off**. Default value: off. |
|XForwardedFor\_proto|String|No|on|Specifies whether to use the `X-Forwarded-Proto` header to obtain the listener protocol of the SLB instance.

Valid values: **on and off**. Default value: off. |
|Gzip|String|No|on|Specifies whether to enable Gzip compression to compress files of a specific type. Default value: **on**.

Valid values: **on and off**. |
|AclId|String|No|123|The ID of the Access Control List \(ACL\) to which the listener is bound.

This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|white|The type of ACL. Valid values: white and black.

-   **white**: specifies the ACL as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

Risks may arise if you specify an ACL as a whitelist.

The whitelist allows only network traffic from the IP addresses in the specified ACL to access the SLB listener.

If a whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

-   **black**: specifies the ACL as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If the blacklist is enabled but the corresponding ACL does not contain any IP addresses, the SLB listener forwards all requests.


This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable the access control feature.

Valid values: **on and off**. Default value: off. |
|Description|String|No|Listener description|The description of the listener.

It must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |
|ListenerForward|String|No|off|Specifies whether to enable the HTTP-to-HTTPS redirection.

Valid values: **on and off**. |
|ForwardPort|Integer|No|443|The listening port that is used to redirect HTTP requests to HTTPS. |
|IdleTimeout|Integer|No|3|The timeout period of an idle connection. Unit: seconds. Valid values: 1 to 60. Default value: 15.

If no request is received during the specified timeout period, the SLB instance closes the connection. When another request is received, the SLB instance establishes a new connection. |
|RequestTimeout|Integer|No|6|The timeout period of a request. Unit: seconds. Valid values: 1 to 180. Default value: 60.

If no response is received from the backend server within the specified timeout period, SLB sends an `HTTP 504` error to the client. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=CreateLoadBalancerHTTPListener
&HealthCheck=off
&ListenerPort=80
&LoadBalancerId=lb-bp1c9vixxjh92q83tw*****
&StickySession=off
&BackendServerPort=80
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoadBalancerHTTPListenerResponse>
      <RequestId>1FF504CB-BFFF-4508-A51A-58A416604FC8</RequestId>
</CreateLoadBalancerHTTPListenerResponse>
```

`JSON` format

```
{
    "RequestId": "1FF504CB-BFFF-4508-A51A-58A416604FC8"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

