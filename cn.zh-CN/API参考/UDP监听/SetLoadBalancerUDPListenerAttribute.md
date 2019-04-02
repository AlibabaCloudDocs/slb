# SetLoadBalancerUDPListenerAttribute {#doc_api_Slb_SetLoadBalancerUDPListenerAttribute .reference}

使用SetLoadBalancerUDPListenerAttribute修改UDP协议监听的配置。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerUDPListenerAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerUDPListenerAttribute|要执行的操作。取值：**SetLoadBalancerUDPListenerAttribute**

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**

 |
|LoadBalancerId|String|是|lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|AclId|String|否|off|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on | off**

 |
|AclType|String|否|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

 设置白名单存在一定业务风险。

 一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

 如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

 -   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

 如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|Bandwidth|Integer|否|-1|监听的带宽峰值，取值：**-1|1-5120**

 -   **-1**：不限制带宽峰值。
-   **1-5120**（Mbps）：监听的带宽峰值，所有监听的带宽峰值之和不能超过实例的带宽峰值。

 |
|Description|String|否|test|设置监听的描述信息。

 |
|HealthCheckConnectPort|Integer|否|80|健康检查使用的端口。

 取值：**1-65535**

 |
|HealthCheckConnectTimeout|Integer|否|100|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）

 **说明：** 如果**HealthCheckConnectTimeout**的值小于**HealthCheckInterval**的值，则**HealthCheckConnectTimeout**无效，超时时间为**HealthCheckInterval**的值。

 |
|HealthCheckInterval|Integer|否|5|健康检查的时间间隔。

 取值：**1-50**（秒）

 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**

 |
|MasterSlaveServerGroup|String|否|on|是否使用主备服务器组。取值：**on|off**

 **VserverGroup**和**MasterSlaveServerGroup**只允许一个值为**on**。

 |
|MasterSlaveServerGroupId|String|否|rsp-0bfucwuotx|主备服务器组ID。

 **说明：** 服务器组ID和主备服务器组ID只能选择一个。

 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。

当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。

-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。
-   **sch**：基于源IP地址的一致性hash，相同的源地址会调度到相同的后端服务器。
-   **tch**：基于四元组的一致性hash（源IP+目的IP+源端口+目的端口），相同的流会调度到相同的后端服务器。
-   **qch**：基于QUIC Connection ID一致性hash，相同的QUIC Connection ID会调度到相同的后端服务器。

 **说明：** 仅有性能保障型实例支持sch、 tch和 qch一致性hash算法。

 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**

 |
|VServerGroup|String|否|on|是否使用虚拟服务器组。

 取值：**on | off**

 **说明：** **VserverGroup**和**MasterSlaveServerGroup**只允许一个值为**on**。

 |
|VServerGroupId|String|否|rsp-cige6j5e7p|虚拟服务器组ID。

 |
|healthCheckExp|String|否|ok|UDP监听健康检查的响应串，只允许包含字母、数字字符，最大长度限制为500字符。

 |
|healthCheckReq|String|否|hello|UDP监听健康检查的请求串，只允许包含字母、数字字符，最大长度限制为500字符。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerUDPListenerAttributeResponse>
  <RequestId>A0F0643E-D653-4F6F-A67F-205B2A92BE18</RequestId>
</SetLoadBalancerUDPListenerAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A0F0643E-D653-4F6F-A67F-205B2A92BE18"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

