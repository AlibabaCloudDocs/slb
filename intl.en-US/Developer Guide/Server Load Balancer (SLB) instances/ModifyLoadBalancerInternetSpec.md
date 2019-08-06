# ModifyLoadBalancerInternetSpec {#doc_api_879498 .reference}

You can call the ModifyLoadBalancerInternetSpec API to modify the billing method for an Internet SLB instance.

-   Modify the peak bandwidth for an instance that is charged by bandwidth. The operation takes effect immediately after the modification.
-   Change the billing method from traffic-based billing to bandwidth-based billing. This operation takes effect from 00:00 the next day.
-   Change the billing method from bandwidth-based billing to traffic-based billing. This operation takes effect from 00:00 the next day.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInternetSpec) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|ModifyLoadBalancerInternetSpec| The action to perform. Valid value:**ModifyLoadBalancerInternetSpec**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08exfuca5| The ID of the SLB instance

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the SLB instance belongs.

 You can query the region ID by referring to the list of[regions and zones](~~40654~~), or by calling the[DescribeRegions](~~25609~~)API.

 |
|AutoPay|Boolean|No|false| Whether to automatically pay the bill of a Subscription Internet instance. Valid values:**true | false \(default value\)**.

 |
|Bandwidth|Integer|No|10| The peak bandwidth of an Internet instance that is billed by bandwidth.

 The listeners in this instance share the specified bandwidth. For more information, see[Share bandwidth](~~57846~~).

 Valid values: 1–5000 Mbit/s \(the peak bandwidth varies by region\).

 **Note:** This parameter is not required for the instance that is billed by traffic \(the value of the**InternetChargeType**parameter is**paybytraffic**\).

 |
|InternetChargeType|String|No|paybytraffic| The billing method of an Internet instance. Valid values:

 -   paybytraffic: billed by traffic

 **Note:** If you do not specify this parameter, the original billing method is maintained.

 |
|OwnerAccount|String|No|OwnerAccount| OwnerAccount

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|OrderId|Long|201429619788910| The order ID of a Subscription instance

 |
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyLoadBalancerInternetSpec
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&<CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyLoadBalancerInternetSpecResponse>
  <RequestId>E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED</RequestId>
</ModifyLoadBalancerInternetSpecResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED"
}
```

## Error codes {#section_vv7_vjk_1nq .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Operation.NotAllowed|Operation Denied. Unfinished order exists.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Prepay instance only permitted to modify internet bandwidth.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Prepay instance only permitted to increase internet bandwidth.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. The Purchase status of the instance is not valid.|The operation is not allowed. An unfinished purchase order exists.|

[Click here to view the error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

