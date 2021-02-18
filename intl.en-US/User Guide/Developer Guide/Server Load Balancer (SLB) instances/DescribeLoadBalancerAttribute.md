# DescribeLoadBalancerAttribute

Queries the details of a Server Load Balancer \(SLB\) instance.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerAttribute|The name of this action.

 Value: **DescribeLoadBalancerAttribute** |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08ex\*\*\*\*\*|The ID of the SLB instance to be queried. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|LoadBalancerId|String|lb-dhhd\*\*\*\*\*\*|The ID of the SLB instance. |
|ResourceGroupId|String|rg-atstuj3rtop\*\*\*\*\*|The ID of the enterprise resource group. |
|LoadBalancerName|String|abc|The name of the SLB instance. |
|LoadBalancerStatus|String|active|The status of the SLB instance. Valid values:

 -   **inactive**: The listeners of an SLB instance do not forward traffic when the SLB instance is in the inactive state.
-   **active**: The instance is running. After an SLB instance is created, it is in the **active** state by default.
-   **locked**: The instance is locked. The instance has an overdue payment or is locked by Alibaba Cloud. |
|RegionId|String|cn-hangzhou|The ID of the region to which the SLB instance belongs. |
|RegionIdAlias|String|cn-hangzhou|The name of the region to which the SLB instance belongs. |
|Address|String|42.250.6.\*\*|The IP address of the SLB instance. |
|AddressType|String|internet|The IP address type of the SLB instance. |
|VpcId|String|vpc-25dvzy9f8\*\*\*\*\*|The ID of the VPC to which the internal SLB instance belongs. |
|VSwitchId|String|vsw-255ecrwq5\*\*\*\*\*|The ID of the VSwitch to which the internal SLB instance belongs. |
|NetworkType|string|vpc|The network type of the SLB instance. |
|InternetChargeType|String|paybybandwidth|The billing method of the public-facing SLB instance.

 Valid values: **paybybandwidth \| paybytraffic**

 -   **paybybandwidth**: billed based on bandwidth
-   **paybytraffic** \(default\): billed based on the actually used traffic |
|AutoReleaseTime|Long|1513947075|The scheduled release time. |
|Bandwidth|Integer|5|The peak bandwidth of the pay-by-bandwidth public-facing SLB instance. |
|LoadBalancerSpec|String|slb.s2.small|The specification of the SLB instance. |
|CreateTime|String|2017-08-31T02:49:05Z|The time when the SLB instance is created. |
|CreateTimeStamp|Long|1504147745000|The timestamp generated when the SLB instance is created. |
|EndTime|String|2999-09-08T16:00:00Z|The time when the SLB instance expires. |
|EndTimeStamp|Long|32493801600000|The timestamp generated when the SLB instance expires. |
|PayType|String|PrePay|The billing method of the SLB instance. Valid values: PayOnDemand \| PrePay |
|MasterZoneId|String|cn-hangzhou-b|The ID of the primary zone to which the SLB instance belongs. |
|SlaveZoneId|String|cn-hangzhou-b|The ID of the secondary zone to which the SLB instance belongs. |
|AddressIPVersion|string|ipv4|The IP version of the SLB instance. |
|RenewalDuration|Integer|1|The period of an automatic renewal. This parameter is valid only when the value of **RenewalStatus** is **AutoRenewal**.

 -   If the value of **PeriodUnit** is **Year**, valid values of this parameter are 1, 2, and 3.
-   If the value of **PeriodUnit** is **Month**, valid values of this parameter are 1, 2, 3, and 6. |
|RenewalStatus|String|AutoRenewal|The renewal mode of the SLB instance. Valid values:

 -   **AutoRenewal**: Automatic renewal is enabled.
-   **Normal**: You must renew the SLB instance manually.
-   **NotRenewal**: Renewal is stopped for the SLB instance. If this value is returned, Alibaba Cloud stops sending notifications about the impending instance expiration, and only sends one reminder on the third day before the SLB instance expires. |
|RenewalCycUnit|String|Month|The automatic renewal cycle. This parameter is valid only when the value of the **RenewalStatus** parameter is **AutoRenewal**.

 Valid values: **Year \| Month**. Default value: Month |
|DeleteProtection|String|off|Indicates whether deletion protection is enabled to protect the SLB instance from being mistakenly deleted.

 Valid values: **on \| off** |
