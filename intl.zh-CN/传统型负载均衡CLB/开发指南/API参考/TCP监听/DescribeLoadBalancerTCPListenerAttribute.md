# DescribeLoadBalancerTCPListenerAttribute

调用DescribeLoadBalancerTCPListenerAttribute查询TCP监听配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerTCPListenerAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerTCPListenerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerTCPListenerAttribute**。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1~65535**。 |
|LoadBalancerId|String|是|lb-bp1ygod3yctvg1y\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|ListenerPort|Integer|443|负载均衡实例前端使用的端口。 |
|BackendServerPort|Integer|443|负载均衡实例后端使用的端口。

 **说明：** 当后端服务器组为虚拟服务器组时，该参数不显示。 |
|Status|String|stopped|当前监听的状态。

 取值：**running\|stopped**。

 -   **running**：监听正常运行中。
-   **stopped**：监听停止。 |
|Bandwidth|Integer|-1|监听的带宽峰值。 |
|Scheduler|String|wrr|调度算法。

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|SynProxy|String|enable|是否开启SynProxy，SynProxy是负载均衡的攻击防护功能。

 建议用户一般情况下不要调整这个参数，由负载均衡控制。

 -   **enable**：开启。
-   **disable**：关闭。 |
|PersistenceTimeout|Integer|0|是否开启了会话保持。

 取值为**0**时，表示没有开启。 |
|EstablishedTimeout|Integer|500|连接超时时间。 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on \| off**。 |
|HealthyThreshold|Integer|4|健康检查阈值。 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。 |
|HealthCheckConnectTimeout|Integer|100|超时时间。 |
|HealthCheckConnectPort|Integer|8080|健康检查使用的端口。 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，单位为秒。 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|健康检查正常的HTTP状态码。 |
|HealthCheckDomain|String|www.domain.com|用于健康检查的域名。 |
|HealthCheckURI|String|/test/index.html|用于健康检查的URI。

 长度限制为1~80，只能使用字母、数字和-/.%?\#&这些字符。 URL不能只为/，但必须以/开头。 |
|HealthCheckType|String|tcp|TCP协议监听的健康检查方式。

 取值：**tcp \| http**。 |
|HealthCheckMethod|String|tcp|健康检查方式。 |
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*8|绑定的服务器组ID。 |
|MasterSlaveServerGroupId|String|rsp-0bfucw\*\*\*\*\*|绑定的主备服务器组ID。 |
|AclId|String|12|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclType|String|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclStatus|String|off|是否开启访问控制功能。

 取值：**on \| off**（默认值）。 |
|Description|String|描述。|监听描述。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancerTCPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeLoadBalancerTCPListenerAttributeResponse>
			  <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode>
	  <PersistenceTimeout>0</PersistenceTimeout>
	  <HealthCheckType>tcp</HealthCheckType>
	  <HealthyThreshold>3</HealthyThreshold>
	  <Scheduler>wrr</Scheduler>
	  <UnhealthyThreshold>3</UnhealthyThreshold>
	  <Bandwidth>-1</Bandwidth>
	  <Description>tcp_80</Description>
	  <AclStatus>off</AclStatus>
	  <HealthCheckURI>/</HealthCheckURI>
	  <HealthCheck>on</HealthCheck>
	  <HealthCheckConnectTimeout>5</HealthCheckConnectTimeout>
	  <ListenerPort>80</ListenerPort>
	  <Status>running</Status>
	  <EstablishedTimeout>900</EstablishedTimeout>
	  <HealthCheckDomain></HealthCheckDomain>
	  <HealthCheckInterval>2</HealthCheckInterval>
	  <RequestId>9A113A8C-BB8F-475E-9533-7819ECA2FFC1</RequestId>
	  <BackendServerPort>80</BackendServerPort>
    </DescribeLoadBalancerTCPListenerAttributeResponse>
```

`JSON` 格式

```
{
    "HealthCheckHttpCode": "http_2xx,http_3xx", 
    "PersistenceTimeout": 0, 
    "HealthCheckType": "tcp", 
    "HealthyThreshold": 3, 
    "Scheduler": "wrr", 
    "UnhealthyThreshold": 3, 
    "Bandwidth": -1, 
    "Description": "tcp_80", 
    "AclStatus": "off", 
    "HealthCheckURI": "/", 
    "HealthCheck": "on", 
    "HealthCheckConnectTimeout": 5, 
    "ListenerPort": 80, 
    "Status": "running", 
    "EstablishedTimeout": 900, 
    "HealthCheckDomain": "", 
    "HealthCheckInterval": 2, 
    "RequestId": "9A113A8C-BB8F-475E-9533-7819ECA2FFC1", 
    "BackendServerPort": 80
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

