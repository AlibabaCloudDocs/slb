# CreateLoadBalancer

调用CreateLoadBalancer创建负载均衡实例。

在使用该接口创建实例时，请注意：

-   实例创建前，请调用[DescribeAvailableResource](~~117645~~)查询可用区支持的资源售卖情况。
-   实例创建后，会产生费用。
-   如果不指定实例规格**LoadBalancerSpec**，则创建性能共享型实例。建议在创建负载均衡实例时，通过规格参数**LoadBalancerSpec**指定实例的规格。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancer&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateLoadBalancer|要执行的操作。

 取值：**CreateLoadBalancer**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |
|AddressType|String|否|internet|负载均衡实例的网络类型。取值：

 -   **internet**：创建公网负载均衡实例后，系统会分配一个公网IP地址，可以转发公网请求。
-   **intranet**：创建内网负载均衡实例后，系统会分配一个内网IP地址，仅可转发内网请求。 |
|InternetChargeType|String|否|paybytraffic|公网类型实例的付费方式。取值：

 -   paybytraffic：按流量计费（默认值）。 |
|Bandwidth|Integer|否|10|监听的带宽峰值，单位Mbps。

 取值：**-1**或**1~5120**。

 -   **-1**：对于按流量计费的公网负载均衡实例，可以将带宽峰值设置为**-1**，即不限制带宽峰值。
-   **1~5120**： 对于按带宽计费的公网负载均衡实例，可以设置每个监听的带宽峰值，但所有监听的带宽峰值之和不能超过实例的带宽峰值。详情参见[共享实例带宽](~~85930~~)。 |
|ClientToken|String|否|5A2CFF0E-5718-\*\*\*\*\*\*\*45B5-9D4D-70B3FF3898|用于保证请求的幂等性。由客户端生成该参数值，要保证在不同请求间唯一，最大不值过64个ASCII字符。 |
|LoadBalancerName|String|否|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例的名称。

 长度为1~80个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。

 不指定该参数时，默认由系统分配一个实例名称。 |
|VpcId|String|否|vpc-bp1aevy8sofi8mh1\*\*\*\*\*|负载均衡实例的所属的VPC ID。 |
|VSwitchId|String|否|vsw-bp12mw1f8k3jgy\*\*\*\*\*|专有网络实例的所属的交换机ID。

 创建专有网络类型的负载均衡实例，必须指定该参数。如果指定了该参数，**AddessType**参数的值会默认被设置为**intranet**。 |
|MasterZoneId|String|否|cn-hangzhou-b|负载均衡实例的主可用区ID。

 您可以通过调用[DescribeZone](~~27585~~)接口可查到相应地域下的主备可用区信息。 |
|SlaveZoneId|String|否|cn-hangzhou-d|负载均衡实例的备可用区ID。

 您可以通过调用[DescribeZone](~~27585~~)接口可查到相应地域下的主备可用区信息。 |
|LoadBalancerSpec|String|否|slb.s2.small|负载均衡实例的规格。取值：

 -   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

 每个地域支持的规格不同。

 目前支持性能保障型实例的地域有：华北 1（青岛）、华北 2（北京）、华东 1（杭州）、华东 2（上海）、华南 1（深圳）、华北 3（张家口）、华北 5 （呼和浩特）、亚太东南 1（新加坡）、英国（伦敦）、欧洲中部 1（法兰克福）、亚太东南 2（悉尼）、亚太东南 3（吉隆坡）、中东东部 1（迪拜）、亚太东南 5（雅加达）、美西 1（硅谷）、亚太南部 1（孟买）、亚太东北 1（东京）、中国香港和美东 1（弗吉尼亚）。关于每种规格的说明，参见[性能保障型实例](~~85931~~)。

 **说明：** 若不指定规格，则创建性能共享型实例。 |
|ResourceGroupId|String|否|rg-atstuj3rtopt\*\*\*\*|企业资源组ID。 |
|PayType|String|否|PayOnDemand|实例的计费类型，取值：

 -   **PayOnDemand**：按量付费。 |
|PricingCycle|String|否|month|预付费公网实例的计费周期，取值：**month**或**year**

 **说明：** 该参数仅适用于中国站且仅对包年包月实例有效，即**PayType**的参数值为**PrePay**时有效。 |
