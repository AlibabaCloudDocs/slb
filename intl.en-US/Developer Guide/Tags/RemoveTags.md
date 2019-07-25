# RemoveTags {#doc_api_Slb_RemoveTags .reference}

Remove tags of an SLB instance.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=RemoveTags) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveTags| The name of this action.

 Value: **RemoveTags**

 |
|LoadBalancerId|String|Yes|139a00604ad-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |
|Tags|String|Yes|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]| A list of tags to be removed.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=RemoveTags
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&RegionId=cn-hangzhou
&Tags=[{"TagKey":"Key1","TagValue":"Value1"}{"TagKey":"Key2","TagValue":"Value2"}]
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<RemoveTagsResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
</RemoveTagsResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
}
```

## Error codes {#section_120_2z2_fds .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

