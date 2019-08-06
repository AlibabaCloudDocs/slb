# SetRule {#doc_api_Slb_SetRule .reference}

Changes the destination VServer group of a forwarding rule.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetRule) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetRule| The name of this action.

 Value: **SetRule**

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|RuleId|String|Yes|rule-3ejhktkaeu| The ID of the forwarding rule.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the destination VServer group of the forwarding rule.

 |
|Cookie|String|No|23ffsa| Optional. The cookie configured on the backend server.

 The cookie must be 1 to 200 characters in length and can only contain ASCII English letters and numbers. It cannot contain commas \(,\), semicolons \(;\), or spaces, nor can it begin with $.

 This parameter is required and takes effect only when **StickySession** is set to **on** and **StickySessionType** is set to **server**.

 |
|CookieTimeout|Integer|No|123| Optional. The timeout period of the cookie.

 Value range:**1 to 86400**. Unit: seconds

 This parameter is required and takes effect only when **StickySession** is set to **on** and **StickySessionType** is set to **insert**.

 |
|HealthCheck|String|No|off| Optional. Indicates whether to enable the health check function.

 Valid values:**on | off**

 **Note:** This parameter is required and takes effect only when **ListenerSync** is set to **off**.

 |
|HealthCheckConnectPort|Integer|No|80| Optional. The port used for health checks.

 Value range:**1 to 65535**

 **Note:** This parameter takes effect only when **HealthCheck** is set to **on**.

 |
|HealthCheckDomain|String|No|domain| Optional. The domain name used for health checks. Valid values:

 -   **$\_ip**: the private IP address of the backend server. If $\_ip is specified or HealthCheckDomain is not specified, SLB uses the private IP addresses of backend servers as the domain names for health checks.
-   **domain**: domain name, which must be 1 to 80 characters in length and can contain letters, numbers, periods \(.\), and hyphens \(-\).

 **Note:** This parameters takes effect only when **HealthCheck** is set to **on**.

 |
|HealthCheckHttpCode|String|No|http\_2xx| Optional. The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by using commas \(,\).

 This parameter is required when **HealthCheck** is set to **on**.

 Valid values: **http\_2xx****| http\_3xx | http\_4xx | http\_5xx**. Default value: http\_2xx

 **Note:** This parameter takes effect only when **HealthCheck** is set to **on**.

 |
|HealthCheckInterval|Integer|No|20| Optional. The time interval between two consecutive health checks.

 This parameter is required when **HealthCheck** is set to **on**.

 Value range:**1 to 50**. Unit: seconds

 **Note:** This parameter takes effect only when **HealthCheck** is set to **on**.

 |
|HealthCheckTimeout|Integer|No|20| Optional. The length of time to wait for the response from the health check. If the backend ECS does not send a response within the specified time, the health check fails.

 **Note:** This parameter is required and takes effect only when **HealthCheck** is set to **on**.

 Value range:**1 to 300**. Unit: seconds

 |
|HealthCheckURI|String|No|/example| Optional. The URI used for health checks. This parameter is required and takes effect only when **HealthCheck** is set to **on**.

 |
|HealthyThreshold|Integer|No|12| Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to**success**\).

 This parameter is required and takes effect only when **HealthCheck** is set to **on**.

 Value range:**2 to 10**.

 |
|ListenerSync|String|No|off| Optional. Indicates whether a forwarding rule inherits the settings of health checks, session persistence, and scheduling algorithm from a listener.

 Valid values:**on | off**

 -   **off**: The rule customs health check and session persistence settings instead of inheriting them from the listener.
-   **on**: The rule inherits the settings from the listener.

 |
|RuleName|String|No|doctest| Optional. The name of the forwarding rule. The name must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).

 **Note:** In a listener, the name of each rule must be unique.

 |
|Scheduler|String|No|wrr| This parameter is required and takes effect only when **ListenerSync** is set to **off**.

 Optional. The scheduling algorithm. Valid values:

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight receives more requests. When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 |
|StickySession|String|No|off| This parameter is required and takes effect only when**ListenerSync** is set to **off**.

 Optional. Indicates whether to enable session persistence. Valid values: **on | off**.

 |
|StickySessionType|String|No|insert| Optional. The method used to handle the cookie. This parameter is required and takes effect only when **StickySession** is set to **on**.

 Valid values:

 -   insert: Insert the cookie.

SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP/HTTPS response packet\). The next request contains the cookie and the listener distributes the request to the same backend server.

-   server: Rewrite the cookie.

SLB overwrites the original cookie when a new cookie is set. The next time the client carries the new cookie to access SLB, the listener distributes the request to the previously recorded backend server.


 |
|UnhealthyThreshold|Integer|No|1| Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success**to**failure**\).

 This parameter is required and takes effect only when **HealthCheck** is set to **on**.

 Value range:**2 to 10**.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetRule
&RegionId=cn-hangzhou
&RuleId=rule-3ejhktkaeu
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetRuleResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</SetRuleResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Error codes {#section_k99_z7r_ik4 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

