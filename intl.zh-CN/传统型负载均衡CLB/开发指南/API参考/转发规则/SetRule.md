# SetRule

调用SetRule修改目标虚拟服务器组的转发规则。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetRule&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetRule|要执行的操作。

 取值：**SetRule**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|RuleId|String|是|rule-3ejhkt\*\*\*\*\*\*|转发规则ID。 |
|VServerGroupId|String|是|rsp-cige6\*\*\*\*\*\*|转发规则的目标服务器组ID。 |
|RuleName|String|否|doctest|转发规则名称，长度限制为1~80个字符，支持字母、数字、短划线（-）、正斜线（/）、英文句点（.）和下划线（\_）这些字符。

 **说明：** 同一个监听内不同规则的名称必须唯一。 |
|ListenerSync|String|否|off|是否继承监听的健康检查、会话保持和调度算法配置。

 取值：**on**或**off**。

 -   **off**：不继承监听配置。转发规则自定义健康检查及会话保持配置。
-   **on**：继承监听配置。 |
|Scheduler|String|否|wrr|在**ListenerSync**为**off**时必选且有效，其他情况忽略此参数。

 调度算法，取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|StickySession|String|否|off|在**ListenerSync**为**off**时必选且有效，其他情况会忽略此参数。

 是否开启会话保持，取值：**on**或**off**。

 -   **on**：开启。
-   **off**：不开启。 |
|StickySessionType|String|否|insert|Cookie的处理方式，**StickySession**为**on**时必选且有效，其他情况会忽略此参数。

 取值：

 -   **insert**：植入Cookie。

客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP或HTTPS响应报文中插入ServerId），下次客户端携带此Cookie访问时，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。

-   **server**：重写Cookie。

负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问时，负载均衡服务会将请求定向转发给之前记录到的后端服务器。 |
|CookieTimeout|Integer|否|123|Cookie超时时间。

 取值：**1**~**86400**秒。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**insert**时必选且有效，其他情况会忽略此参数。 |
|Cookie|String|否|23ffsa|服务器上配置的Cookie。

 长度为1~200个字符，只能包含ASCII英文字母和数字字符，不能包含逗号（,）、分号（;）或空格，也不能以美元符号（$）开头。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**server**时必选且有效，其他情况会忽略此参数。 |
|HealthCheck|String|否|off|是否开启健康检查。

 取值：**on**或**off**。

 **说明：** **ListenerSync**为**off**时必选且有效，其他情况会忽略此参数。 |
|HealthCheckDomain|String|否|www.domain.com|用于健康检查的域名，取值：

 -   **$\_ip**： 后端服务器的私网IP。当指定了$\_ip或HealthCheckDomain未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   **domain**：域名长度为1~80字符，只能包含字母、数字、英文句点（.）和短划线（-）。

 **说明：** **HealthCheck**为**on**时有效，其他情况会忽略此参数。 |
|HealthCheckURI|String|否|/example|用于健康检查的URL。**HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**失败**判定为**成功**。

 取值：**2**~**10**。

 **说明：** **HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**成功**判定为**失败**。

 取值：**2**~**10**。

 **说明：** **HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|HealthCheckTimeout|Integer|否|20|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1**~**300**秒。

 **说明：** **HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|HealthCheckInterval|Integer|否|20|健康检查的时间间隔。

 取值：**1**~**50**秒。

 **说明：** **HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|HealthCheckHttpCode|String|否|http\_2xx|健康检查正常的HTTP状态码，多个状态码用逗号（,）分割。

 取值：**http\_2xx**（默认值）、**http\_3xx**、**http\_4xx**或**http\_5xx**。

 **说明：** **HealthCheck**为**on**时必选且有效，其他情况会忽略此参数。 |
|HealthCheckConnectPort|Integer|否|80|健康检查使用的端口。

 取值：**1**~**65535**。

 **说明：** **HealthCheck**为**on**时有效，其他情况会忽略此参数。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetRule
&RegionId=cn-hangzhou
&RuleId=rule-3ejhkt******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetRuleResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</SetRuleResponse>
```

`JSON` 格式

```
{
"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

