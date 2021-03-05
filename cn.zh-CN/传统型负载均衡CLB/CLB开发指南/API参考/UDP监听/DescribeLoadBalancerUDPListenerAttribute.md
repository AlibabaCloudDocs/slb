# DescribeLoadBalancerUDPListenerAttribute

调用DescribeLoadBalancerUDPListenerAttribute查询UDP监听的配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerUDPListenerAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerUDPListenerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerUDPListenerAttribut**。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1**~**65535**。 |
|LoadBalancerId|String|是|lb-bp1rtfnodmywb43e\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|ListenerPort|Integer|53|负载均衡实例前端使用的端口。 |
|BackendServerPort|Integer|90|负载均衡实例后端使用的端口。

 **说明：** 如果后端服务器组为虚拟服务器组，则不返回该参数。 |
|Bandwidth|Integer|-1|监听的带宽峰值，单位Mbps。取值：

 -   **-1**：对于按流量计费的公网负载均衡实例，可以将带宽峰值设置为-1，即不限制带宽峰值。
-   **1**~**5120**：对于按带宽计费的公网负载均衡实例，可以设置每个监听的带宽峰值，但所有监听的带宽峰值之和不能超过实例的带宽峰值。 |
|Status|String|stopped|当前监听的状态。取值：

 -   **running**：监听正常运行。
-   **stopped**：监听停止运行。 |
|Scheduler|String|wrr|调度算法，取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。

当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。

-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on**（默认值）或**off**。 |
|HealthyThreshold|Integer|4|健康检查阈值。健康检查连续成功多少次后，将后端服务器的健康检查状态由**失败**判定为**成功**。取值：**2**~**10**。 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。健康检查连续失败多少次后，将后端服务器的健康检查状态由**成功**判定为**失败**。取值：**2**~**10**。 |
|HealthCheckConnectTimeout|Integer|100|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。取值：**1**~**300**秒。 |
|HealthCheckConnectPort|Integer|8080|健康检查的端口。取值：**1**~**65535**。不设置此参数时，表示使用后端服务端口（BackendServerPort）。

 **说明：** 在**HealthCheck**值为**on**时才会有效。 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，取值：**1**~**50**秒。 |
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*|绑定的虚拟服务器组ID。 |
|AclId|String|123943\*\*\*\*\*|访问控制策略组ID。 |
|AclStatus|String|off|是否开启访问控制功能。取值：**on**或**off**（默认值）。 |
|AclType|String|white|访问控制类型：

 -   **white**：仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发全部请求。

-   **black**：来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。 |
|Description|String|访问控制|访问控制描述。 |
|HealthCheckExp|String|ok|UDP监听健康检查的响应串。只允许包含字母、数字，最大长度限制为64个字符。 |
|HealthCheckReq|String|hello|UDP监听健康检查的请求串。只允许包含字母、数字，最大长度限制为64个字符。 |
|MasterSlaveServerGroupId|String|rsp-0bfucw\*\*\*\*|绑定的主备服务器组ID。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43e*****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeLoadBalancerUDPListenerAttributeResponse>
    <AclStatus>off</AclStatus>
    <HealthCheck>on</HealthCheck>
    <HealthCheckConnectTimeout>5</HealthCheckConnectTimeout>
    <PersistenceTimeout>0</PersistenceTimeout>
    <ListenerPort>80</ListenerPort>
    <Status>stopped</Status>
    <Scheduler>wrr</Scheduler>
    <HealthyThreshold>3</HealthyThreshold>
    <HealthCheckInterval>2</HealthCheckInterval>
    <RequestId>9C103591-2533-432B-9E6B-6DB098C0E65C</RequestId>
    <UnhealthyThreshold>3</UnhealthyThreshold>
    <BackendServerPort>34</BackendServerPort>
    <Bandwidth>67</Bandwidth>
</DescribeLoadBalancerUDPListenerAttributeResponse>
```

`JSON`格式

```
{
	"AclStatus":"off",
	"HealthCheck":"on",
	"HealthCheckConnectTimeout":5,
	"PersistenceTimeout":0,
	"ListenerPort":80,
	"Status":"stopped",
	"Scheduler":"wrr",
	"HealthyThreshold":3,
	"HealthCheckInterval":2,
	"RequestId":"9C103591-2533-432B-9E6B-6DB098C0E65C",
	"UnhealthyThreshold":3,
	"BackendServerPort":34,
	"Bandwidth":67
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

