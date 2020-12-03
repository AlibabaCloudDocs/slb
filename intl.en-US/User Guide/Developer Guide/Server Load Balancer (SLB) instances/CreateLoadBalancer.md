# CreateLoadBalancer

Creates an SLB instance.

Before you call this operation, take note of the following information:

-   Before you create a Server Load Balancer \(SLB\) instance, call the [DescribeAvailableResource](~~117645~~) operation to query the resources available for purchase in the region where you want to create the instance.
-   After the instance is created, fees will be charged for the instance.
-   If you do not set **LoadBalancerSpec** to set the instance specifications, a shared-resource instance is created. We recommend that you set **LoadBalancerSpec** to set the instance specifications when you create an SLB instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancer&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoadBalancer|The operation that you want to perform.

 Set the value to: **CreateLoadBalancer**. |
|RegionId|String|Yes|cn-hangzhou|The region where you want to create the SLB instance.

 You can call the [DescribeRegions](~~25609~~) operation to query region IDs. |
|AddressType|String|No|internet|The address type of the SLB instance. Valid values:

 -   **internet**: After a public-facing SLB instance is created, the system allocates a public IP address to the SLB instance. Then, the instance can forward requests from the Internet.
-   **intranet**: After an internal SLB instance is created, the system allocates a private IP address to it so that the instance can only forward internal requests. |
|InternetChargeType|String|No|paybytraffic|The billing method of the public-facing SLB instance. Set the value to paybytraffic.

 -   paybytraffic: You are charged on a pay-by-data-transfer basis. This is the default value. |
|Bandwidth|Integer|No|10|The maximum bandwidth of the listener. Unit: Mbit/s.

 Valid values: **1 to 5120 and -1**.

 -   **-1**: For a pay-by-data-transfer public-facing SLB instance, you can set the maximum bandwidth to **-1**. This specifies that the maximum bandwidth is not limited.
-   **1 to 5120**: For a pay-by-bandwidth public-facing SLB instance, you can specify the maximum bandwidth of each listener. The sum of maximum bandwidth values of all listeners cannot exceed the maximum bandwidth of the SLB instance. For more information, see [EIP bandwidth plan](~~85930~~). |
|ClientToken|String|No|5A2CFF0E-5718-45B5-9D4D-70B3FF3898|The client token that is used to ensure the idempotence of the request. You can use the client to generate the value, but you must ensure that it is unique among different requests. The token can only contain ASCII characters and cannot exceed 64 characters in length. |
|LoadBalancerName|String|No|abc|The name of the SLB instance.

 The name must be 1 to 80 characters in length. It must start with letters. It can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\).

 If this parameter is not set, the system automatically assigns a name for the SLB instance. |
|VpcId|String|No|vpc-bp1aevy8sofi8mh1\*\*\*\*\*|The ID of the virtual private cloud \(VPC\) to which the SLB instance belongs. |
|VSwitchId|String|No|vsw-bp12mw1f8k3jgy\*\*\*\*\*|The ID of the VSwitch to which the internal SLB instance belongs.

 To create an internal SLB instance, you must set this parameter. When this parameter is set, the value of the **AddessType** parameter is set to **intranet** by default. |
|MasterZoneId|String|No|cn-hangzhou-b|The ID of the primary zone to which the SLB instance belongs.

 You can call the [DescribeZone](~~27585~~) operation to query the information of the primary and secondary zones in the corresponding region. |
|SlaveZoneId|String|No|cn-hangzhou-d|The ID of the secondary zone to which the SLB instance belongs.

 You can call the [DescribeZone](~~27585~~) operation to query the information of the primary and secondary zones in the corresponding region. |
|LoadBalancerSpec|String|No|slb.s2.small|The types of the SLB instance. Valid values:

 -   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

 The available types vary by region.

 You can purchase guaranteed-performance SLB instances in the following regions: China \(Qingdao\), China \(Beijing\), China \(Hangzhou\), China \(Shanghai\), China \(Shenzhen\), China \(Zhangjiakou\), China \(Hohhot\), Singapore \(Singapore\), UK \(London\), Germany \(Frankfurt\), Australia \(Sydney\), Malaysia \(Kuala Lumpur\), UAE \(Dubai\), Indonesia \(Jakarta\), US \(Silicon Valley\), India \(Mumbai\), Japan \(Tokyo\), China \(Hong Kong\), and US \(Virginia\). For more information about the types of SLB instance, see Guaranteed-performance instance FAQ[~~85931~~](~~85931~~).

 **Note:** If this parameter is not set, a shared-performance instance is created. |
