# DescribeRuleAttribute {#doc_api_Slb_DescribeRuleAttribute .reference}

Queries the settings of a forwarding rule.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeRuleAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeRuleAttribute| The name of this action.

 Value: **DescribeRuleAttribute**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|RuleId|String|Yes|rule-bp1efemp9suk5| The ID of the forwarding rule.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RuleName|String|Rule1| The name of the forwarding rule.

 |
|LoadBalancerId|String|lb-bp1ca0zt07t934wxezyxo| The ID of the SLB instance.

 |
|ListenerPort|String|90| The frontend listener port used by the SLB instance.

 |
|Domain|String|test.com| The domain name of the forwarding rule.

 |
|Url|String|/cache| The forwarding rule path.

 |
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group associated with the forwarding rule.

 |
|Cookie|String|wwe| The cookie configured on the backend server.

 The cookie must be 1 to 200 characters in length and can only contain ASCII English letters and numbers. It cannot contain commas \(,\), semicolons \(;\), or spaces, nor can it begin with $.

 This parameter is required and takes effect only when **StickySession** is set to **on** and **StickySessionType** is set to **server**.

 |
|CookieTimeout|Integer|12| Timeout period of the cookie.

 Value range:**1 to 86400**. Unit: seconds

 **Note:** This parameter is required and takes effect only when **StickySession** is set to **on** and **StickySessionType** is set to **insert**.

 |
|HealthCheck|String|off| Indicates whether to enable the health check function.

 Valid values:**on | off**

 **Note:** This parameter takes effect when **ListenerSync** is set to **off**. Listener settings prevail when this parameter is set to **on**.

 |
|HealthCheckConnectPort|Integer|23| The port of the backend server used for health checks.

 Value range:**1 to 65535**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**. By default, backend listener settings prevail if this parameter retains empty and **HealthCheck** is set to **on**.

 |
|HealthCheckDomain|String|www.example.com| The domain name used for health checks. Valid values:

 -   **$\_ip**: the private IP address of the backend server. If the IP address is specified or this parameter is not specified, SLB uses the private IP addresses of backend servers as the domain names for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|HealthCheckHttpCode|String|http\_3xx| The HTTP status code indicating that the health check is normal. Separate multiple status codes by using commas \(,\). Default value:**http\_2xx**

 Valid values:**http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|HealthCheckInterval|Integer|34| The time interval between two consecutive health checks.

 Value range:**1 to 50**. Unit: seconds

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|HealthCheckTimeout|Integer|34| The length of time to wait for the response from a health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckTimeout** is smaller than that of **HealthCheckInterval**, the parameter **HealthCheckTimeout** is invalid, and the timeout is set to the value of **HealthCheckInterval**. This parameter takes effect when **HealthCheck** is set to **on**.

 |
|HealthCheckURI|String|10.21.22.1| The URI used for health checks.

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|HealthyThreshold|Integer|2| The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to**success**\).

 Value range:**2 to 10**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|ListenerSync|String|off| Indicates whether a forwarding rule inherits the settings of health checks, session persistence, and scheduling algorithm from a listener.

 Valid values:**on | off**

 -   **off**: The rule customs health check and session persistence settings instead of inheriting them from the listener.
-   **on**: The rule inherits the settings from the listener.

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |
|RuleId|String|rule-hfgnd\*\*\*\*\*| The ID of the forwarding rule.

 |
|Scheduler|String|wrr| The algorithm used to distribute traffic. Value values:

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight receives more requests.

When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.

-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 **Note:** This parameter takes effect when **ListenerSync** is set to **off**. Listener settings prevail when this parameter is set to **on**.

 |
|StickySession|String|off| Indicates whether to enable session persistence.

 Valid values:**on | off**

 **Note:** This parameter is required and takes effect when **ListenerSync** is set to **off**. Listener settings take precedence when this parameter is set to **on**.

 |
|StickySessionType|String|insert| The method used to handle the cookie. Valid values:

 -   **insert**: Insert the cookie. SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP and HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.
-   **server**: Rewrite the Cookie. SLB will overwrite the original cookie when a new cookie is set. The next time the client carries the new cookie to access the SLB instance, the listener will distribute the request to the previously recorded backend server.

 **Note:** This parameter takes effect when **StickySession** is set to **on**.

 |
|UnhealthyThreshold|Integer|3| The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success** to**failure**\).

 Value range: **2 to 10**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeRuleAttribute
&RegionId=cn-hangzhou
&RuleId=rule-bp1efemp9suk5
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeRuleAttributeResponse>
  <Domain>test.com</Domain>
  <VServerGroupId>rsp-bp114nimo4kl9</VServerGroupId>
  <LoadBalancerId>lb-bp1ca0zt07t934wxezyxo</LoadBalancerId>
  <RuleName>Rule2</RuleName>
  <ListenerPort>90</ListenerPort>
  <RequestId>DB3C28EE-9A6C-4FFA-8759-4ED8346A675E</RequestId>
  <ListenerSync>on</ListenerSync>
</DescribeRuleAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"Domain":"test.com",
	"RequestId":"DB3C28EE-9A6C-4FFA-8759-4ED8346A675E",
	"VServerGroupId":"rsp-bp114nimo4kl9",
	"LoadBalancerId":"lb-bp1ca0zt07t934wxezyxo",
	"RuleName":"Rule2",
	"ListenerSync":"on",
	"ListenerPort":90
}
```

## Error codes {#section_7fb_b56_yee .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

