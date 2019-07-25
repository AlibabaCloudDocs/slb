# DescribeTags {#doc_api_Slb_DescribeTags .reference}

Queries details of specified tags.

Before you call this API, note the following:

-   You can use the SLB instance ID, TagKey, or TagValue to search for tags that meet your search conditions.
-   The relationship between the conditions is "AND". Only tags that meet all the specified conditions will be returned.
-   If you specify a TagKey without specifying a TagValue, all tags associated with the TagKey will be queried.
-   A TagValue must be specified with a TagKey. However, a TagKey can be specified without a TagValue.
-   If a TagKey/TagValue pair is specified, then exact matching is performed.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeTags) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeTags| The name of this action.

 Value: **DescribeTags**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|DistinctKey|Boolean|No|false| Optional. Indicates whether it is DistinctKey.

 Valid values: **true | false**

 |
|LoadBalancerId|String|No|139a00604ad-cn-east-hangzhou-01| Optional. The ID of the SLB instance.

 |
|PageNumber|Integer|No|1| Optional. The page number of the SLB instance list. Initial value: 1. Default value: 1

 |
|PageSize|Integer|No|50| Optional. The number of results per page. Default value: 50. Maximum value: 100

 |
|Tags|String|No|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]| Optional. A list of tags to query.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|TagSets| | | The list of tags.

 |
|└TagKey|String|test| The tag key.

 |
|└TagValue|String|api| The tag value.

 |
|└InstanceCount|Integer|10| The total number of SLB instances with which the tag is associated.

 |
|PageSize|Integer|50| Default value: 50. Maximum value: 100

 |
|PageNumber|Integer|1| The page number of the tag list. Initial value: 1. Default value: 1

 |
|TotalCount|Integer|1| The total number of tags that meet your search conditions.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeTags
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeTagsResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <TagSets>
    <TagSet>
      <TagKey>test</TagKey>
      <TagValue>api</TagValue>
    </TagSet>
  </TagSets>
  <PageSize>50</PageSize>
  <PageNumber>1</PageNumber>
  <TotalCount>1</TotalCount>
</DescribeTagsResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"TagSets":{
		"PageNumber":1,
		"TotalCount":1,
		"PageSize":50,
		"TagSet":[
			{
				"TagValue":"api",
				"TagKey":"test"
			}
		]
	}
}
```

## Error codes {#section_zkr_r4r_vme .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