|ResourceGroupId|String|No|rg-atstuj3rtopt\*\*\*\*|The ID of the enterprise resource group. |
|PayType|String|No|PayOnDemand|The billing method of the SLB instance. Set the value to PayOnDemand.

 -   **PayOnDemand**: You are charged on a pay-as-you-go basis. |
|PricingCycle|String|No|month|The subscription period of the subscription public-facing SLB instance. Valid values: **month and year**.

 **Note:**

-   This parameter applies to only the Alibaba Cloud China site \(aliyun.com\).
-   This parameter takes effect for only subscription SLB instances. You can set **PayType** to **PrePay** to specify subscription SLB instances. |
|Duration|Integer|No|1|The subscription duration of the subscription public-facing SLB instance. Valid values:

 -   If you set the value of **PricingCycle** to **month**, the valid values are from **1 to 9**.
-   If you set the value of **PricingCycle** to **year**, the valid values are from **1 to 3**.

 **Note:**

-   This parameter applies to only the Alibaba Cloud China site \(aliyun.com\).
-   This parameter takes effect for only subscription SLB instances. You can set **PayType** to **PrePay** to specify subscription SLB instances. |
|AutoPay|Boolean|No|true|Specifies whether to automatically pay for subscription public-facing SLB instances. Valid values:

 -   **true:** Automatic payment is enabled. After you call the API operation, an SLB instance is created.
-   **false:** This is the default value. After you call the API operation, an order is placed for the SLB instance but the payment is not settled. You can view the order in the SLB console. The SLB instance will not be created before the order is paid.

 This parameter applies to only the Alibaba Cloud China site \(aliyun.com\).

 This parameter takes effect for only subscription SLB instances. You can set **PayType** to **PrePay** to specify subscription SLB instances. |
|AddressIPVersion|String|No|ipv4|The IP protocol used by the SLB instance. Valid values: ipv4 and ipv6. |
|Address|String|No|192.168.0.\*\*|The private IP address of the SLB instance. This private IP address must belong to the destination CIDR blocks of the VSwitch. |
|DeleteProtection|String|No|on|Specifies whether to enable deletion protection for the SLB instance. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoadBalancerId|String|lb-hddhfjg\*\*\*\*\*\*\*|The ID of the SLB instance. |
|Address|String|42.250.\*\*. \*\*|The IP address of the SLB instance. |
|VpcId|String|vpc-25dvzy9\*\*\*\*\*|The ID of the VPC to which the SLB instance belongs. |
|VSwitchId|String|vsw-255ecr\*\*\*|The ID of the VSwitch to which the SLB instance belongs. |
|LoadBalancerName|String|abc|The name of the SLB instance. |
|AddressIPVersion|String|ipv4|The IP protocol used by the SLB instance. |
|NetworkType|String|classic|The type of the network where the SLB instance is deployed. Valid values:**vpc and classic**.

 -   vpc: The SLB instance is deployed in a VPC.
-   classic: The SLB instance is deployed in a classic network. |
|OrderId|Long|201429619788910|The ID of the order. |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ResourceGroupId|String|rg-atstuj3rto\*\*\*\*\*\*|The ID of the enterprise resource group. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=CreateLoadBalancer
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoadBalancerResponse>
    <NetworkType>vpc</NetworkType>
	  <LoadBalancerName>abc</LoadBalancerName>
	  <Address>192.168.0. **</Address>
	  <ResourceGroupId>rg-acfmxazb***</ResourceGroupId>
	  <RequestId>AB197CF0-D9E9-4475-A89D-35DBCCF13BBE</RequestId>
	  <AddressIPVersion>ipv4</AddressIPVersion>
	  <LoadBalancerId>lb-bp1b6c719dfa0***</LoadBalancerId>
	  <VSwitchId>vsw-bp12mw1f8k3jgygk9****</VSwitchId>
	  <VpcId>vpc-bp1aevy8sofi8mh1q***</VpcId>
</CreateLoadBalancerResponse>
```

`JSON` format

```
{
    "NetworkType": "vpc",
    "LoadBalancerName": "abc",
    "Address": "192.168.0. **",
    "ResourceGroupId": "rg-acfmxazb4ph****",
    "RequestId": "AB197CF0-D9E9-4475-A89D-35DBCCF13BBE",
    "AddressIPVersion": "ipv4",
    "LoadBalancerId": "lb-bp1b6c719dfa08ex****",
    "VSwitchId": "vsw-bp12mw1f8k3jgygk9****",
    "VpcId": "vpc-bp1aevy8sofi8mh1****"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

