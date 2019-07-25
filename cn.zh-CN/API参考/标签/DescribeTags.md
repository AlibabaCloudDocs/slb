# DescribeTags {#doc_api_Slb_DescribeTags .reference}

调用DescribeTags查询标签列表。

调用该接口时，请注意：

-   允许根据实例ID、Tagkey、Tagvalue等条件查询所有符合条件的Tags。
-   指定的条件为and关系，只有满足所有指定条件的TagSet才会被返回。
-   如果指定了Tagkey而没有指定Tagvalue，就查询所有该Tagkey关联的Tag。
-   不允许用户只指定Tagvalue而不指定Tagkey。
-   若指定了Tagkey/Tagvalue对，则精确匹配该Tag。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeTags&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeTags|要执行的操作。

 取值：**DescribeTags**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|DistinctKey|Boolean|否|false|是否为DistinctKey。

 取值：**true|false**。

 |
|LoadBalancerId|String|否|139a00604ad-cn-east-hangzhou-01|负载均衡实例ID。

 |
|PageNumber|Integer|否|1|实例列表页码，起始值1，默认值1。

 |
|PageSize|Integer|否|50|单页结果数量，接口默认50，最大100。

 |
|Tags|String|否|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]|要查询的标签列表。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|TagSets| | |Tag列表。

 |
|TagKey|String|test|标签Key。

 |
|TagValue|String|api|标签Value。

 |
|InstanceCount|Integer|10|该标签绑定的实例总数。

 |
|PageSize|Integer|50|默认50，最大100。

 |
|PageNumber|Integer|1|实例列表页码，起始值1，默认值1。

 |
|TotalCount|Integer|1|根据过滤条件得到的实例总个数。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeTags
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

