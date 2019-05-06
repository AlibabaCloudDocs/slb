# DeleteRules {#doc_api_875532 .reference}

You can call the DeleteRules API to delete forwarding rules.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=DeleteRules) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|DeleteRules|The action to perform. Valid value: **DeleteRules**

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 You can call the [DescribeRegions](~~27584~~) API to query the region ID.

 |
|RuleIds|String|Yes|\["rule-bp1z9cee47oip","rule-bp1tucxr06qu4"\]|A list of the forwarding rules to be deleted

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteRules
&RegionId=cn-hangzhou
&RuleIds=["rule-bp1z9cee47oip","rule-bp1tucxr06qu4"]
&<CommonParameters>

```

Normal response examples

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

Abnormal response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

