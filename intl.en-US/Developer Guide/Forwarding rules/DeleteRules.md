# DeleteRules {#doc_api_Slb_DeleteRules .reference}

Deletes one or more forwarding rules.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteRules) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteRules| The name of this action.

 Value: **DeleteRules**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|RuleIds|String|Yes|\["rule-bp1z9cee47oip","rule-bp1tucxr06qu4"\]| A list of the forwarding rules to be deleted

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteRules
&RegionId=cn-hangzhou
&RuleIds=["rule-bp1z9cee47oip","rule-bp1tucxr06qu4"]
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteRulesResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteRulesResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Error codes {#section_73k_ez3_zle .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

