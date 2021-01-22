# DeleteRules

Deletes one or more forwarding rules.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DeleteRules&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteRules|The name of this action.

 Value: **DeleteRules** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the Server Load Balancer \(SLB\) instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~). |
|RuleIds|String|Yes|\["rule-bp1z9ce\*\*\*\*\*\*","rule-bp1tuc\*\*\*\*\*\*4"\]|The list of the forwarding rules that you want to delete. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DeleteRules
&RegionId=cn-hangzhou
&RuleIds=["rule-bp1z9ce******","rule-bp1tuc******4"]
&<CommonParameters>

```

Response example

`XML` format

```
<DeleteRulesResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteRulesResponse>
```

`JSON` format

```
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

