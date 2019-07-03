# DescribeLoadBalancerAttribute {#doc_api_Slb_DescribeLoadBalancerAttribute .reference}

调用DescribeLoadBalancerAttribute查询指定负载均衡实例的详细信息。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerAttribute**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08exfuca5|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01|负载均衡实例的ID。

 |
|RegionId|String|cn-hangzhou|负载均衡实例的地域ID。

 |
|RegionIdAlias|String|cn-hangzhou|负载均衡实例所属的地域别名。

 |
|LoadBalancerName|String|abc|负载均衡实例的名称。

 |
|LoadBalancerStatus|String|active|负载均衡实例状态：

 -   **inactive**: 此状态的实例监听不会再转发流量。
-   **active**: 实例创建后，默认状态为**active**。
-   **locked**: 实例已经欠费或被阿里云锁定。

 |
|Address|String|42.250.6.36|负载均衡实例的服务地址。

 |
|AddressType|String|internet|负载均衡实例的地址类型。

 |
|NetworkType|String|vpc|负载均衡实例的网络类型。

 |
|VpcId|String|vpc-25dvzy9f8|私网负载均衡实例的专有网络ID。

 |
|Bandwidth|Integer|5|按带宽计费的公网型实例的带宽峰值。

 |
|CreateTime|String|2017-08-31T02:49:05Z|负载均衡实例的创建时间。

 |
|ListenerPorts| |"ListenerPort": \[ 80, 443 \]|负载均衡实例前端使用的端口列表。

 |
|ListenerPortsAndProtocol| | |负载均衡实例前端使用的端口和协议列表。

 |
|└ListenerPort|Integer|443|负载均衡实例前端使用的端口。

 |
|└ListenerProtocol|String|https|负载均衡实例前端使用的协议。

 |
|└Description|String|监听|负载均衡监听端口和协议描述。

 |
|└ForwardPort|Integer|80|转发到的目的监听端口，必须是已经存在的HTTPS监听端口。

 |
|└ListenerForward|String|yes|是否启用监听转发。

 |
|BackendServers| | |负载均衡实例的后端服务器列表。

 |
|└ServerId|String|vm-234|后端服务器名（ECS实例）ID。

 |
|└Weight|Integer|90|后端服务器的权重。

 |
|└Description|String|描述。|后端服务器描述。

 |
|└Type|String|ecs|后端服务器类型。

 |
|MasterZoneId|String|cn-hangzhou-b|负载均衡实例的主可用区ID。

 |
|AddressIPVersion|String|ipv4|IP版本。

 |
|AutoReleaseTime|Long|1513947075|预约释放时间。

 |
|CreateTimeStamp|Long|1504147745000|负载均衡实例创建时间戳。

 |
|DeleteProtection|String|off|是否开启实例删除保护。

 取值：**on|off**。

 |
|EndTime|String|2999-09-08T16:00:00Z|负载均衡实例结束时间。

 |
|EndTimeStamp|Long|32493801600000|负载均衡实例结束时间戳。

 |
|InternetChargeType|String|paybybandwidth|公网类型实例付费方式。取值：**paybybandwidth|paybytraffic**

 |
|ListenerPortsAndProtocal| | |同ListenerPortsAndProtocol。

 |
|└ListenerPort|Integer|443|负载均衡实例前端使用的端口。

 |
|└ListenerProtocal|String|http|负载均衡实例前端使用的协议。

 |
|LoadBalancerSpec|String|slb.s2.small|负载均衡实例的的性能规格。

 |
|PayType|String|PrePay|负载均衡实例付费类型，取值PayOnDemand或者PrePay。

 |
|RenewalCycUnit|String|Month|自动续费周期，仅在**RenewalStatus**为**AutoRenewal**时有效。

 取值：**Year | Month**（默认值）。

 |
|RenewalDuration|Integer|1|自动续费时长，仅在**RenewalStatus**为**AutoRenewal时**有效.

 -   **PeriodUnit**为**Year**时，取值：1，2，3。
-   **PeriodUnit**为**Month**时，取值：1，2，3，6。

 |
|RenewalStatus|String|AutoRenewal|续费状态，取值：

 -   **AutoRenewal**：自动续费。
