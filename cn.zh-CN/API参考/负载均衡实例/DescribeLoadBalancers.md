# DescribeLoadBalancers {#doc_api_Slb_DescribeLoadBalancers .reference}

调用DescribeLoadBalancers查询已创建的负载均衡实例。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancers)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancers|要执行的操作。取值：**DescribeLoadBalancers**

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|Address|String|否|192.168.0.6|负载均衡实例的服务地址。

 |
|AddressIPVersion|String|否|ipv4|IP版本，可以设置为ipv4或者ipv6。

 **说明：** 目前支持创建IPv6实例且实例类型必须为性能保障型实例的可用区如下：

 华东1地域的E、F两个可用区、华北2地域的F、G两个可用区、华东2地域的所有可用区和华南1地域的D、E两个可用区。

 |
|AddressType|String|否|intranet|负载均衡实例的网络类型，取值：**intranet**或**internet**

 |
|InternetChargeType|String|否|paybybandwidth|公网类型实例付费方式。取值：**paybybandwidth|paybytraffic**

 |
|LoadBalancerId|String|否|lb-bp1b6c719dfa08exfuca5|负载均衡实例ID。

 支持多值查询，最多可输入10个ID，以逗号分隔。

 |
|LoadBalancerName|String|否|abc1|负载均衡实例名称。

 支持多值查询，最多可输入10个名称，以逗号分隔。

 |
|LoadBalancerStatus|String|否|active|负载均衡实例状态：

 -   inactive: 此状态的实例监听不会再转发流量。
-   active: 实例创建后，默认状态为active。
-   locked: 实例已经被锁定。

 |
|MasterZoneId|String|否|cn-hangzhou-b|负载均衡实例的主可用区ID。

 |
|NetworkType|String|否|vpc|私网负载均衡实例的网络类型，取值：**vpc|classic**

 -   vpc：专有网络实例
-   classic：经典网络实例

 |
|PageNumber|Integer|否|1|分页查询时的页码。

 |
|PageSize|Integer|否|50|分页查询时设置的每页行数。

 |
|PayType|String|否|PayOnDemand|负载均衡实例付费类型。取值：**PayOnDemand|PrePay**

 |
|ResourceGroupId|String|否|rg-acfmxazb4ph6aiy|企业资源组ID。

 |
|ServerId|String|否|vm-231|添加的后端服务器（ECS实例）的ID。

 |
|ServerIntranetAddress|String|否|10.80.102.20|添加的后端服务器（ECS实例）的内网地址。

 支持多值查询，以逗号分隔。

 |
|SlaveZoneId|String|否|cn-hangzhou-d|负载均衡实例的备可用区ID。

 目前对金融云用户暂时不支持多可用区功能。

 |
|Tags|String|否|\{"tagKey":"Key1","tagValue":"Value1"\}|负载均衡实例绑定的Tag列表，其结构是一个json dictionary，包含TagKey和TagValue。

 一次请求中，List中的元素最多有10个。

 |
|VSwitchId|String|否|vsw-bp12mw1f8k3jgygk9bmlj|负载均衡实例所属的VSwitch ID。

 |
|VpcId|String|否|vpc-bp1aevy8sofi8mh1qc5cm|负载均衡实例所属的VPC ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancers| | |数组格式，返回负载均衡实例列表，详情见下表。

 |
|└LoadBalancerId|String|282b00102ac-cn-east-hangzhou-01|负载均衡实例ID。

 |
|└LoadBalancerName|String|def|负载均衡实例的名称。

 |
|└LoadBalancerStatus|String|active|负载均衡实例状态：

 -   inactive: 此状态的实例监听不会再转发流量。
-   active: 实例创建后，默认状态为active。
-   locked: 实例已经被锁定。

 |
|└Address|String|100.98.28.55|负载均衡实例服务地址。

 |
|└RegionId|String|cn-hangzhou|负载均衡实例的地域ID。

 |
|└RegionIdAlias|String|cn-hangzhou|负载均衡实例的地域名称。

 |
