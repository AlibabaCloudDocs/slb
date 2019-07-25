# DescribeLoadBalancerUDPListenerAttribute {#doc_api_Slb_DescribeLoadBalancerUDPListenerAttribute .reference}

调用DescribeLoadBalancerUDPListenerAttribute查询UDP监听的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerUDPListenerAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerUDPListenerAttribute|要执行的操作。

 取值：DescribeLoadBalancerUDPListenerAttribut。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp1rtfnodmywb43e\*\*\*\*\*|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ListenerPort|Integer|53|负载均衡实例前端使用的端口。

 |
|BackendServerPort|Integer|53|负载均衡实例后端使用的端口。

 **说明：** 如果后端服务器组为虚拟服务器组，则不返回该参数。

 |
|Bandwidth|Integer|-1|监听的带宽峰值。

 |
|Status|String|stopped|当前监听的状态。

 取值：**starting | running | configuring | stopping | stopped**

 |
|Scheduler|String|wrr|调度算法。

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。

当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。

-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。

 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on | off**。

 |
|HealthyThreshold|Integer|4|健康检查阈值。

 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。

 |
|HealthCheckConnectTimeout|Integer|100|健康检查响应超时时间。

 |
|HealthCheckConnectPort|Integer|8080|健康检查的端口。

 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，单位为秒。

 |
|VServerGroupId|String|rsp-cige6j\*\*\*\*8|绑定的虚拟服务器组ID。

 |
|AclId|String|12394388|访问控制策略组ID。

 |
|AclStatus|String|off|是否开启访问控制功能。

 取值：**on|off**（默认值）。

 |
|AclType|String|white|访问控制类型：

 -   white：

仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发全部请求。

-   black：

来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|Description|String|访问控制描述。|访问控制描述。

 |
|HealthCheckExp|String|ok|UDP监听健康检查的响应串。

 |
|HealthCheckReq|String|hello|UDP监听健康检查的请求串。

 |
|MasterSlaveServerGroupId|String|rsp-0bfucw\*\*\*\*|绑定的主备服务器组ID。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43e*****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
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

`JSON` 格式

``` {#json_return_success_demo}
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

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

