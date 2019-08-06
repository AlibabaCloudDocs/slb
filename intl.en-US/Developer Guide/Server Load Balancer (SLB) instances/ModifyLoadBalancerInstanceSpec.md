# ModifyLoadBalancerInstanceSpec {#doc_api_880395 .reference}

Modifies the specification of an SLB instance.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInstanceSpec) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyLoadBalancerInstanceSpec| The name of this action. Value:**ModifyLoadBalancerInstanceSpec**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08exfuca5| The ID of the SLB instance.

 |
|LoadBalancerSpec|String|Yes|slb.s2.small| The specification of the SLB instance. Valid values:

 -   slb.s1.small
-   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

Available specifications may vary according to the region. For more information, see [Guaranteed-performance instance](~~27657~~).

 **Note:** When you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds. We recommend that you perform this operation during off-peak traffic hours, or use GSLB to schedule the service to other SLB instances first.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the SLB instance belongs.

 To query the region ID, refer to the list of[regions and zones](~~40654~~) or call the [DescribeRegions](~~25609~~) API.

 |
|AutoPay|Boolean|No|true| Indicates whether to pay automatically.

 -   If the value is **true**, the order is automatically paid.
-   If the value is **false**, you need to pay the order in the Billing console.

 **Note:** This parameter only applies to Subscription instances.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|OrderId|Long|201429619788910| The order ID of a Subscription instance.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyLoadBalancerInstanceSpec
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&LoadBalancerSpec=slb.s2.small
&<CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyLoadBalancerInstanceSpecResponse>
  <RequestId>D456A34A-6E40-4379-8DAF-9175760FE215</RequestId>
</ModifyLoadBalancerInstanceSpecResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"D456A34A-6E40-4379-8DAF-9175760FE215"
}
```

Error response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## Error codes {#section_md5_vl6_eoo .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|ModifySpecNotAllowed|LoadBalancerSpec not allowed for this instance|This specification is not supported by this instance.|
|400|ModifySpecNotAllowed|LoadBalancerSpec not allowed for this instance|This specification is not supported by this instance.|
|400|Operation.NotAllowed|Operation Denied. Unfinished order exists.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Prepay instance only permitted to increase loadBalancerSpec.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. The Purchase status of the instance is not valid.|The operation is not allowed. An unfinished purchase order exists.|

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