|└AddressType|String|intranet|负载均衡实例的网络类型。

 |
|└VSwitchId|String|vsw-255ecrwq5|私网负载均衡实例的交换机ID。

 |
|└VpcId|String|vpc-25dvzy9f8|私网负载均衡实例的专有网络ID。

 |
|└NetworkType|String|vpc|私网负载均衡实例的网络类型，取值：

 -   vpc：专有网络实例
-   classic：经典网络实例

 |
|└CreateTime|String|2017-08-31T02:49:05Z|负载均衡实例创建时间。

 |
|└MasterZoneId|String|cn-hangzhou-b|实例的主可用区ID。

 |
|└SlaveZoneId|String|cn-hangzhou-d|实例的备可用区ID。

 |
|└AddressIPVersion|String|ipv4|IP版本，可以设置为ipv4或者ipv6。

 |
|└CreateTimeStamp|Long|1504147745000|负载均衡实例创建时间戳。

 |
|└InternetChargeType|String|paybybandwidth|公网实例的计费方式。取值：

 -   4：paybytraffic，按流量计费（默认值）

 **说明：** 当PayType参数的值为PrePay时，只支持按带宽计费。

 |
|└PayType|String|PrePay|负载均衡实例付费类型，取值PayOnDemand或者PrePay。

 |
|└ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |
|PageNumber|Integer|1|实例列表页码。

 |
|PageSize|Integer|50|当前分页的行数。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|TotalCount|Integer|1|根据过滤条件得到的实例总个数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeLoadBalancersResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
  <PageSize>50</PageSize>
  <LoadBalancers>
    <LoadBalancer>
      <CreateTimeStamp>1541679713000</CreateTimeStamp>
      <LoadBalancerName>abc1</LoadBalancerName>
      <RegionIdAlias>cn-hangzhou</RegionIdAlias>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <AddressIPVersion>ipv4</AddressIPVersion>
      <LoadBalancerId>lb-bp1b6c719dfa08exfuca5</LoadBalancerId>
      <VSwitchId>vsw-bp12mw1f8k3jgygk9bmlj</VSwitchId>
      <InternetChargeType>4</InternetChargeType>
      <VpcId>vpc-bp1aevy8sofi8mh1qc5cm</VpcId>
      <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
      <NetworkType>vpc</NetworkType>
      <MasterZoneId>cn-hangzhou-b</MasterZoneId>
      <CreateTime>2018-11-08T20:21Z</CreateTime>
      <Address>192.168.0.6</Address>
      <RegionId>cn-hangzhou</RegionId>
      <AddressType>intranet</AddressType>
      <PayType>PayOnDemand</PayType>
      <LoadBalancerStatus>active</LoadBalancerStatus>
    </LoadBalancer>
  </LoadBalancers>
  <RequestId>1C7445CB-C21C-4C19-9A3C-65C3190D1944</RequestId>
</DescribeLoadBalancersResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":1,
	"PageSize":50,
	"RequestId":"1C7445CB-C21C-4C19-9A3C-65C3190D1944",
	"LoadBalancers":{
		"LoadBalancer":[
			{
				"CreateTimeStamp":1541679713000,
				"LoadBalancerName":"abc1",
				"RegionIdAlias":"cn-hangzhou",
				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
				"AddressIPVersion":"ipv4",
				"LoadBalancerId":"lb-bp1b6c719dfa08exfuca5",
				"VSwitchId":"vsw-bp12mw1f8k3jgygk9bmlj",
				"InternetChargeType":"4",
				"VpcId":"vpc-bp1aevy8sofi8mh1qc5cm",
				"SlaveZoneId":"cn-hangzhou-d",
				"NetworkType":"vpc",
				"MasterZoneId":"cn-hangzhou-b",
				"RegionId":"cn-hangzhou",
				"Address":"192.168.0.6",
				"CreateTime":"2018-11-08T20:21Z",
				"AddressType":"intranet",
				"PayType":"PayOnDemand",
				"LoadBalancerStatus":"active"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