-   **Normal**：非自动续费，您需要自行续费负载均衡实例。
-   **NotRenewal**：不再续费。返回该值后，系统不再发送到期提醒，只在到期前第三天发送不续费提醒。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |
|SlaveZoneId|String|cn-hangzhou-d|负载均衡实例的备可用区ID。

 |
|VSwitchId|String|vsw-255ecrwq5|私网负载均衡实例的交换机ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLoadBalancerAttributeResponse>
  <CreateTimeStamp>1541679713000</CreateTimeStamp>
  <RegionIdAlias>cn-hangzhou</RegionIdAlias>
  <BackendServers>
    <BackendServer>
      <ServerId>i-bp1c3zrr37ablp8ujo7v</ServerId>
      <Weight>100</Weight>
      <Type>ecs</Type>
    </BackendServer>
  </BackendServers>
  <HasReservedInfo>false</HasReservedInfo>
  <ListenerPorts/>
  <InternetChargeType>paybytraffic</InternetChargeType>
  <VSwitchId>vsw-bp12mw1f8k3jgygk9bmlj</VSwitchId>
  <VpcId>vpc-bp1aevy8sofi8mh1qc5cm</VpcId>
  <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
  <LoadBalancerSpec>slb.s2.small</LoadBalancerSpec>
  <NetworkType>vpc</NetworkType>
  <ListenerPortsAndProtocol/>
  <PayType>PayOnDemand</PayType>
  <Bandwidth>5120</Bandwidth>
  <LoadBalancerName>abc1</LoadBalancerName>
  <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
  <AddressIPVersion>ipv4</AddressIPVersion>
  <LoadBalancerId>lb-bp1b6c719dfa08exfuca5</LoadBalancerId>
  <EndTimeStamp>32493801600000</EndTimeStamp>
  <MasterZoneId>cn-hangzhou-b</MasterZoneId>
  <ListenerPortsAndProtocal/>
  <Address>192.168.0.6</Address>
  <RegionId>cn-hangzhou</RegionId>
  <RequestId>35D745B3-1567-4855-9EF1-F5CED3C1670C</RequestId>
  <CreateTime>2018-11-08T12:21:53Z</CreateTime>
  <AddressType>intranet</AddressType>
  <EndTime>2999-09-08T16:00:00Z</EndTime>
  <LoadBalancerStatus>active</LoadBalancerStatus>
</DescribeLoadBalancerAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CreateTimeStamp":1541679713000,
	"RegionIdAlias":"cn-hangzhou",
	"HasReservedInfo":"false",
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-bp1c3zrr37ablp8ujo7v",
				"Weight":100,
				"Type":"ecs"
			}
		]
	},
	"ListenerPorts":{
		"ListenerPort":[]
	},
	"VSwitchId":"vsw-bp12mw1f8k3jgygk9bmlj",
	"InternetChargeType":"paybytraffic",
	"VpcId":"vpc-bp1aevy8sofi8mh1qc5cm",
	"SlaveZoneId":"cn-hangzhou-d",
	"NetworkType":"vpc",
	"LoadBalancerSpec":"slb.s2.small",
	"ListenerPortsAndProtocol":{
		"ListenerPortAndProtocol":[]
	},
	"PayType":"PayOnDemand",
	"Bandwidth":5120,
	"LoadBalancerName":"abc1",
	"ResourceGroupId":"rg-acfmxazb4ph6aiy",
	"AddressIPVersion":"ipv4",
	"LoadBalancerId":"lb-bp1b6c719dfa08exfuca5",
	"EndTimeStamp":32493801600000,
	"MasterZoneId":"cn-hangzhou-b",
	"ListenerPortsAndProtocal":{
		"ListenerPortAndProtocal":[]
	},
	"Address":"192.168.0.6",
	"RegionId":"cn-hangzhou",
	"RequestId":"35D745B3-1567-4855-9EF1-F5CED3C1670C",
	"CreateTime":"2018-11-08T12:21:53Z",
	"EndTime":"2999-09-08T16:00:00Z",
	"AddressType":"intranet",
	"LoadBalancerStatus":"active"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

