# RemoveTags {#doc_api_834936 .reference}

使用RemoveTags解绑指定负载均衡实例下的标签。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=RemoveTags)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveTags|要执行的操作。取值：**RemoveTags**

 |
|LoadBalancerId|String|是|139a00604ad-cn-east-hangzhou-01|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|Tags|String|是|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]|需要解绑的Tag列表。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=RemoveTags
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&RegionId=cn-hangzhou
&Tags=[{"TagKey":"Key1","TagValue":"Value1"}{"TagKey":"Key2","TagValue":"Value2"}]
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveTagsResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
</RemoveTagsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
}
```

异常返回示例

`JSON` 格式

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

