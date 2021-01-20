# CreateLoadBalancerHTTPListener

调用CreateLoadBalancerHTTPListener创建HTTP监听。

**说明：** 新建的监听的状态为**stopped**。创建完成后，调用[StartLoadBalancerListener](~~27597~~)接口启动监听来转发流量。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerHTTPListener&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoadBalancerHTTPListener|要执行的操作。

 取值：**CreateLoadBalancerHTTPListener**。 |
|HealthCheck|String|是|on|是否开启健康检查。取值：

 -   **on**：开启健康检查。
-   **off**：不开启健康检查。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1**~**65535**。 |
|LoadBalancerId|String|是|lb-bp1c9vixxjh92q83tw\*\*\*\*\*|负载均衡实例ID。 |
|StickySession|String|是|off|是否开启会话保持。取值：

 -   **on**：开启会话保持。
-   **off**：不开启会话保持。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|Bandwidth|Integer|否|-1|监听的带宽峰值，取值：

 -   **-1**：不限制带宽峰值。
-   **1~5120**：监听的带宽峰值，所有监听的带宽峰值之和不能超过实例的带宽峰值。

 **说明：** 该参数只适用于中国内地。 |
|BackendServerPort|Integer|否|80|负载均衡实例后端使用的端口。

 取值：**1~65535**。

 **说明：** 如果不使用服务器组（不指定VServerGroupId参数），则该参数必选。 |
|XForwardedFor|String|否|on|是否开启通过`X-Forwarded-For`头字段获取来访者真实 IP。

 取值：**on**或**off**（默认值）。 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|StickySessionType|String|否|insert|Cookie处理方式。取值：

 -   **insert**：植入Cookie。

客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP或HTTPS响应报文中插入ServerId），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。

-   **server**：重写Cookie。

负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。

**说明：** 当**StickySession**值为**on**时，必须指定该参数。 |
|CookieTimeout|Integer|否|500|Cookie超时时间。

 取值：**1~86400**秒。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**insert**时，该参数必选。 |
|Cookie|String|否|B490B5EBF6F3CD402E515D22BCDA1598|服务器上配置的Cookie。

 长度为1~200个字符，只能包含ASCII英文字母和数字字符，不能包含逗号（,）、分号（；）或空格，也不能以美元符号（$）开头。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**server**时，该参数必选。 |
|HealthCheckDomain|String|否|172.16.\*\*.\*\*|用于健康检查的域名，取值：

 -   **$\_ip**： 后端服务器的私网IP。当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   **domain**：域名长度为1~80字符，只能包含字母、数字、半角句号（.）和短划线（-）。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthCheckURI|String|否|/test/index.html|用于健康检查的URL。

 长度限制为1~80个字符，只能使用字母、数字和短划线（-）、正斜线（/）、半角句号（.）、百分号（%）、问号（?）、井号（\#）和and（&amp;）这些字符。 URL不能只为正斜线（/），但必须以正斜线（/）开头。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**失败**判定为**成功**。

 取值：**2~10**。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**成功**判定为**失败**。

 取值：**2~10**。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthCheckTimeout|Integer|否|3|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。在**HealthCheck**值为**on**时才会有效。

 取值：**1~300**秒。

 **说明：** 如果**HealthCHeckTimeout**的值小于**HealthCheckInterval**的值，则**HealthCHeckTimeout**无效，超时时间为**HealthCheckInterval**的值。 |
|HealthCheckConnectPort|Integer|否|80|健康检查的后端服务器的端口。

 取值： **1~65535**。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthCheckInterval|Integer|否|5|健康检查的时间间隔。

 取值： **1~50**秒。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthCheckHttpCode|String|否|http\_2xx|健康检查正常的HTTP状态码，多个状态码用逗号分隔。

 默认值为**http\_2xx**。

 取值：**http\_2xx**、**http\_3xx**、**http\_4xx**或**http\_5xx**。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|VServerGroupId|String|否|rsp-cige6j\*\*\*\*\*|虚拟服务器组ID。 |
|XForwardedFor\_SLBIP|String|否|on|是否通过`SLB-IP`头字段获取客户端请求的真实IP。

 取值：**on**或**off**（默认值）。 |
|XForwardedFor\_SLBID|String|否|on|是否通过`SLB-ID`头字段获取负载均衡实例ID。

 取值：**on**或**off**（默认值）。 |
|XForwardedFor\_proto|String|否|on|是否通过`X-Forwarded-Proto`头字段获取负载均衡实例的监听协议。

 取值：**on**或**off**（默认值）。 |
|Gzip|String|否|on|是否开启Gzip压缩，对特定文件类型进行压缩。默认值为**on**。

 取值：**on**或**off**（默认值）。 |
|AclId|String|否|123|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclType|String|否|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数有效。 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on**或**off**（默认值）。 |
|Description|String|否|监听说明|设置监听的描述信息。

 长度限制为1~80个字符，允许包含中文、字母、数字、短划线（-）、正斜线（/）、半角句号（.）和下划线（\_）等字符。 |
|ListenerForward|String|否|off|是否开启HTTP至HTTPS的转发。

 取值：**on**或**off**（默认值）。 |
|ForwardPort|Integer|否|443|HTTP至HTTPS的监听转发端口。 |
|IdleTimeout|Integer|否|3|指定连接空闲超时时间，取值范围为**1**~**60**秒，默认值为**15**秒。

 在超时时间内一直没有访问请求，负载均衡会暂时中断当前连接，直到一下次请求来临时重新建立新的连接。 |
|RequestTimeout|Integer|否|6|指定请求超时时间，取值范围为**1**~**180**秒，默认值为**60**秒。

 在超时时间内后端服务器一直没有响应，负载均衡将放弃等待，给客户端返回`HTTP 504`错误码。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateLoadBalancerHTTPListener
&HealthCheck=off
&ListenerPort=80
&LoadBalancerId=lb-bp1c9vixxjh92q83tw*****
&StickySession=off
&BackendServerPort=80
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<CreateLoadBalancerHTTPListenerResponse>
	  <RequestId>1FF504CB-BFFF-4508-A51A-58A416604FC8</RequestId>
</CreateLoadBalancerHTTPListenerResponse>
```

`JSON`格式

```
{
    "RequestId": "1FF504CB-BFFF-4508-A51A-58A416604FC8"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

