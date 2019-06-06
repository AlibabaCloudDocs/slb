# DescribeRules {#doc_api_Slb_DescribeRules .reference}

Queries the forwarding rules that have been configured for a specified listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeRules) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeRules|The name of this action. Value: **DescribeRules**

 |
|ListenerPort|Integer|Yes|90|The frontend listener port used by the SLB instance. Value range: 1 to 65535

 |
|LoadBalancerId|String|Yes|lb-bp1ca0zt07t934wxezyxo|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|Request ID.

 |
|Rules| | |A list of forwarding rules.

 |
|└RuleId|String|rule-tybqi6qkp8|The ID of the forwarding rule.

 |
|└RuleName|String|Rule2|The name must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).

 **Note:** In a listener, the name of each rule must be unique.

 |
|└Domain|String|test.com|The request domain name associated with the forwarding rule.

 |
|└Url|String|/cache|The request path associated with the forwarding rule.

 |
|└VServerGroupId|String|rsp-6cejjzlld7|The ID of the destination VServer group associated with the forwarding rule.

 |
|└Cookie|String|23|The Cookie configured on the server.

 The cookie must be a string of 1 to 200 characters and can only contain ASCII letters and numbers. It cannot contain commas \(,\), semicolons \(;\), or spaces, and it cannot start with a dollar sign \($\).

 **Note:** This parameter is required and takes effect only when **StickySession** is set to **on** and **StickySessionType** is set to **server**.

 |
|└CookieTimeout|Integer|56|The cookie expiration period. Value range:**1 to 86400**. Unit: seconds

 **Note:** This parameter takes effect when **StickySession** is set to **on** and **StickySessionType** is set to **insert**.

 |
|└HealthCheck|String|off|Indicates whether to enable the health check function.

 Valid values: **on | off**

 **Note:** This parameter takes effect when **ListenerSync** is set to **off**. Listener settings prevail when this parameter is set to **on**.

 |
|└HealthCheckConnectPort|Integer|45|The port of the backend server used for health checks.

 Value range: **1 to 65535**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**. By default, backend listener settings prevail if this parameter retains empty and **HealthCheck** is set to **on**.

 |
|└HealthCheckDomain|String|domain|The domain name used for health checks. Valid values:

 -   **$\_ip**: private IP address of the backend server.

If the IP address is specified or this parameter is not specified, SLB uses the private IP addresses of backend servers as the domain names for health checks.

-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└HealthCheckHttpCode|String|http\_3xx|The HTTP status code indicating that the health check is normal. Separate multiple status codes by using commas \(,\). Default value: **http\_2xx**

 Valid values: **http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└HealthCheckInterval|Integer|5|The time interval between two consecutive health checks.

 Value range: **1 to 50**. Unit: seconds

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└HealthCheckTimeout|Integer|34|The amount of time to wait for the response from the health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range: **1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckTimeout** is smaller than that of **HealthCheckInterval**, the parameter **HealthCheckTimeout** is invalid, and the timeout is set to the value of **HealthCheckInterval**. This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└HealthCheckURI|String|/example|The URI used for health checks.

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└HealthyThreshold|Integer|5|The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to **success**\).

 Value range:**2 to 10**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |
|└ListenerSync|String|off|Indicates whether a forwarding rule inherits the settings of health checks, session persistence, and scheduling algorithm from a listener.

 Valid values: **on | off**

 -   **off**: The rule customs health check and session persistence settings instead of inheriting them from the listener.
-   **on**: The rule inherits the settings from the listener.

 |
|└Scheduler|String|wrr|The algorithm used to distribute traffic. Valid values:

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A backend server with a higher weight will receive more requests. When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 **Note:** This parameter takes effect when **ListenerSync** is set to **off**. Listener settings prevail when this parameter is set to **on**.

 |
|└StickySession|String|off|Indicates whether to enable session persistence.

 Valid values: **on | off**.

 **Note:** This parameter takes effect when **ListenerSync** is set to **off**. Listener settings prevail when this parameter is set to **on**.

 |
|└StickySessionType|String|insert|The method used to handle the Cookie. Valid values:

 -   **insert**: Insert the Cookie. SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP/HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.
-   **server**: Rewrite the Cookie. SLB will overwrite the original cookie when a new cookie is set. The next time the client carries the new cookie to access the SLB instance, the listener will distribute the request to the previously recorded backend server.

 **Note:** This parameter takes effect when **StickySession** is set to **on**.

 |
|└UnhealthyThreshold|Integer|2|The number of consecutive failures of health checks on the same ECS instance before a backend server is declared as unhealthy \(from **success** to **failure**\).

 Value range:**2 to 10**

 **Note:** This parameter takes effect when **HealthCheck** is set to **on**.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeRules
&ListenerPort=90 
&LoadBalancerId=lb-bp1ca0zt07t934wxezyxo 
&RegionId=cn-hangzhou 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeRulesResponse> 
  <RequestId>11D87D83-741B-4F8A-8AAD-FD6867FDE7B2</RequestId> 
  <Rules> 
    <Rule> 
      <Url>/image</Url> 
      <Domain>example.com</Domain> 
      <VServerGroupId>rsp-bp114nimo4kl9</VServerGroupId> 
      <RuleId>rule-bp1supbxos2u3</RuleId> 
      <RuleName>auto_named_rule</RuleName> 
      <ListenerSync>on</ListenerSync> 
    </Rule> 
    <Rule> 
      <Domain>test.com</Domain> 
      <VServerGroupId>rsp-bp114nimo4kl9</VServerGroupId> 
      <RuleId>rule-bp1efemp9suk5</RuleId> 
      <RuleName>Rule2</RuleName> 
      <ListenerSync>on</ListenerSync> 
    </Rule> 
    <Rule> 
      <Domain>test2.com</Domain> 
      <VServerGroupId>rsp-bp114nimo4kl9</VServerGroupId> 
      <RuleId>rule-bp12jzy0hvio3</RuleId> 
      <RuleName>Rule3</RuleName> 
      <ListenerSync>on</ListenerSync> 
    </Rule> 
  </Rules> 
</DescribeRulesResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"11D87D83-741B-4F8A-8AAD-FD6867FDE7B2",
	"Rules":{
		"Rule":[
			{
				"Domain":"example.com",
				"Url":"/image",
				"RuleId":"rule-bp1supbxos2u3",
				"VServerGroupId":"rsp-bp114nimo4kl9",
				"RuleName":"auto_named_rule",
				"ListenerSync":"on"
			},
			{
				"Domain":"test.com",
				"RuleId":"rule-bp1efemp9suk5",
				"VServerGroupId":"rsp-bp114nimo4kl9",
				"RuleName":"Rule2",
				"ListenerSync":"on"
			},
			{
				"Domain":"test2.com",
				"RuleId":"rule-bp12jzy0hvio3",
				"VServerGroupId":"rsp-bp114nimo4kl9",
				"RuleName":"Rule3",
				"ListenerSync":"on"
			}
		]
	}
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

