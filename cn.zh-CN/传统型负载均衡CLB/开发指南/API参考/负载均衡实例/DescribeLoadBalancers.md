# DescribeLoadBalancers

调用DescribeLoadBalancers查询已创建的负载均衡实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancers&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancers|要执行的操作。

 取值：**DescribeLoadBalancers**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |
|ServerId|String|否|vm-server-23\*\*\*\*\*group|添加的后端服务器（ECS实例）的ID。 |
|AddressIPVersion|String|否|ipv4|IP版本，可以设置为**ipv4**或者**ipv6**。

 **说明：** 目前支持创建IPv6实例且实例类型必须为性能保障型实例的可用区包括：华东1地域的E、F两个可用区、华北2地域的F、G两个可用区、华东2地域的D、E两个可用区、华北3地域的A、B两个可用区和华南1地域的D、E两个可用区。 |
|LoadBalancerStatus|String|否|active|负载均衡实例状态：

 -   **inactive**: 此状态的实例监听不会再转发流量。
-   **active**: 实例创建后，默认状态为**active**。
-   **locked**: 实例已经被锁定。 |
|LoadBalancerId|String|否|lb-bp1b6c719dfa\*\*\*\*\*\*\*|负载均衡实例ID。

 支持多值查询，最多可输入10个ID，以逗号（,）分隔。 |
|LoadBalancerName|String|否|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例名称。

 长度为1~80个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。

 支持多值查询，最多可输入10个名称，以逗号（,）分隔。 |
|ServerIntranetAddress|String|否|10.\*\*.\*\*.102|添加的后端服务器（ECS实例）的内网地址。

 支持多值查询，以逗号（,）分隔。 |
|AddressType|String|否|intranet|负载均衡实例的网络类型。

 取值：**intranet**或**internet**。

 -   **internet**：创建公网负载均衡实例后，系统会分配一个公网IP地址，可以转发公网请求。
-   **intranet**：创建内网负载均衡实例后，系统会分配一个内网IP地址，仅可转发内网请求。 |
|InternetChargeType|String|否|paybybandwidth|公网类型实例付费方式。取值：**paybybandwidth**或**paybytraffic**。

 -   **paybybandwidth**：按带宽计费。
-   **paybytraffic**：按流量计费 。

 **说明：** 如果不指定该参数，则表示保持原有的计费方式。 |
|VpcId|String|否|vpc-bp1aevy8sof\*\*\*\*\*\*\*\*|负载均衡实例所属的VPC ID。 |
|VSwitchId|String|否|vsw-bp12mw1f8k3\*\*\*\*\*\*\*|负载均衡实例所属的交换机ID。 |
|NetworkType|String|否|vpc|私网负载均衡实例的网络类型，取值：**vpc**或**classic**。

 -   **vpc**：专有网络实例
-   **classic**：经典网络实例 |
|Address|String|否|192.168.0.\*\*|负载均衡实例的服务地址。 |
|MasterZoneId|String|否|cn-hangzhou-b|负载均衡实例的主可用区ID。 |
|SlaveZoneId|String|否|cn-hangzhou-d|负载均衡实例的备可用区ID。

 目前对金融云用户暂时不支持多可用区功能。 |
|Tags|String|否|\{"tagKey":"Key1","tagValue":"Value1"\}|负载均衡实例绑定的标签列表，其结构是一个json dictionary，包含标签键和标签值。

 一次请求中，绑定的标签列表中最多支持10个标签。 |
|PayType|String|否|PayOnDemand|负载均衡实例付费类型。取值：**PayOnDemand**或**PrePay**。

 -   **PayOnDemand**：按量付费。
-   **PrePay**：包年包月。 |
|ResourceGroupId|String|否|rg-acfmxazb4p\*\*\*\*\*\*|企业资源组ID。 |
|PageNumber|Integer|否|1|分页查询时的页码。 |
|PageSize|Integer|否|50|分页查询时设置的每页行数。

 取值范围：**1~100**。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancers|Array of LoadBalancer| |数组格式，返回负载均衡实例列表。 |
|LoadBalancer| | | |
|LoadBalancerId|String|lb-bp1b6c719dfa\*\*\*\*\*\*\*|负载均衡实例ID。 |
|LoadBalancerName|String|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例的名称。 |
|LoadBalancerStatus|String|active|负载均衡实例状态：

 -   **inactive**: 此状态的实例监听不会再转发流量。
