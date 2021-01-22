# CreateLoadBalancerUDPListener

调用CreateLoadBalancerUDPListener创建UDP监听。

经典网络的负载均衡的UDP协议监听暂不支持查看源地址。

**说明：** 新建的监听的状态为**stopped**。创建完成后，调用StartLoadBalancerListener接口启动监听来转发流量。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerUDPListener&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoadBalancerUDPListener|要执行的操作。

 取值：**CreateLoadBalancerUDPListener**。 |
|Bandwidth|Integer|是|34|监听的带宽峰值。

 取值：**-1\|1-5120**。

 -   **-1**：对于按流量计费的公网负载均衡实例，可以将带宽峰值设置为**-1**，即不限制带宽峰值。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。 |
|LoadBalancerId|String|是|lb-bp1ygod3yctvg1y7\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|地域ID。 |
|BackendServerPort|Integer|否|80|负载均衡实例后端使用的端口，取值：**1-65535**。

 如果不使用服务器组（不指定VServerGroupId），则该参数必选。 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。
-   **sch**：基于源IP地址的一致性hash，相同的源地址会调度到相同的后端服务器。
-   **tch**：基于四元组的一致性hash（源IP+目的IP+源端口+目的端口），相同的流会调度到相同的后端服务器。
-   **qch**：基于QUIC Connection ID一致性hash，相同的QUIC Connection ID会调度到相同的后端服务器。

 仅有性能保障型实例支持 sch、 tch和qch一致性hash算法。 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**。 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**。 |
|HealthCheckConnectTimeout|Integer|否|100|接收来自运行状况检查的响应需要等待的时间。

 如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）。 |
|HealthCheckConnectPort|Integer|否|80|健康检查使用的端口。取值：**1-65535**

 不设置此参数时，表示使用后端服务端口（**BackendServerPort**）。 |
|healthCheckInterval|Integer|否|3|健康检查的时间间隔。

 取值：**1-50**（秒）。 |
|healthCheckReq|String|否|hello|UDP监听健康检查的请求串，只允许包含字母、数字字符，最大长度限制为500字符。 |
|healthCheckExp|String|否|ok|UDP监听健康检查的响应串，只允许包含字母、数字字符，最大长度限制为500字符。 |
|VServerGroupId|String|否|rsp-cige6j\*\*\*\*8|服务器组ID。 |
|MasterSlaveServerGroupId|String|否|rsp-0bfucwu\*\*\*\*|主备服务器组ID。

 **说明：** 服务器组ID和主备服务器组ID只能选择一个。 |
|AclId|String|否|123|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclType|String|否|white|访问控制类型：

 -   **white**：仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发请求。

-   **black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数有效。 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on\|off**（默认值）。 |
|Description|String|否|test|设置监听的描述信息。

 长度限制为1-80个字符，允许包含字母、数字、“-”、“/”、“.”和“\_”等字符。支持中文描述。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateLoadBalancerUDPListener
&Bandwidth=34
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y7******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateLoadBalancerUDPListenerResponse>
	  <RequestId>06F00FBB-3D9E-4CCE-9D43-1A6946A75456</RequestId>
</CreateLoadBalancerUDPListenerResponse>
```

`JSON` 格式

```
{
    "RequestId": "06F00FBB-3D9E-4CCE-9D43-1A6946A75456"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|参数VServerGroupId或MasterSlaveServerGroupId不匹配。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

