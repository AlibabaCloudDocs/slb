# DescribeLoadBalancers

Queries Server Load Balancer \(SLB\) instances in a region.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancers|The name of this action.

 Value: **DescribeLoadBalancers** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |
|ServerId|String|No|vm-23\*\*|The ID of the added backend server \(ECS instance\). |
|AddressIPVersion|String|No|ipv4|The IP version of the SLB instance, which can be set to ipv4 or ipv6.

 **Note:** You can create IPv6 instances in the following zones, but the instance type must be guaranteed-performance instances:

 Zone E and Zone F in the China \(Hangzhou\) region, Zone F and Zone G in the China \(Beijing\) region, Zone D and Zone E in the China \(Shanghai\) region, Zone A and Zone B in the China \(Zhangjiakou\) region, and Zone D and Zone E in the China \(Shenzhen\) region. |
|LoadBalancerStatus|String|No|active|The status of the SLB instance. Valid values:

 -   inactive: The listeners of an SLB instance do not forward traffic when the SLB instance is in the inactive state.
-   active: After an SLB instance is created, it is in the active state by default.
-   locked: The SLB instance is locked. |
|LoadBalancerId|String|No|lb-bp1b6c719dfa\*\*\*\*\*\*\*|The ID of the SLB instance.

 Up to 10 IDs can be queried each time. Separate multiple IDs with commas \(,\). |
|LoadBalancerName|String|No|abc1|The name of the SLB instance that you want to query.

 Up to 10 names can be queried each time. Separate multiple names with commas \(,\). |
|ServerIntranetAddress|String|No|10.80.102.\*\*|The internal IP address of the added backend server \(ECS instance\).

 Multiple IP addresses can be queried each time. Separate multiple IP addresses with commas \(,\). |
|AddressType|String|No|intranet|The network type of the SLB instance.

 Valid values: **intranet** \| **internet**

 -   **internet**: Indicates a public-facing SLB instance. After a public-facing SLB instance is created, the system allocates a public IP address to it so that the instance can forward requests from the Internet.
-   **intranet**: Indicates an internal SLB instance. After an internal SLB instance is created, the system allocates a private IP address to it. The internal SLB instance can only forward requests from the internal network. |
|InternetChargeType|String|No|paybybandwidth|The billing method of the public-facing SLB instance. Valid values:

 Valid values: **paybybandwidth \| paybytraffic**

 -   **paybybandwidth**: billed based on bandwidth
-   **paybytraffic**: billed based on the actually used traffic

 **Note:** If this parameter is not specified, the original billing method is used. |
|VpcId|String|No|vpc-bp1aevy8sof\*\*\*\*\*\*\*\*|The ID of the VPC to which the SLB instance belongs. |
|VSwitchId|String|No|vsw-bp12mw1f8k3\*\*\*\*\*\*\*|The ID of the VSwitch to which the SLB instance belongs. |
|NetworkType|String|No|vpc|The network type of the internal SLB instance. Valid values: **vpc \| classic**

 -   vpc: Virtual Private Cloud
-   classic: classic network |
|Address|String|No|192.168.0.\*\*|The IP address of the SLB instance. |
|MasterZoneId|String|No|cn-hangzhou-b|The ID of the primary zone to which the SLB instance belongs. |
|SlaveZoneId|String|No|cn-hangzhou-d|The ID of the secondary zone to which the SLB instance belongs.

 The multi-zone function is unavailable for users of Alibaba Cloud financial cloud solutions. |
|Tags|String|No|\{"tagKey":"Key1","tagValue":"Value1"\}|The list of tags associated with the SLB instance. It is a JSON dictionary that contains TagKey and TagValue pairs.

 For each request, the list can contain up to 10 tags. |
|PayType|String|No|PayOnDemand|The billing method of the SLB instance.

 Valid values: **PayOnDemand \| PrePay**

 -   **PayOnDemand**: pay-as-you-go
-   **PrePay**: subscription |
|ResourceGroupId|String|No|rg-acfmxazb4p\*\*\*\*\*\*|The ID of the enterprise resource group. |
|PageNumber|Integer|No|1|The page number in a paged query. |
|PageSize|Integer|No|50|The number of rows per page.

 Value range: **1 to 100** |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|PageNumber|Integer|1|The page number of the queried SLB instance list. |
|PageSize|Integer|50|The number of rows on the current page. |
|TotalCount|Integer|1|The total number of SLB instances that meet the filter conditions. |
|LoadBalancers|Array| |The list of SLB instances in array format. |
|LoadBalancerId|String|lb-hjfng\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|The ID of the SLB instance. |
|LoadBalancerName|String|def|The name of the SLB instance. |
|LoadBalancerStatus|String|active|The status of the SLB instance. Valid values:

 -   inactive: The listeners of an SLB instance do not forward traffic when the SLB instance is in the inactive state.
-   active: After an SLB instance is created, it is in the active state by default.
-   locked: The SLB instance is locked. |
|Address|String|100.98.28.\*\*|The IP address of the SLB instance. |
|AddressType|String|intranet|The network type of the SLB instance. |
|RegionId|String|cn-hangzhou|The ID of the region to which the SLB instance belongs. |
|RegionIdAlias|String|cn-hangzhou|The name of the region to which the SLB instance belongs. |
|VSwitchId|String|vsw-255ecr\*\*\*\*\*\*|The ID of the VSwitch to which the internal SLB instance belongs. |
|VpcId|String|vpc-25dvzy9f8\*\*\*\*\*\*|The ID of the VPC to which the internal SLB instance belongs. |
|NetworkType|String|vpc|The network type of the internal SLB instance. Valid values:

 -   vpc: Virtual Private Cloud
-   classic: classic network |
|MasterZoneId|String|cn-hangzhou-b|The ID of the primary zone to which the SLB instance belongs. |
|SlaveZoneId|String|cn-hangzhou-d|The ID of the secondary zone to which the SLB instance belongs. |
|InternetChargeType|String|paybybandwidth|The billing method of the public-facing SLB instance. Valid values:

 -   paybytraffic \(default\): billed based on the actually used traffic

 **Note:** If the value of PayType is set to PrePay, only bandwidth-based billing is supported. |
|CreateTime|String|2017-08-31T02:49:05Z|The time when the SLB instance is created. |
|CreateTimeStamp|Long|1504147745000|The timestamp generated when the SLB instance is created. |
|PayType|String|PrePay|The billing method of the SLB instance. Valid values: PayOnDemand \| PrePay |
|ResourceGroupId|String|rg-atstuj3r\*\*\*\*\*\*|The ID of the enterprise resource group. |
|AddressIPVersion|String|ipv4|The IP version of the SLB instance, which can be set to ipv4 or ipv6. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancers
&RegionId=cn-hangzhou
&<CommonParameters>
```

Response example

`XML` format

```
<DescribeLoadBalancersResponse>
      <PageNumber>1</PageNumber>
	  <TotalCount>1</TotalCount>
	  <PageSize>50</PageSize>
	  <LoadBalancers>
		    <LoadBalancer>
			      <CreateTimeStamp>1541679713000</CreateTimeStamp>
			      <LoadBalancerName>abc1</LoadBalancerName>
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
			      <Address>192.168.0. **</Address>
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

```
{
    "PageNumber": 1, 
    "TotalCount": 1, 
    "PageSize": 50, 
    "LoadBalancers": {
        "LoadBalancer": [
            {
                "CreateTimeStamp": 1541679713000, 
                "LoadBalancerName": "abc1", 
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

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

