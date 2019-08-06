# AddTags {#doc_api_Slb_AddTags .reference}

Adds tags to an SLB instance.

Limits

Before you call this API, note the following limits:

-   You can add up to 10 tags to each SLB instance.
-   You can add up to five pairs of tags at a time.
-   All the tags and keys added to an SLB instance must be unique.
-   If you add a tag of which the key is the same as that of an existing tag, but the value is different, the new tag overwrites the existing one.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddTags) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddTags| The name of this action.

 Value: **AddTags**

 |
|LoadBalancerId|String|Yes|139a00604ad-cn-east-hangzhou-| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|Tags|String|Yes|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]| A list of tags to be added.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=AddTags
&LoadBalancerId=139a00604ad-cn-east-hangzhou-
&RegionId=cn-hangzhou
&Tags=[{"TagKey":"Key1","TagValue":"Value1"}{"TagKey":"Key2","TagValue":"Value2"}]
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<AddTagsResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
</AddTagsResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
}
```

## Error codes {#section_l35_eyq_fs8 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