|ListenerPortsAndProtocal|Array| |The frontend ports and protocols used by the listeners of the SLB instance. |
|ListenerPort|Integer|443|The frontend port used by the listener of the SLB instance. |
|ListenerProtocal|String|http|The listening protocol used by the listener of the SLB instance. |
|ListenerPortsAndProtocol|Array| |The frontend ports and protocols used by the listeners of the SLB instance. |
|ListenerPort|Integer|443|The frontend port used by the listener of the SLB instance. |
|ListenerProtocol|String|https|The listening protocol used by the listener of the SLB instance. |
|ListenerForward|String|yes|Indicates whether HTTP-to-HTTPS redirection is enabled. |
|ForwardPort|Integer|80|The destination listening port to which the requests are redirected. It must be the port of an existing HTTPS listener. |
|Description|String|The description of the listener.|The description of the listening port and protocol used by the listener. |
|BackendServers|Array| |The list of backend servers of the SLB instance. |
|ServerId|String|i-djghr2\*\*\*\*|The ID of the backend server. |
|Weight|Integer|90|The weight of the backend server. |
|Type|String|ecs|The type of the backend server. |
|Description|String|The description of the backend server.|The description of the backend server. |
|ListenerPorts|List|80|The list of frontend ports used by the listeners of the SLB instance. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-bp1b6c719dfa08ex*****
&<CommonParameters>
```

Response example

`XML` format

```
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
	  <ListenerPorts></ListenerPorts>
	  <InternetChargeType>paybytraffic</InternetChargeType>
	  <VSwitchId>vsw-bp12mw1f8k3*********</VSwitchId>
	  <VpcId>vpc-bp1aevy8sofi8mh*****</VpcId>
	  <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
	  <LoadBalancerSpec>slb.s2.small</LoadBalancerSpec>
	  <NetworkType>vpc</NetworkType>
	  <ListenerPortsAndProtocol></ListenerPortsAndProtocol>
	  <PayType>PayOnDemand</PayType>
	  <Bandwidth>5120</Bandwidth>
	  <LoadBalancerName>abc1</LoadBalancerName>
	  <ResourceGroupId>rg-acfmxazb4p*****</ResourceGroupId>
	  <AddressIPVersion>ipv4</AddressIPVersion>
	  <LoadBalancerId>lb-bp1b6c719dfa08e*****</LoadBalancerId>
	  <EndTimeStamp>32493801600000</EndTimeStamp>
	  <MasterZoneId>cn-hangzhou-b</MasterZoneId>
	  <ListenerPortsAndProtocal></ListenerPortsAndProtocal>
	  <Address>192.168.0. *</Address>
	  <RegionId>cn-hangzhou</RegionId>
	  <RequestId>35D745B3-1567-4855-9EF1-F5CED3C1670C</RequestId>
	  <CreateTime>2018-11-08T12:21:53Z</CreateTime>
	  <AddressType>intranet</AddressType>
	  <EndTime>2999-09-08T16:00:00Z</EndTime>
	  <LoadBalancerStatus>active</LoadBalancerStatus>
</DescribeLoadBalancerAttributeResponse>
```

`JSON` format

```
{
    "CreateTimeStamp": 1541679713000, 
    "RegionIdAlias": "cn-hangzhou", 
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-bp1c3zrr37ab*****", 
                "Weight": 100, 
                "Type": "ecs"
            }
        ]
    }, 
    "HasReservedInfo": "false", 
    "ListenerPorts": {
        "ListenerPort": [ ]
    }, 
    "InternetChargeType": "paybytraffic", 
    "VSwitchId": "vsw-bp12mw1f8k******", 
    "VpcId": "vpc-bp1aevy8sofi8mh******", 
    "SlaveZoneId": "cn-hangzhou-d", 
    "LoadBalancerSpec": "slb.s2.small", 
    "NetworkType": "vpc", 
    "ListenerPortsAndProtocol": {
        "ListenerPortAndProtocol": [ ]
    }, 
    "PayType": "PayOnDemand", 
    "Bandwidth": 5120, 
    "LoadBalancerName": "abc1", 
    "ResourceGroupId": "rg-acfmxazb*****", 
    "AddressIPVersion": "ipv4", 
    "LoadBalancerId": "lb-bp1b6c719dfa08*****", 
    "EndTimeStamp": 32493801600000, 
    "MasterZoneId": "cn-hangzhou-b", 
    "ListenerPortsAndProtocal": {
        "ListenerPortAndProtocal": [ ]
    }, 
    "Address": "192.168.0. **", 
    "RegionId": "cn-hangzhou", 
    "RequestId": "35D745B3-1567-4855-9EF1-F5CED3C1670C", 
    "CreateTime": "2018-11-08T12:21:53Z", 
    "AddressType": "intranet", 
    "EndTime": "2999-09-08T16:00:00Z", 
    "LoadBalancerStatus": "active"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

