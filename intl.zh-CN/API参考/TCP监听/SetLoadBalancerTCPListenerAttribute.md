# SetLoadBalancerTCPListenerAttribute {#doc_api_Slb_SetLoadBalancerTCPListenerAttribute .reference}

调用SetLoadBalancerTCPListenerAttribute修改TCP监听的配置。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerTCPListenerAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerTCPListenerAttribute|要执行的操作。

 取值：**SetLoadBalancerTCPListenerAttribute**。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp1ygod3yctvg1y7wezms|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|AclId|String|否|12333|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on | off**。

 |
|AclType|String|否|white|访问控制类型：

 -   **white**：仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发请求。

-   **black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|Bandwidth|Integer|否|43|监听的带宽峰值。取值：**-1 | 1-5120**。

 -   **-1**：对于按流量计费的公网负载均衡实例，可以将带宽峰值设置为**-1**，即不限制带宽峰值。
-   **1-5120Mbps**：对于按带宽计费的公网负载均衡实例，可以设置每个监听的带宽峰值，但所有监听的带宽峰值之和不能超过实例的带宽峰值。详情参见[共享实例带宽](~~57846~~)。

 |
|Description|String|否|test|TCP监听描述。

 |
|EstablishedTimeout|Integer|否|500|连接超时时间。

 取值：**10-900**（秒）。

 |
|HealthCheckConnectPort|Integer|否|8080|健康检查使用的端口。取值：**1-65535**。

 不设置此参数时，表示使用后端服务端口（**BackendServerPort**）。

 |
|HealthCheckConnectTimeout|Integer|否|100|接收来自运行状况检查的响应需要等待的时间。

 如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）。

 **说明：** 如果**HealthCheckConnectTimeout**的值小于**HealthCheckInterval**的值，则**HCTimeout**无效，超时时间为**HealthCheckInterval**的值。

 |
|HealthCheckDomain|String|否|$\_ip|用于健康检查的域名。当TCP监听需要使用HTTP健康检查时可配置此参数，如不配置则按TCP健康检查。

 -   **$\_ip**：后端服务器的私网IP。

当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。

-   **domain**：域名长度为1~80，只能包含字母、数字、点号（.）和连字符（-）。

 |
|HealthCheckHttpCode|String|否|http\_2xx,http\_3xx|健康检查正常的HTTP状态码，多个状态码用逗号（,）分割。

 取值：**http\_2xx | http\_3xx | http\_4xx | http\_5xx**。

 |
|HealthCheckInterval|Integer|否|5|健康检查的时间间隔。取值：**1-50**（秒）。

 |
|HealthCheckType|String|否|tcp|健康检查类型。

 取值：**tcp | http**。

 |
|HealthCheckURI|String|否|/test/index.html|用于健康检查的URI。

 当TCP监听需要使用HTTP健康检查时，可配置此参数。

 如不配置，则按TCP健康检查。

 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**。

 |
|MasterSlaveServerGroup|String|否|on|是否使用主备服务器组。

 取值：**on | off**。

 **VserverGroup**和**MasterSlaveServerGroup**只允许一个值为**on**。

 |
|MasterSlaveServerGroupId|String|否|rsp-cige\*\*\*\*\*\*|主备服务器组ID。

 **说明：** 服务器组ID和主备服务器组ID只能选择一个。

 |
|PersistenceTimeout|Integer|否|0|会话保持的超时时间。取值：**0-3600**（秒）。

 默认值：**0**，表示关闭会话保持。

 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。
-   **sch**：基于源IP地址的一致性hash，相同的源地址会调度到相同的后端服务器。
-   **tch**：基于四元组的一致性hash（源IP+目的IP+源端口+目的端口），相同的流会调度到相同的后端服务器。

 **说明：** 仅有性能保障型实例支持sch和tch一致性hash算法。

 |
|SynProxy|String|否|enable|是否开启SynProxy，SynProxy是负载均衡的攻击防护功能。

 建议用户一般情况下不要调整这个参数，由负载均衡控制。

 取值：**enable | disable**。

 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**。

 |
|VServerGroup|String|否|on|是否使用虚拟服务器组。

 取值：**on | off**。

 **VserverGroup**和**MasterSlaveServerGroup**只允许一个值为**on**。

 |
|VServerGroupId|String|否|rsp-cige6j5\*\*\*\*\*|虚拟服务器组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetLoadBalancerTCPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y7wezms
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerTCPListenerAttributeResponse>
  <RequestId>59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1</RequestId>
</SetLoadBalancerTCPListenerAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

