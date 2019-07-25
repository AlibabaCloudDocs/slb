# DescribeLoadBalancerAttribute {#doc_api_Slb_DescribeLoadBalancerAttribute .reference}

Queries the details of an SLB instance.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerAttribute| The name of this action.

 Value: **DescribeLoadBalancerAttribute**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08exfuca5| The ID of the SLB instance that you want to query.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|RegionId|String|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|RegionIdAlias|String|cn-hangzhou| The alias of the region to which the SLB instance belongs.

 |
|LoadBalancerName|String|abc| The name of the SLB instance.

 |
|LoadBalancerStatus|String|active| The status of the SLB instance.

 -   **inactive**: When the SLB instance is inactive, the listeners of the instance do not distribute traffic.
-   **active**: After an instance is created, it is in the **active** state by default.
-   **Locked**: The payment of the SLB instance is overdue or the instance is locked by Alibaba Cloud.

 |
|Address|String|42.250.6.36| The IP address of the SLB instance.

 |
|AddressType|String|internet| The address type of the SLB instance.

 |
|NetworkType|String|vpc| The network type of the SLB instance.

 |
|VpcId|String|vpc-25dvzy9f8| The ID of the VPC to which an intranet SLB instance belongs.

 |
|Bandwidth|Integer|5| The peak bandwidth of an Internet instance that is billed based on bandwidth.

 |
|CreateTime|String|2017-08-31T02:49:05Z| The time when the SLB instance is created.

 |
|ListenerPorts| |"ListenerPort": \[ 80, 443 \]| A list of frontend ports used by the SLB instance.

 |
|ListenerPortsAndProtocol| | | A list of the frontend ports and protocols used by the SLB instance.

 |
|└ListenerPort|Integer|443| The frontend port used by the SLB instance.

 |
|└ListenerProtocol|String|https| The frontend protocol used by the SLB instance.

 |
|└Description|String|Listener| A description of the listening port and protocol used by the SLB instance.

 |
|└ForwardPort|Integer|80| The destination listening port to which requests are forwarded. It is an existing HTTPS listening port.

 |
|└ListenerForward|String|yes| Indicates whether redirection is enabled.

 |
|BackendServers| | | The list of backend servers added to the SLB instance.

 |
|└ServerId|String|vm-234| The ID of the backend server \(ECS instance\).

 |
|└Weight|Integer|90| The weight of the backend server.

 |
|└Description|String|Description| A description of the backend server.

 |
|└Type|String|ecs| The backend server type.

 |
|MasterZoneId|String|cn-hangzhou-b| The primary zone ID of the SLB instance.

 |
|AddressIPVersion|String|ipv4| The IP version.

 |
|AutoReleaseTime|Long|1513947075| The specified release time.

 |
|CreateTimeStamp|Long|1504147745000| The timestamp indicating when the SLB instance is created.

 |
|DeleteProtection|String|off| Indicates whether deletion protection is enabled.

 Valid values: **on | off**

 |
|EndTime|String|2999-09-08T16:00:00Z| The end time of the SLB instance.

 |
|EndTimeStamp|Long|32493801600000| The timestamp indicating when the SLB instance ends.

 |
|InternetChargeType|String|paybybandwidth| The billing method of an Internet SLB instance. Valid values: **paybybandwidth | paybytraffic**

 |
|ListenerPortsAndProtocal| | | A list of the listening ports and protocols used by the SLB instance.

 |
|└ListenerPort|Integer|443| The frontend port used by the SLB instance.

 |
|└ListenerProtocal|String|http| The frontend protocol used by the SLB instance.

 |
|LoadBalancerSpec|String|slb.s2.small| The specification of the SLB instance.

 |
|PayType|String|PrePay| The billing method of the SLB instance. Valid values: PayOnDemand | PrePay

 |
|RenewalCycUnit|String|Month| The automatic renewal cycle. It applies only when the value of**RenewalStatus** is**AutoRenewal**.

 Valid values:**Year | Month** \(default value\)

 |
|RenewalDuration|Integer|1| The automatic renewal period of validity. It applies only when the value of**RenewalStatus** is**AutoRenewal**.

 -   Valid values are 1, 2, and 3 when the value of **PeriodUnit** is**Year**.
-   Valid values are 1, 2, 3, and 6 when the value of**PeriodUnit** is**Month**.

 |
|RenewalStatus|String|AutoRenewal| The renewal mode. Valid values:

 -   **AutoRenewal**: Automatic renewal is enabled.
-   **Normal**: You can only renew the SLB instance manually.
-   **NotRenewal**: Renewal is stopped for the instance. If this value is returned, Alibaba Cloud stops sending notifications about the impending instance expiration, and only sends one reminder on the third day before the instance expires.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The request ID.

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui| The ID of the enterprise resource group to which the SLB instance belongs.

 |
|SlaveZoneId|String|cn-hangzhou-d| The secondary zone ID of the SLB instance.

 |
|VSwitchId|String|vsw-255ecrwq5| The ID of the VSwitch to which an intranet SLB instance belongs.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

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

## Error codes {#section_dks_fqk_21f .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

