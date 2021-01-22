# DescribeLoadBalancerHTTPListenerAttribute

调用DescribeLoadBalancerHTTPListenerAttribute查询HTTP监听配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPListenerAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerHTTPListenerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerHTTPListenerAttribute**。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1~65535**。 |
|LoadBalancerId|String|是|lb-bp1o94dp5\*\*\*\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。 |
|Bandwidth|Integer|-1|监听的带宽峰值。 |
|Status|String|stopped|当前监听的状态。

 取值：**running\|stopped**。

 -   **running**：表示监听正常运行。
-   **stopped**：表示监听停止。 |
|XForwardedFor|String|on|是否开启通过X-Forwarded-For的方式获取来访者真实IP。

 取值：**on \| off**。 |
|Scheduler|String|wrr|调度算法。

 取值：**wrr \| wlc \| rr**。

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|StickySession|String|on|是否开启会话保持。

 取值：**on \| off**（默认值）。 |
|StickySessionType|String|insert|

 Cookie的处理方式。

 取值：**insert \| server。**

 -   insert：植入Cookie。

客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP/HTTPS响应报文中插入SERVERID），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。

-   server：重写Cookie。

负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。


 **说明：** 当**StickySession**的值为**on**时，必须指定该参数。 |
|CookieTimeout|Integer|500|cookie超时时间。 |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|服务器上配置的cookie。 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on \| off**。 |
|HealthCheckDomain|String|www.domain.com|用于健康检查的域名。 |
|HealthCheckURI|String|/test/index.html|用于健康检查的URI。

 长度限制为1~80，只能使用字母、数字和短横线（-）、正斜杠（/）、点号（.）、百分号（%），问号（？）、井号（\#）和&amp;这些字符。 URL不能只为正斜杠（/），但必须以正斜杠（/）开头。 |
|HealthyThreshold|Integer|4|健康检查阈值。 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。 |
|HealthCheckTimeout|Integer|3|每次健康检查响应的最大超时间，单位为秒。 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，单位为秒。 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|健康检查正常的HTTP状态码。 |
|HealthCheckConnectPort|Integer|8080|健康检查的端口。

 **说明：** 当**HealthCheck**值为**on**时才会有效。 |
|VServerGroupId|String|rsp-cige6j\*\*\*\*|绑定的服务器组ID。 |
|Gzip|String|on|是否开启Gzip压缩，对特定文件类型进行压缩。

 取值：**on \| off**。 |
|AclId|String|on|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclStatus|String|off|是否开启访问控制功能。

 取值：**on \| off**（默认值）。 |
|AclType|String|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。 |
|BackendServerPort|Integer|80|负载均衡实例后端使用的端口。 |
|Description|String|test|HTTP监听描述。 |
|ForwardPort|Integer|80|HTTP至HTTPS的监听转发端口。

 **说明：** 如果**ListenerForward**的值为**off**，该参数不显示。 |
|IdleTimeout|Integer|2|指定连接空闲超时时间，取值范围为1-60秒，默认值为15秒。

 在超时时间内一直没有访问请求，负载均衡会暂时中断当前连接，直到下一次请求来临时重新建立新的连接。 |
|ListenerForward|String|on|表示是否开启HTTP至HTTPS的监听转发。

 -   **on**：表示开启。
-   **off**：表示未开启。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|RequestTimeout|Integer|34|指定请求超时时间，取值范围为1~180秒，默认值为60秒。

 在超时时间内后端服务器一直没有响应，负载均衡将放弃等待，给客户端返回HTTP 504错误码。 |
|Rules|Array| |转发规则描述。 |
|Rule| | | |
|Domain|String|www.example.com|域名。 |
|RuleId|String|1234|转发规则ID。 |
|RuleName|String|test|转发规则名称。 |
|Url|String|/example|访问路径。 |
|VServerGroupId|String|123|转发规则的目标服务器组ID。 |
|SecurityStatus|String|on|安全状态。

 取值：**on\|off**。 |
|XForwardedFor\_SLBID|String|on|是否通过`SLB-ID`头字段获取负载均衡实例ID。 |
|XForwardedFor\_SLBIP|String|on|是否通过SLB-IP头字段获取客户端请求的真实IP。 |
|XForwardedFor\_proto|String|on|是否通过X-Forwarded-Proto头字段获取负载均衡实例的监听协议。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancerHTTPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1o94dp5*********
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeLoadBalancerHTTPListenerAttributeResponse>
    <ForwardPort>443</ForwardPort>
    <ListenerPort>80</ListenerPort>
    <Status>stopped</Status>
    <RequestId>99439CEF-192C-4B01-A45A-2D5BD5BCDA62</RequestId>
    <ListenerForward>on</ListenerForward>
</DescribeLoadBalancerHTTPListenerAttributeResponse>
```

`JSON` 格式

```
{
    "ForwardPort": 443, 
    "ListenerPort": 80, 
    "Status": "stopped", 
    "RequestId": "99439CEF-192C-4B01-A45A-2D5BD5BCDA62", 
    "ListenerForward": "on"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

