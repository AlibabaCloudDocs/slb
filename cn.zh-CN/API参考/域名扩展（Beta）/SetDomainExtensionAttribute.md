# SetDomainExtensionAttribute {#doc_api_Slb_SetDomainExtensionAttribute .reference}

调用SetDomainExtensionAttribute修改扩展域名的证书。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetDomainExtensionAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetDomainExtensionAttribute|要执行的操作。

 取值：**SetDomainExtensionAttribute**。

 |
|DomainExtensionId|String|是|de-bp1rp7ta191dv|要修改的扩展域名ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡示例的地域ID。

 |
|ServerCertificateId|String|是|1231579xxxxxxxx\_166f8204689\_1714763408\_709981xxx|新的证书ID。

 |

## 返回数据 {#resultMapping .section}

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

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