-   **active**: 实例创建后，默认状态为**active**。
-   **locked**: 实例已经被锁定。 |
|Address|String|100.\*\*.\*\*.28|负载均衡实例服务地址。 |
|RegionId|String|cn-hangzhou|负载均衡实例的地域ID。 |
|RegionIdAlias|String|cn-hangzhou|负载均衡实例的地域名称。 |
|AddressType|String|intranet|负载均衡实例的网络类型。 |
|VSwitchId|String|vsw-255ecr\*\*\*\*\*\*|私网负载均衡实例的交换机ID。 |
|VpcId|String|vpc-25dvzy9f8\*\*\*\*\*\*|私网负载均衡实例的专有网络ID。 |
|NetworkType|String|vpc|私网负载均衡实例的网络类型，取值：

 -   **vpc**：专有网络实例。
-   **classic**：经典网络实例。 |
|CreateTime|String|2017-08-31T02:49:05Z|负载均衡实例创建时间。 |
|MasterZoneId|String|cn-hangzhou-b|实例的主可用区ID。 |
|SlaveZoneId|String|cn-hangzhou-d|实例的备可用区ID。 |
|AddressIPVersion|String|ipv4|IP版本，可以设置为**ipv4**或者**ipv6**。 |
|CreateTimeStamp|Long|1504147745000|负载均衡实例创建时间戳。 |
|InternetChargeType|String|paybybandwidth|公网类型实例付费方式。

 取值：**paybybandwidth**或**paybytraffic**。

 -   **paybybandwidth**：按带宽计费。
-   **paybytraffic**：按流量计费（默认值）。

**说明：** 当PayType参数的值为**PrePay**时，只支持按带宽计费。 |
|ModificationProtectionReason|String|托管实例|修改保护原因。长度为2~128个英文或中文字符，必须以字母或中文开头，可包含数字、英文句号（.）、下划线（\_）和短划线（-）。

 **说明：** 仅在`ModificationProtectionStatus`为**ConsoleProtection**时有效且合法。 |
|ModificationProtectionStatus|String|ConsoleProtection|负载均衡修改保护状态：

 -   **NonProtection**：不保护，表示不允许传入ModificationProtectionReason。如果配置了ModificationProtectionReason，则清空其配置信息。
-   **ConsoleProtection**：控制台修改保护，此时允许传入ModificationProtectionReason。 |
|PayType|String|PrePay|负载均衡实例付费类型，取值**PayOnDemand**或者**PrePay**。 |
|ResourceGroupId|String|rg-atstuj3r\*\*\*\*\*\*|企业资源组ID。 |
|PageNumber|Integer|1|实例列表页码。 |
|PageSize|Integer|50|当前分页的行数。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|TotalCount|Integer|1|根据过滤条件得到的实例总个数。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeLoadBalancersResponse>
      <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <PageSize>50</PageSize>
	  <LoadBalancers>
		    <LoadBalancer>
			      <CreateTimeStamp>1541679713000</CreateTimeStamp>
			      <LoadBalancerName>lb-bp1o94dp5i6ea*******</LoadBalancerName>
			      <RegionIdAlias>cn-hangzhou</RegionIdAlias>
			      <ResourceGroupId>rg-acfmxaz*******y</ResourceGroupId>
			      <AddressIPVersion>ipv4</AddressIPVersion>
			      <LoadBalancerId>lb-bp1b6c********fuca5</LoadBalancerId>
			      <VSwitchId>vsw-bp12mw1f********bmlj</VSwitchId>
			      <InternetChargeType>4</InternetChargeType>
			      <VpcId>vpc-bp1aevy8*********5cm</VpcId>
			      <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
			      <NetworkType>vpc</NetworkType>
			      <MasterZoneId>cn-hangzhou-b</MasterZoneId>
			      <CreateTime>2018-11-08T20:21Z</CreateTime>
			      <Address>192.168.0.**</Address>
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

```
{
    "PageNumber": 1, 
    "TotalCount": 1, 
    "PageSize": 50, 
    "LoadBalancers": {
        "LoadBalancer": [
            {
                "CreateTimeStamp": 1541679713000, 
                "LoadBalancerName": "lb-bp1o94dp5i6ea*******", 
                "RegionIdAlias": "cn-hangzhou", 
                "ResourceGroupId": "rg-acfmxazb4p****", 
                "AddressIPVersion": "ipv4", 
                "LoadBalancerId": "lb-bp1b6c719d******exfuca5", 
                "VSwitchId": "vsw-bp12mw1f8k******bmlj", 
                "InternetChargeType": "4", 
                "VpcId": "vpc-bp1aevy8sof*******5cm", 
                "SlaveZoneId": "cn-hangzhou-d", 
                "NetworkType": "vpc", 
                "MasterZoneId": "cn-hangzhou-b", 
                "CreateTime": "2018-11-08T20:21Z", 
                "Address": "192.168.0.6", 
                "RegionId": "cn-hangzhou", 
                "AddressType": "intranet", 
                "PayType": "PayOnDemand", 
                "LoadBalancerStatus": "active"
            }
        ]
    }, 
    "RequestId": "1C7445CB-C21C-4C19-9A3C-65C3190D1944"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

