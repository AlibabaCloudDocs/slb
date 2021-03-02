# DescribeRules

Queries the forwarding rules that are configured for a specified listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeRules&type=RPC&version=2014-05-15)

## Request Parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeRules|The operation that you want to perform.

 Set the value to **DescribeRules**. |
|ListenerPort|Integer|Yes|90|The frontend listener port that is used by the Server Load Balancer \(SLB\) instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1ca0zt07t934\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is deployed.

 You can call the [DescribeRegions](~~27584~~) operation to query region IDs. |
|ListenerProtocol|String|No|https|The frontend listener protocol that is used by the SLB instance.

 **Note:** This parameter is required when listeners that use different protocols listen on the same port. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |
|Rules|Array of Rule| |The list of forwarding rules. |
|Rule| | | |
|RuleId|String|rule-tybqi6\*\*\*\*\*\*|The ID of the forwarding rule. |
|RuleName|String|Rule2|The name of the forwarding rule. The name must be 1 to 80 characters in length, and can contain only letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).

 **Note:** The name of each forwarding rule must be unique within a listener. |
|Domain|String|test.com|The requested domain name specified in the forwarding rule. |
|Url|String|/cache|The requested URL specified in the forwarding rule. |
|VServerGroupId|String|rsp-6cejjzl\*\*\*\*\*\*|The ID of the destination vServer group specified in the forwarding rule. |
|Cookie|String|23|The cookie that is configured on the backend server.

 The value must be 1 to 200 characters in length, and can contain only ASCII letters and digits. It cannot contain commas \(,\), semicolons \(;\), or spaces. The value cannot start with a dollar sign \($\).

 **Note:** If you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **server**, this parameter is required. |
|CookieTimeout|Integer|56|The timeout period of a cookie. Valid values: **1 to 86400**. Unit: seconds.

 **Note:** If you set the **StickySession** parameter to **on** and the **StickySessionType** parameter to **insert**, this parameter is required. |
|HealthCheck|String|off|Indicates whether health checks are enabled.

 Valid values: **on** and **off**.

 **Note:** If you set the **ListenerSync** parameter to **off**, this parameter is required. If you set the parameter to **on**, the configuration of the listener is used. |
|HealthCheckConnectPort|Integer|45|The port of the backend server that is used for health check.

 Valid values: **1 to 65535**.

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. If you left this parameter empty and the **HealthCheck** parameter is set to **on**, the backend port configuration of the listener is used by default. |
|HealthCheckDomain|String|www.domain.com|The domain name that is used for health checks. Valid values:

 -   **$\_ip**: The private IP address of the backend server.

If you do not set this parameter or set the parameter to $\_ip, the SLB instance uses the private IP address of each backend server as the domain name for health checks.

-   **domain**: The domain name must be 1 to 80 characters in length. The domain name can contain only letters, digits, periods \(.\), and hyphens \(-\).

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|HealthCheckHttpCode|String|http\_3xx|The HTTP status code that indicates a successful health check. Multiple HTTP status codes are separated by commas \(,\). Default value: **http\_2xx**.

 Valid values: **http\_2xx**, **http\_3xx**, **http\_4xx**, and **http\_5xx**.

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|HealthCheckInterval|Integer|5|The interval between two consecutive health checks.

 Valid values: **1 to 50**. Unit: seconds.

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|HealthCheckTimeout|Integer|34|The timeout period for a health check response. If a backend ECS instance does not return an expected response within the specified period of time, the backend server is declared unhealthy.

 Valid values: **1 to 300**. Unit: seconds.

 **Note:** If the value of the **HealthCHeckTimeout** parameter is smaller than that of the **HealthCheckInterval** parameter, the value of the **HealthCHeckTimeout** parameter is ignored and the value of the **HealthCheckInterval** parameter is regarded as the waiting period. If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|HealthCheckURI|String|/example|The URL that is used for health checks.

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|HealthyThreshold|Integer|5|Indicates the number of times that an unhealthy backend server must consecutively pass health checks before it is declared healthy \(from **fail** to **success**\).

 Valid values: **2 to 10**.

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |
|ListenerSync|String|off|Indicates whether the forwarding rule uses the scheduling algorithm, session persistence, and health check configurations of the listener.

 Valid values: **on** and **off**.

 -   **off**: does not use the configurations of the listener. You can customize health check and session persistence configurations for the forwarding rule.
