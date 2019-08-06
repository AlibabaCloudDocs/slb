# ModifyLoadBalancerPayType {#doc_api_837690 .reference}

Converts a Pay-As-You-Go instance to a Subscription instance.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerPayType) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyLoadBalancerPayType| The name of this action. Value: **ModifyLoadBalancerPayType**

 |
|Duration|Integer|Yes|1| The billing duration.

 -   If the value of **PricingCycle** is **month**, the valid values for this parameter are **1 to 9**.
-   If the value of **PricingCycle** is **year**, the valid values for this parameter are **1 to 3**.

 |
|LoadBalancerId|String|Yes|lb-test| The ID of the SLB instance.

 |
|PayType|String|Yes|PrePay| The billing method of the instance. Valid values:

 -   **PayOnDemand**: Pay-As-You-Go

 |
|PricingCycle|String|Yes|month| The billing cycle. Valid values:**year | month**.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the SLB instance belongs.

 You can query the region ID by referring to the list of[regions and zones](~~40654~~)or by calling the[DescribeRegions](~~25609~~)API.

 |
|AutoPay|Boolean|No|true| Whether to pay automatically. Valid values:**true | false**.

 -   **true**: Pay automatically.
-   **false \(default value\)**: Do not pay automatically.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request

 |
|OrderId|Long|201429619788910| The order ID of a Subscription instance

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=ModifyLoadBalancerPayType
&LoadBalancerId=lb-test
&RegionId=cn-hangzhou
& <CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyLoadBalancerPayType>
  <RequestId>B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8</RequestId>
  <OrderId>202778336800296</OrderId>
</ModifyLoadBalancerPayType>

```

`JSON` format

``` {#json_return_success_demo}
{
	"OrderId":202778336800296,
	"RequestId":"B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8"
}
```

Error response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"cdn.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## Error codes {#section_suf_nbb_ibm .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Operation.NotAllowed|Cannot change internet payByTraffic loadBalancer from PayOnDemand to PrePay.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Only allow changing loadBalancer from PayOnDemand to PrePay.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Unfinished order exists.|The operation is not allowed. An unfinished purchase order exists.|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|The operation is not allowed. An unfinished purchase order exists.|

[Click here to view the error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

