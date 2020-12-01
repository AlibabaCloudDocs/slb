# SetRule

Modifies the forwarding rule of a specified vServer group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetRule&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetRule|The operation that you want to perform.

 Set the value to **SetRule**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is created.

 You can call the [DescribeRegions](~~27584~~) operation to query region IDs. |
|RuleId|String|Yes|rule-3ejhkt\*\*\*\*\*\*|The ID of the forwarding rule. |
|VServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the vServer group with which the forwarding rule is associated. |
|RuleName|String|No|doctest|The name of the forwarding rule must be 1 to 80 characters in length. It can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).

 **Note:** Forwarding rule names must be unique within each listener. |
|ListenerSync|String|No|off|Specifies whether the forwarding rule uses the scheduling algorithm, session persistence, and health check configurations of the listener.

 Valid values: **on and off**.

 -   **off**: does not use the configurations of the listener. You can customize the health check and session persistence configurations for the forwarding rule.
-   **on**: uses the configurations of the listener. |
|Scheduler|String|No|wrr|This parameter is required and effective only when you specify **off** for **ListenerSync**.

 The scheduling algorithm. Valid values:

 -   **wrr**: A backend server with a higher weight is expected to receive more requests. This is the default value.
-   **wlc**: Requests are forwarded based on the weight and load \(the number of connections\) of each backend server. If two backend servers have the same weight, the system forwards more requests to the backend server with fewer connections.
-   **rr**: Requests are distributed to each backend server on a rotation. |
|StickySession|String|No|off|This parameter is required and effective only when you specify **off** for **ListenerSync**.

 Specifies whether to enable session persistence. Valid values: **on and off**. |
|StickySessionType|String|No|insert|Specifies whether to insert or rewrite the cookie. This parameter is required and effective when you specify **on** for **StickySession**.

 Valid values:

 -   insert: inserts a cookie.

The SLB instance inserts a cookie \(SERVERID\) into the first HTTP or HTTPS response packet that is sent to a client. The next request from the client contains this cookie. Then, the listener distributes this request to the recorded backend server.

-   server: rewrites a cookie.

When the SLB instance detects a user-defined cookie, it rewrites the original cookie with the user-defined cookie. The next request from the client contains the user-defined cookie, and the listener distributes the request to the recorded backend server. |
|CookieTimeout|Integer|No|123|The timeout period of a cookie.

 Valid values: **1 to 86400** Unit: seconds.

 Only when you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **insert**, this parameter is required and effective. |
|Cookie|String|No|23ffsa|The cookie configured on the backend server.

 The cookie must be 1 to 200 characters in length and can contain only ASCII letters and digits. It cannot contain commas \(,\), semicolons \(;\), or spaces. It cannot start with a dollar sign \($\).

 Only when you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **server**, this parameter is required and effective. |
|HealthCheck|String|No|off|Specifies whether to enable health checks.

 Valid values: **on and off**.

 **Note:** This parameter is required and effective only when you set **ListenerSync** to **off**. |
|HealthCheckDomain|String|No|www.domain.com|The domain name that is used for health checks. Valid values:

 -   **$\_ip**: The private IP address of the backend server. If the $\_ip parameter is specified or the HealthCheckDomain parameter is not specified, the SLB instance uses the private IP addresses of backend servers as the domain names for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length and can contain only letters, digits, periods \(.\), and hyphens \(-\).

 **Note:** This parameter is required and effective only when you set **HealthCheck** to **on**. |
|HealthCheckURI|String|No|/example|This parameter is required and effective only when you set **HealthCheck** to **on**. |
|HealthyThreshold|Integer|No|4|The number of consecutive health check successes required before a backend server is declared healthy \(from **fail** to **success**\).

 This parameter is required and effective only when you set **HealthCheck** to **on**.

 Valid values: **2 to 10**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive health check failures required before a backend server is declared unhealthy \(from **success** to **fail**\).

 This parameter is required and effective only when you set **HealthCheck** to **on**.

 Valid values: **2 to 10**. |
|HealthCheckTimeout|Integer|No|20|Specify the amount of time to wait for a health check response. If the backend Elastic Compute Service \(ECS\) instance does not send an expected response within the specified period of time, the health check fails.

 **Note:** This parameter is required and effective only when you set **HealthCheck** to **on**.

 Valid values: **1 to 300**. Unit: seconds. |
|HealthCheckInterval|Integer|No|20|The interval between two consecutive health checks.

 This parameter is required only when you set **HealthCheck** to **on**.

 Valid values: **1 to 50** .

 **Note:** This parameter is required and effective only when you set **HealthCheck** to **on**. |
|HealthCheckHttpCode|String|No|http\_2xx|The HTTP status code that specifies a successful health check. Separate multiple HTTP status codes with commas \(,\).

 This parameter is required only when you set **HealthCheck** to **on**.

 Valid values: **http\_2xx** \(default value\), **http\_3xx, http\_4xx, and http\_5xx**.

 **Note:** This parameter is effective only when you set **HealthCheck** to **on**. |
|HealthCheckConnectPort|Integer|No|80|The port number used for health checks.

 Valid values: **1 to 65535**.

 **Note:** This parameter is effective only when you set **HealthCheck** to **on**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=SetRule
&RegionId=cn-hangzhou
&RuleId=rule-3ejhkt******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetRuleResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</SetRuleResponse>
```

`JSON` format

```
{
"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

