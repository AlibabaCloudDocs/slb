# DescribeRuleAttribute {#doc_api_Slb_DescribeRuleAttribute .reference}

调用DescribeRuleAttribute查询指定转发规则的配置详情。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeRuleAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeRuleAttribute|要执行的操作。

 取值：**DescribeRuleAttribute**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|RuleId|String|是|rule-bp1efemp9suk5|转发规则ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RuleName|String|Rule1|转发规则名称。

 |
|LoadBalancerId|String|lb-bp1ca0zt07t934wxezyxo|负载均衡实例ID。

 |
|ListenerPort|String|90|负载均衡实例前端使用的监听端口。

 |
|Domain|String|test.com|转发规则域名。

 |
|Url|String|/cache|转发规则路径。

 |
|VServerGroupId|String|rsp-cige6j5e7p|转发规则关联的服务器组ID。

 |
|Cookie|String|wwe|服务器上配置的Cookie。

 长度为1-200个字符，只能包含ASCII英文字母和数字字符，不能包含逗号、分号或空格，也不能以$开头。

 当**StickySession**为**on**且**StickySessionType**为**server**时，该参数必选且有效。

 |
|CookieTimeout|Integer|12|Cookie超时时间。

 取值：**1-86400**（秒）。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**insert**时，该参数必选且有效。

 |
|HealthCheck|String|off|是否开启健康检查。

 取值：**on | off**。

 **说明：** **ListenerSync**为**off**时有效，为**on**时表明与监听配置一致。

 |
|HealthCheckConnectPort|Integer|23|健康检查的后端服务器的端口。

 取值：**1-65535**。

 **说明：** **HealthCheck**为**on**时该参数有效，若为空且**HealthCheck**为**on**，表明默认使用监听后端端口配置。

 |
|HealthCheckDomain|String|www.example.com|用于健康检查的域名，取值：

 -   **$\_ip**： 后端服务器的私网IP。当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   **domain**：域名长度为1-80字符，只能包含字母、数字、点号（.）和连字符（-）。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|HealthCheckHttpCode|String|http\_3xx|健康检查正常的HTTP状态码，多个状态码用逗号分隔。默认值为**http\_2xx**。

 取值：**http\_2xx | http\_3xx | http\_4xx | http\_5xx**。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|HealthCheckInterval|Integer|34|健康检查的时间间隔。

 取值：**1-50**（秒）。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|HealthCheckTimeout|Integer|34|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）。

 **说明：** 如果**HealthCHeckTimeout**的值小于**HealthCheckInterval**的值，则**HealthCHeckTimeout**无效，超时时间为**HealthCheckInterval**的值。**HealthCheck**为**on**时，该参数有效。

 |
|HealthCheckURI|String|10.21.22.1|用于健康检查的URI。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|HealthyThreshold|Integer|2|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**。

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |
|ListenerSync|String|off|转发规则是否从监听上继承健康检查、会话保持和调度算法配置。

 取值：**on | off**。

 -   **off**：不继承监听配置，转发规则自定义健康检查及会话保持配置。
-   **on**：继承监听配置。

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |
|RuleId|String|rule-hfgnd\*\*\*\*\*|转发规则ID。

 |
|Scheduler|String|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。

当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。

-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。

 **说明：** **ListenerSync**为**off**时有效，为**on**时表明与监听配置一致。

 |
|StickySession|String|off|是否开启会话保持。

 取值：**on | off**。

 **说明：** 在**ListenerSync**为**off**时必选且有效，为**on**时表明与监听配置一致。

 |
|StickySessionType|String|insert|cookie的处理方式。取值：

 -   **insert**：植入Cookie。客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP/HTTPS响应报文中插入SERVERID），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。
-   **server**：重写Cookie。负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。

 **说明：** 当**StickySession**的值为**on**时，该参数有效。

 |
|UnhealthyThreshold|Integer|3|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**

 **说明：** **HealthCheck**为**on**时，该参数有效。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeRuleAttribute
&RegionId=cn-hangzhou
&RuleId=rule-bp1efemp9suk5
&<公共请求参数>

```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

