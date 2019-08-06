# DescribeLoadBalancers {#doc_api_Slb_DescribeLoadBalancers .reference}

Queries one or more SLB instances.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancers| The name of this action.

 Value: **DescribeLoadBalancers**

 |
|RegionId|String|Yes|cn-hangzhou-d| The region to which the SLB instance to be queried belongs.

 To query the region ID, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |
|Address|String|No|192.168.0.6| Optional. The IP address of the SLB instance to be queried.

 |
|AddressIPVersion|String|No|ipv4| Optional. The IP version, which can be set to ipv4 or ipv6.

 **Note:** Currently, you can create IPv6 instances and the instance type must be guaranteed-performance instances in the following zones:

 Zones E and F in China \(Hangzhou\), Zones F and G in China \(Beijing\), all zones in China \(Shanghai\), and Zones D and E in China \(Shenzhen\).

 |
|AddressType|String|No|intranet| Optional. The network type of the SLB instance to be queried. Valid values:**intranet** | **internet**

 |
|InternetChargeType|String|No|paybybandwidth| Optional. The billing method of an Internet SLB instance. Valid values:**paybybandwidth | paybytraffic**

 |
|LoadBalancerId|String|No|lb-bp1b6c719dfa08exfuca5| Optional. The ID of the SLB instance to be queried.

 You can enter up to 10 IDs. Multiple IDs must be separated by commas \(,\).

 |
|LoadBalancerName|String|No|abc1| Optional. The name of the SLB instance to be queried.

 You can enter up to 10 names. Multiple names must be separated by commas \(,\).

 |
|LoadBalancerStatus|String|No|active| Optional. The status of the SLB instance to be queried.

 -   inactive: When an SLB instance is in the inactive state, the listeners of the instance do not distribute traffic.
-   active: After an instance is created, it is in the active state.
-   locked: The SLB instance is in the locked state.

 |
|MasterZoneId|String|No|cn-hangzhou-b| Optional. The primary zone ID of the SLB instance to be queried.

 |
|NetworkType|String|No|vpc| Optional. The network type of an intranet SLB instance. Valid values:**vpc | classic**

 -   vpc: Indicates a network of the VPC type.
-   classic: Indicates a classic network.

 |
|PageNumber|Integer|No|1| Optional. The page number in the case of paging query.

 |
|PageSize|Integer|No|50| Optional. The maximum number of entries on a page.

 |
|PayType|String|No|PayOnDemand| Optional. The billing method of the SLB instance to be queried.

 Valid values:**PayOnDemand | PrePay**

 |
|ResourceGroupId|String|No|rg-acfmxazb4ph6aiy| Optional. The ID of the enterprise resource group.

 |
|ServerId|String|No|vm-231| Optional. The ID of the backend server \(ECS instance\).

 |
|ServerIntranetAddress|String|No|10.80.102.20| Optional. The intranet IP address of the backend server \(ECS instance\).

 You can enter multiple values. Separate multiple values by using commas \(,\).

 |
|SlaveZoneId|String|No|cn-hangzhou-d| Optional. The secondary zone ID of the SLB instance to be queried.

 Currently, multi-zone is not supported for users of Alibaba Cloud’s financial service solutions.

 |
|Tags|String|No|\{"tagKey":"Key1","tagValue":"Value1"\}| Optional. The list of tags associated with the SLB instance to be queried. It is a dictionary that is serialized into JSON and contains TagKey and TagValue pairs.

 For each request, the list can contain up to 10 tags.

 |
|VSwitchId|String|No|vsw-bp12mw1f8k3jgygk9bmlj| Optional. The VSwitch ID of the SLB instance to be queried.

 |
|VpcId|String|No|vpc-bp1aevy8sofi8mh1qc5cm| Optional. The VPC ID of the SLB instance to be queried.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoadBalancers| | | A list of SLB instances in array format.

 |
|└LoadBalancerId|String|282b00102ac-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|└LoadBalancerName|String|def| The name of the SLB instance.

 |
|└LoadBalancerStatus|String|active| The status of the SLB instance.

 -   inactive: When an SLB instance is in the inactive state, the listeners of the instance do not distribute traffic.
-   active: After an instance is created, it is in the active state.
-   locked: The SLB instance is in the locked state.

 |
|└Address|String|100.98.28.55| The IP address of the SLB instance.

 |
|└RegionId|String|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|└RegionIdAlias|String|cn-hangzhou-d| The alias of the region to which the SLB instance belongs.

 |
|└AddressType|String|intranet| The network type of the SLB instance.

 |
|└VSwitchId|String|vsw-255ecrwq5| The ID of the VSwitch to which an intranet SLB instance belongs.

 |
|└VpcId|String|vpc-25dvzy9f8| The ID of the VPC to which an intranet SLB instance belongs.

 |
|└NetworkType|String|vpc| The network type of an intranet SLB instance. Valid values:

 -   vpc: Indicates a network of the VPC type.
-   classic: Indicates a classic network.

 |
|└CreateTime|String|2017-08-31T02:49:05Z| The time when the SLB instance is created.

 |
|└MasterZoneId|String|cn-hangzhou-b| The ID of the primary zone.

 |
|└SlaveZoneId|String|cn-hangzhou-d| The ID of the secondary zone.

 |
|└AddressIPVersion|String|ipv4| The IP version, which can be ipv4 or ipv6.

 |
|└CreateTimeStamp|Long|1504147745000| The timestamp indicating when the SLB instance is created.

 |
|└InternetChargeType|String|paybybandwidth| The billing method of an Internet SLB instance. Valid values:

 -   paybytraffic: billed based on traffic \(default value\)

 **Note:** If the value of PayType is PrePay, only bandwidth-based billing is supported.

 |
|└PayType|String|PrePay| The billing method of the SLB instance. Valid values: PayOnDemand | PrePay.

 |
|└ResourceGroupId|String|rg-atstuj3rtoptyui| The ID of the enterprise resource group.

 |
|PageNumber|Integer|1| The page number of the SLB instance list.

 |
|PageSize|Integer|50| The number of entries on the current page.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The request ID.

 |
|TotalCount|Integer|1| The total number of instances that meet the filter conditions.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

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

## Error codes {#section_fja_h78_o29 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

