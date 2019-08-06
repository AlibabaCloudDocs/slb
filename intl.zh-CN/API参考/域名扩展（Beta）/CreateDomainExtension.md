# CreateDomainExtension {#doc_api_Slb_CreateDomainExtension .reference}

调用CreateDomainExtension创建扩展域名。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateDomainExtension&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateDomainExtension|要执行的操作。

 取值：**CreateDomainExtension**。

 |
|Domain|String|是|\*.example1.com|域名。

 |
|ListenerPort|Integer|是|443|负载均衡实例HTTPS监听的前端端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp1o94dp5i6earrxxxxxx|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|ServerCertificateId|String|是|123157xxxxxxx\_166f820xxxxxx\_1714763408\_709981xxxx|与域名对应的证书ID。

 |

## 返回数据 {#resultMapping .section}

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
<CreateDomainExtensionResponse>
	  <RequestId>A6E7EFC9-0938-40CA-877D-9BEDBD21D357</RequestId>
	  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
	  <ListenerPort>443</ListenerPort>
</CreateDomainExtensionResponse>
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

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

