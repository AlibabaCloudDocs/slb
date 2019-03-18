# DeleteDomainExtension {#doc_api_880890 .reference}

使用DeleteDomainExtension删除扩展域名。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=DeleteDomainExtension)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteDomainExtension|要执行的操作，取值：**DeleteDomainExtension**

 |
|DomainExtensionId|String|是|de-bp1rp7ta191dv|要删除的扩展域名ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡示例的地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&Action=DeleteDomainExtension
&Tags={"tagKey":"Key1","tagValue":"Value1"}
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteDomainExtensionResponse>
  <RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
</DeleteDomainExtensionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"5B45BED9-4D41-47B0-ADD6-47A5624516C7"
}
```

异常返回示例

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

