# SetLoadBalancerModificationProtection

Enables or disables modification protection for a Server Load Balancer \(SLB\) instance.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerModificationProtection&type=RPC&version=2014-05-15)

## Request Parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetLoadBalancerModificationProtection|The operation that you want to perform. Set the value to**SetLoadBalancerModifyProtection**. |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08e\*\*\*\*\*|The ID of the SLB instance. |
|ModificationProtectionStatus|String|Yes|ConsoleProtection|The modification protection state of the SLB instance:

 -   **NonProtection**: disables modification protection. After you disable modification protection, the value of `ModificationProtectionReason` is cleared.
-   **ConsoleProtection**: enables modification protection. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is deployed.

 You can call the [DescribeRegions](~~27584~~) operation to query region IDs. |
|ModificationProtectionReason|String|No|Modify configurations|Enter the reason why you want to enable modification protection. The value must be 1 to 80 characters in length. It must start with a letter and can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\).

 **Note:** This parameter is required only when `ModificationProtectionStatus` is set to **ConsoleProtection**. |

## Response parameters

|Field|Type|Example|Description|
|-----|----|-------|-----------|
|RequestId|String|791D8B68-AE0F-4174-AF54-088C8B3C5D54|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=SetLoadBalancerModificationProtection
&LoadBalancerId=lb-bp1b6c719dfa08e*****
&ModificationProtectionStatus=ConsoleProtection
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
```

`JSON` format

```
{"RequestId":"791D8B68-AE0F-4174-AF54-088C8B3C5D54"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