-   **on**: uses the configurations of the listener. |
|Scheduler|String|wrr|The scheduling algorithm. Valid values:

 -   **wrr** \(default\): Backend servers that have higher weights receive more requests than backend servers that have lower weights.
-   **wlc**: Requests are distributed based on the weights of backend servers together with the number of connections to backend servers. If two backend servers have the same weight, the backend server that has fewer connections receives more requests.
-   **rr**: Requests are distributed to backend servers in sequence.

 **Note:** If you set the **ListenerSync** parameter to **off**, this parameter is required. If you set the parameter to **on**, the configuration of the listener is used. |
|StickySession|String|off|Indicates whether session persistence is enabled.

 Valid values: **on** and **off**.

 **Note:** If you set the **ListenerSync** parameter to **off**, this parameter is required. If you set the parameter to **on**, the configuration of the listener is used. |
|StickySessionType|String|insert|The method that is used to handle a cookie. Valid values:

 -   **insert**: inserts a cookie into the response. SLB inserts a cookie \(SERVERID\) into the first HTTP or HTTPS response packet that is sent to a client. The next request from the client contains this cookie and the listener distributes this request to the recorded backend server.
-   **server**: rewrites the original cookie. When SLB detects a user-defined cookie, SLB overwrites the original cookie with the user-defined cookie. The next request from the client contains the user-defined cookie, and the listener distributes the request to the recorded backend server.

 **Note:** If you set the **StickySession** parameter to **on**, this parameter is required. |
|UnhealthyThreshold|Integer|2|The number of consecutive health check failures required before a backend server is declared unhealthy \(from **success** to **fail**.

 Valid values: **2 to 10**

 **Note:** If you set the **HealthCheck** parameter to **on**, this parameter is required. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeRules
&ListenerPort=90
&LoadBalancerId=lb-bp1ca0zt07t93******
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeRulesResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <Rules>
        <Rule>
              <Cookie>23</Cookie>
              <CookieTimeout>56</CookieTimeout>
              <VServerGroupId>rsp-6cejjzl******</VServerGroupId>
              <HealthCheckInterval>5</HealthCheckInterval>
              <UnhealthyThreshold>2</UnhealthyThreshold>
              <HealthCheckURI>/example</HealthCheckURI>
              <Scheduler>wrr</Scheduler>
              <RuleId>rule-tybqi6******</RuleId>
              <HealthCheck>off</HealthCheck>
              <HealthCheckTimeout>34</HealthCheckTimeout>
              <Url>/cache</Url>
              <StickySession>off</StickySession>
              <HealthCheckConnectPort>45</HealthCheckConnectPort>
              <HealthyThreshold>5</HealthyThreshold>
              <HealthCheckDomain>www.domain.com</HealthCheckDomain>
              <ListenerSync>off</ListenerSync>
              <StickySessionType>insert</StickySessionType>
              <Domain>test.com</Domain>
              <HealthCheckHttpCode>http_3xx</HealthCheckHttpCode>
              <RuleName>Rule2</RuleName>
        </Rule>
  </Rules>
</DescribeRulesResponse>
```

`JSON` format

```
{"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C","Rules":{"Rule":[{"Cookie":"23","CookieTimeout":"56","VServerGroupId":"rsp-6cejjzl******","HealthCheckInterval":"5","UnhealthyThreshold":"2","HealthCheckURI":"/example","Scheduler":"wrr","RuleId":"rule-tybqi6******","HealthCheck":"off","HealthCheckTimeout":"34","Url":"/cache","StickySession":"off","HealthCheckConnectPort":"45","HealthyThreshold":"5","HealthCheckDomain":"www.domain.com","ListenerSync":"off","StickySessionType":"insert","Domain":"test.com","HealthCheckHttpCode":"http_3xx","RuleName":"Rule2"}]}}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