|Duration|Integer|否|1|预付费公网实例的购买时长，取值：

 -   如果**PricingCycle**为**month**，取值为**1~9**。
-   如果**PricingCycle**为**year**，取值为**1~3**。

 **说明：** 该参数仅适用于中国站且仅对包年包月实例有效，即**PayType**的参数值为**PrePay**时有效。 |
|AutoPay|Boolean|否|true|是否是自动支付预付费公网实例的账单。取值：

 -   **true：**自动支付。调用API后，马上生成SLB实例。
-   **false（默认）：**默认选择。调用API后SLB的订单创建成功，但是未支付。您可以在控制台看到未支付订单。由于订单未支付，SLB实例不会被创建出来。

 该参数仅适用于中国站且仅对包年包月实例有效，即**PayType**的参数值为**PrePay**时有效。 |
|AddressIPVersion|String|否|ipv4|负载均衡实例的IP版本，可以设置为**ipv4**或者**ipv6**。 |
|Address|String|否|192.168.0.\*\*|指定负载均衡实例的私网IP地址，该地址必须包含在交换机的目标网段下。 |
|DeleteProtection|String|否|on|是否开启实例删除保护。 |
|ModificationProtectionStatus|String|否|ConsoleProtection|负载均衡修改保护状态：

 -   **NonProtection**：不保护，表示不允许传入ModificationProtectionReason。如果配置了ModificationProtectionReason，则清空其配置信息。
-   **ConsoleProtection**：控制台修改保护，此时允许传入ModificationProtectionReason。 |
|ModificationProtectionReason|String|否|托管实例|修改保护原因。长度为2~128个英文或中文字符，必须以字母或中文开头，可包含数字、英文句号（.）、下划线（\_）和短划线（-）。

 **说明：** 仅在`ModificationProtectionStatus`为**ConsoleProtection**时有效且合法。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|lb-hddhfjg\*\*\*\*\*\*\*|负载均衡实例的ID。 |
|Address|String|42.250.\*\*.\*\*|分配的负载均衡实例的IP地址。 |
|VpcId|String|vpc-25dvzy9\*\*\*\*\*|负载均衡实例的所属专有网络的ID。 |
|VSwitchId|String|vsw-255ecr\*\*\*|负载均衡实例的所属交换机的ID。 |
|LoadBalancerName|String|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例的名称。 |
|AddressIPVersion|String|ipv4|负载均衡实例的IP地址类型。 |
|NetworkType|String|classic|负载均衡实例的网络类型，取值：**vpc**或**classic**。

 -   **vpc**：专有网络实例
-   **classic**：经典网络实例 |
|OrderId|Long|201429619788910|订单ID。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|ResourceGroupId|String|rg-atstuj3rto\*\*\*\*\*\*|企业资源组ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateLoadBalancer
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateLoadBalancerResponse>
    <NetworkType>vpc</NetworkType>
	  <LoadBalancerName>lb-bp1o94dp5i6ea*******</LoadBalancerName>
	  <Address>192.168.0.**</Address>
	  <ResourceGroupId>rg-acfmxazb***</ResourceGroupId>
	  <RequestId>AB197CF0-D9E9-4475-A89D-35DBCCF13BBE</RequestId>
	  <AddressIPVersion>ipv4</AddressIPVersion>
	  <LoadBalancerId>lb-bp1b6c719dfa0***</LoadBalancerId>
	  <VSwitchId>vsw-bp12mw1f8k3jgygk9****</VSwitchId>
	  <VpcId>vpc-bp1aevy8sofi8mh1q***</VpcId>
</CreateLoadBalancerResponse>
```

`JSON` 格式

```
{
    "NetworkType": "vpc",
    "LoadBalancerName": "lb-bp1o94dp5i6ea*******",
    "Address": "192.168.0.**",
    "ResourceGroupId": "rg-acfmxazb4ph****",
    "RequestId": "AB197CF0-D9E9-4475-A89D-35DBCCF13BBE",
    "AddressIPVersion": "ipv4",
    "LoadBalancerId": "lb-bp1b6c719dfa08ex****",
    "VSwitchId": "vsw-bp12mw1f8k3jgygk9****",
    "VpcId": "vpc-bp1aevy8sofi8mh1****"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

