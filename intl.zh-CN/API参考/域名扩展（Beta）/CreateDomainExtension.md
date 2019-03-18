# CreateDomainExtension {#doc_api_1088675 .reference}

使用CreateDomainExtension创建扩展域名。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=CreateDomainExtension)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateDomainExtension|要执行的操作。取值：**CreateDomainExtension**

 |
|Domain|String|是|\*.example1.com|域名。

 |
|ListenerPort|Integer|是|443|负载均衡实例HTTPS监听的前端端口，取值：**1-65535**

 |
|LoadBalancerId|String|是|lb-bp1o94dp5i6earrxxxxxx|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|ServerCertificateId|String|是|123157xxxxxxx\_166f820xxxxxx\_1714763408\_709981xxxx|与域名对应的证书ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DomainExtensionId|String|de-bp1rp7ta19xxxx|创建的扩展域名ID。

 |
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。

 |
|RequestId|String|A6E7EFC9-0938-40CA-877D-9BEDBD21D357|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateDomainExtension
&Domain=*.example1.com
&ListenerPort=443
&LoadBalancerId=lb-bp1o94dp5i6earrxxxxxx
&RegionId=cn-hangzhou
&ServerCertificateId=123157xxxxxxx_166f820xxxxxx_1714763408_709981xxxx
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateDomainExtension>
  <RequestId>A6E7EFC9-0938-40CA-877D-9BEDBD21D357</RequestId>
  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
  <ListenerPort>443</ListenerPort>
</CreateDomainExtension>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A6E7EFC9-0938-40CA-877D-9BEDBD21D357",
	"DomainExtensionId":"de-bp1rp7ta191dv",
	"ListenerPort":443
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

