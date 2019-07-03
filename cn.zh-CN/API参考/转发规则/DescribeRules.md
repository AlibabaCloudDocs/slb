# DescribeRules {#doc_api_Slb_DescribeRules .reference}

调用DescribeRules查询指定监听已配置的转发规则。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeRules)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRules|要执行的操作。

 取值：**DescribeRules**。

 |
|ListenerPort|Integer|是|90|负载均衡实例前端使用的监听端口。

 取值范围：**1~65535**。

 |
|LoadBalancerId|String|是|lb-bp1ca0zt07t934wxezyxo|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |
|Rules| | |转发规则列表。

 |
|└RuleId|String|rule-tybqi6qkp8|转发规则ID。

 |
|└RuleName|String|Rule2|转发规则名称，长度限制为1~80，只能使用字母、数字、‘-’、‘/’、‘.’、‘\_’这些字符。

 **说明：** 同一个监听内不同规则的名称必须唯一。

 |
|└Domain|String|test.com|转发规则绑定的请求域名。

 |
|└Url|String|/cache|转发规则绑定的请求路径。

 |
|└VServerGroupId|String|rsp-6cejjzlld7|转发规则绑定的目标虚拟服务器组ID。

 |
|└Cookie|String|23|服务器上配置的Cookie。

 长度为1-200个字符，只能包含ASCII英文字母和数字字符，不能包含逗号、分号或空格，也不能以$开头。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**server**时，该参数必选且有效。

 |
|└CookieTimeout|Integer|56|Cookie超时时间。取值：**1-86400**（秒）

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**insert**时，该参数有效。

 |
|└HealthCheck|String|off|是否开启健康检查。

 取值：**on | off**

 **说明：** **ListenerSync**为**off**时有效，为**on**时表明与监听配置一致。

 |
|└HealthCheckConnectPort|Integer|45|健康检查的后端服务器的端口。

 取值：**1-65535**

 **说明：** **HealthCheck**为**on**时该参数有效，若为空且**HealthCheck**为**on**表明默认使用监听后端端口配置。

 |
|└HealthCheckDomain|String|domain|用于健康检查的域名，取值：

 -   **$\_ip**： 后端服务器的私网IP。

当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。

-   **domain**：域名长度为1-80字符，只能包含字母、数字、点号（.）和连字符（-）。

 **说明：** **HealthCheck**为**on**时，该参数有效

 |
|└HealthCheckHttpCode|String|http\_3xx|健康检查正常的HTTP状态码，多个状态码用逗号分隔。默认值为**http\_2xx**。

 取值：**http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|└HealthCheckInterval|Integer|5|健康检查的时间间隔。

 取值：**1-50**（秒）

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|└HealthCheckTimeout|Integer|34|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）

 **说明：** 如果**HealthCHeckTimeout**的值小于**HealthCheckInterval**的值，则**HealthCHeckTimeout**无效，超时时间为**HealthCheckInterval**的值。**HealthCheck**为**on**时，该参数有效。

 |
|└HealthCheckURI|String|/example|用于健康检查的URI。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|└HealthyThreshold|Integer|5|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|└ListenerSync|String|off|转发规则是否从监听上继承健康检查、会话保持和调度算法配置。

 取值：**on | off**

 -   **off**：不继承监听配置，转发规则自定义健康检查及会话保持配置。
-   **on**：继承监听配置。

 |
|└Scheduler|String|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。

 **说明：** **ListenerSync**为**off**时有效，为**on**时表明与监听配置一致。

 |
|└StickySession|String|off|是否开启会话保持。

 取值：**on | off**

 **说明：** 在**ListenerSync**为**off**时有效，为**on**时表明与监听配置一致。

 |
|└StickySessionType|String|insert|cookie的处理方式。取值：

 -   **insert**：植入Cookie。客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP/HTTPS响应报文中插入SERVERID），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。
-   **server**：重写Cookie。 负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。

 **说明：** 当**StickySession**的值为**on**时，该参数有效。

 |
|└UnhealthyThreshold|Integer|2|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeRules
&ListenerPort=90
&LoadBalancerId=lb-bp1ca0zt07t934wxezyxo
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

