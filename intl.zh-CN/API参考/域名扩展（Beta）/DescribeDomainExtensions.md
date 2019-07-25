# DescribeDomainExtensions {#doc_api_Slb_DescribeDomainExtensions .reference}

调用DescribeDomainExtensions查询已添加的扩展域名。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeDomainExtensions&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDomainExtensions|要执行的操作。

 取值：**DescribeDomainExtensions**。

 |
|ListenerPort|Integer|是|443|负载均衡实例HTTPS监听的前端端口，取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp1o94dp5i6earr9g6d1l|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|DomainExtensionId|String|否|de-bp1rp7ta191dv|扩展域名ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainExtensions| | |扩展域名列表。

 |
|Domain|String|www.example.com|域名。

 |
|DomainExtensionId|String|de-bp1rp7ta191dv|扩展域名ID。

 |
|ServerCertificateId|String|1231579085529123\_166f8204689\_1714763408\_709981430|域名使用的证书ID。

 |
|RequestId|String|48C1B671-C6DB-4DDE-9B30-10557E36CDE0|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeDomainExtensions
&ListenerPort=443
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDomainExtensionsResponse>
	  <RequestId>CCC710F8-285C-415F-9211-9BD6BF7BB997</RequestId>
	  <DomainExtensions>
		    <DomainExtension>
			      <ServerCertificateId>123157908xxxxxx_166f8204689_1714763408_70xxx</ServerCertificateId>
			      <Domain>*.example2.com</Domain>
			      <DomainExtensionId>de-bp1k4chwdnhxd</DomainExtensionId>
		    </DomainExtension>
	  </DomainExtensions>
</DescribeDomainExtensionsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"48C1B671-C6DB-4DDE-9B30-10557E36CDE0",
	"DomainExtensions":{
		"DomainExtension":[
			{
				"ServerCertificateId":"123157908xxxxxx_166f8204689_1714763408_70xxx",
				"Domain":"*.example1.com",
				"DomainExtensionId":"de-bp1rp7ta191dv"
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

