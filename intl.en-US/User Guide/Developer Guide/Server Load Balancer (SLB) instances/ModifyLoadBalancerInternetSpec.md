# ModifyLoadBalancerInternetSpec

Changes the billing method of a public-facing Server Load Balancer \(SLB\) instance.

-   If you change the maximum bandwidth of a pay-by-bandwidth SLB instance, the change immediately takes effect.
-   If you change the billing method of an SLB instance from pay-by-data-transfer to pay-by-bandwidth, the new billing method takes effect at 00:00 the following day.
-   If you change the billing method of an SLB instance from pay-by-bandwidth to pay-by-data-transfer, the new billing method takes effect at 00:00 the following day.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInternetSpec&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyLoadBalancerInternetSpec|The operation that you want to perform.

 Set the value to **ModifyLoadBalancerInternetSpec**. |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08ex\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created.

 You can query the region ID from the [Regions and zones](~~40654~~) list or by calling the [DescribeRegions](~~25609~~) operation. |
|InternetChargeType|String|No|paybytraffic|The billing method of the public-facing SLB instance Set the value to paybytraffic.

 -   paybytraffic: You are charged on a pay-by-data-transfer basis.

 **Note:** If this parameter is not set, the billing method of the SLB instance remains unchanged. |
|Bandwidth|Integer|No|10|The maximum bandwidth of the public-facing SLB instance that is billed on a pay-by-bandwidth basis. Unit: Mbit/s.

 Valid values: 1 to 5000. The maximum bandwidth varies based on the region of the SLB instance.

 **Note:** You do not need to set this parameter for pay-by-data-transfer SLB instances. The value of **InternetChargeType** is **paybytraffic**. |
|AutoPay|Boolean|No|false|Specifies whether to automatically pay for public-facing SLB instances that are billed on a subscription basis.

 Valid values: **true and false**. Default value: false. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |
|OrderId|Long|201429619788910|The order ID of the subscription SLB instance. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=ModifyLoadBalancerInternetSpec
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyLoadBalancerInternetSpecResponse>
      <RequestId>E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED</RequestId>
</ModifyLoadBalancerInternetSpecResponse>
```

`JSON` format

```
{
    "RequestId": "E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|The error message returned because a pending order exists.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

