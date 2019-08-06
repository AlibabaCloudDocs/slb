# CreateLoadBalancerTCPListener {#doc_api_Slb_CreateLoadBalancerTCPListener .reference}

调用CreateLoadBalancerTCPListener创建TCP监听。

**说明：** 新建的监听的状态为stopped。创建完成后，调用[StartLoadBalancerListener](~~27597~~)接口启动监听来转发流量。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerTCPListener&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoadBalancerTCPListener|要执行的操作。

 取值：**CreateLoadBalancerTCPListener**。

 |
|Bandwidth|Integer|是|-1|监听的带宽峰值。取值：**-1|1-5120**。

 -   **-1**：对于按流量计费的公网负载均衡实例，可以将带宽峰值设置为**-1**，即不限制带宽峰值。
-   **1-5120**（Mbps）： 对于按带宽计费的公网负载均衡实例，可以设置每个监听的带宽峰值，但所有监听的带宽峰值之和不能超过实例的带宽峰值。详情参见[共享实例带宽](~~57846~~)。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08ex\*\*\*\*\*\*|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|AclId|String|否|1323|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on | off**（默认值）。

 |
|AclType|String|否|black| 

 访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|BackendServerPort|Integer|否|80|负载均衡实例后端使用的端口。

 取值：**1-65535**。

 如果不使用服务器组（不指定VServerGroupId），则该参数必选。

 |
|Description|String|否|创建监听。|设置监听的描述信息。

 长度限制为1-80个字符，允许包含字母、数字、“-”、“/”、“.”和“\_”等字符。支持中文描述。

 |
|EstablishedTimeout|Integer|否|500|连接超时时间。

 取值：**10-900**（秒）。

 |
|HealthCheckConnectPort|Integer|否|80|健康检查使用的端口。取值：**1-65535**。

 不设置此参数时，表示使用后端服务端口（BackendServerPort）。

 |
|HealthCheckConnectTimeout|Integer|否|100|每次健康检查响应的最大超时时间。

 取值：**1-300**（秒）

 默认值：5。

 |
|HealthCheckDomain|String|否|$\_ip|用于健康检查的域名。取值：

 -   **$\_ip**： 后端服务器的私网IP。当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   **domain**：域名长度为1-80，只能包含字母、数字、点号（.）和连字符（-）。

 |
|HealthCheckHttpCode|String|否|http\_2xx,http\_3xx|健康检查正常的HTTP状态码，多个状态码用逗号（,）分割。

 取值：**http\_2xx（默认值） | http\_3xx | http\_4xx | http\_5xx**。

 |
|HealthCheckType|String|否|tcp|健康检查类型。

 取值：**tcp（默认值） | http**。

 |
|HealthCheckURI|String|否|/test/index.html|用于健康检查的URI。

 当TCP监听需要使用HTTP健康检查时可配置此参数，如不配置则按TCP健康检查。

 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值: **2-10**。

 |
|MasterSlaveServerGroupId|String|否|rsp-0bfucw\*\*\*\*\*|主备服务器组ID。

 **说明：** 服务器组ID和主备服务器组ID只能选择一个。

 |
|PersistenceTimeout|Integer|否|0|会话保持的超时时间。

 取值：**0-3600**（秒）。

 默认值：**0**，表示关闭会话保持。

 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。
-   **sch**：基于源IP地址的一致性hash，相同的源地址会调度到相同的后端服务器。
-   **tch**：基于四元组的一致性hash（源IP+目的IP+源端口+目的端口），相同的流会调度到相同的后端服务器。

 一致性哈希（CH）算法目前仅支持以下地域：

 -   日本（东京）
-   澳大利亚（悉尼）
-   马来西亚（吉隆坡）
-   印度尼西亚（雅加达）
-   德国（法兰克福）
-   美国（硅谷）
-   美国（弗吉利亚）
-   阿联酋（迪拜）
-   华北5（呼和浩特）
-   英国（伦敦）
-   新加坡B、C可用区
-   香港
-   华北1（青岛）
-   华北3（张家口）
-   西南1（成都）
-   华东（杭州）I、H可用区
-   华北2（北京）G、H可用区
-   华南（深圳）D、E可用区
-   华东2（上海）F、G可用区

 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**。

 |
|VServerGroupId|String|否|rsp-cige6j\*\*\*\*\*|服务器组ID。

 |
|healthCheckInterval|Integer|否|3|健康检查的时间间隔。

 取值:**1-50**（秒）。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateLoadBalancerTCPListener
&Bandwidth=-1
&ListenerPort=80
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateLoadBalancerTCPListenerResponse>
			  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
		</CreateLoadBalancerTCPListenerResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|参数VServerGroupId或MasterSlaveServerGroupId不匹配。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

