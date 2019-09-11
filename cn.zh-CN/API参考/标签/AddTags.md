# AddTags {#doc_api_Slb_AddTags .reference}

调用AddTags为指定的负载均衡实例添加标签。

为指定的负载均衡实例添加标签。

调用该接口时，请注意：

-   每个负载均衡实例最多可绑定10个Tag。
-   单次绑定的标签数最多为5对。
-   一个负载均衡实例下的所有Tag和Key不能重复。
-   当添加的标签与原有标签Key相同，但Value不同时，则覆盖原有的标签。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=AddTags&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddTags|要执行的操作。

 取值：**AddTags**。

 |
|LoadBalancerId|String|是|139a00604ad-cn-east-hangzhou-|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|Tags|String|是|\[\{"TagKey":"Key1","TagValue":"Value1"\}\{"TagKey":"Key2","TagValue":"Value2"\}\]|需要添加的Tag列表。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddTags
&LoadBalancerId=139a00604ad-cn-east-hangzhou-
&RegionId=cn-hangzhou
&Tags=[{"TagKey":"Key1","TagValue":"Value1"}{"TagKey":"Key2","TagValue":"Value2"}]
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddTagsResponse>
	  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
</AddTagsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

