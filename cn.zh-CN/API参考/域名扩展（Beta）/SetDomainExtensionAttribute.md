# SetDomainExtensionAttribute {#doc_api_Slb_SetDomainExtensionAttribute .reference}

调用SetDomainExtensionAttribute修改扩展域名的证书。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetDomainExtensionAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetDomainExtensionAttribute|要执行的操作。取值：**SetDomainExtensionAttribute**

 |
|DomainExtensionId|String|是|de-bp1rp7ta191dv|要修改的扩展域名ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡示例的地域ID。

 |
|ServerCertificateId|String|是|1231579xxxxxxxx\_166f8204689\_1714763408\_709981xxx|新的证书ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetDomainExtensionAttribute
&DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&ServerCertificateId=1231579xxxxxxxx_166f8204689_1714763408_709981xxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetDomainExtensionAttributeResponse>
  <RequestId>149A2470-F010-4437-BF68-xxxxx</RequestId>
</SetDomainExtensionAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"B1435A8D-5AE2-4EB2-9590-xxxxxx"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

