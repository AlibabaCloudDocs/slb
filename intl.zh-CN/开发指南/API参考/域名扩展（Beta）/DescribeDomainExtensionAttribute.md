# DescribeDomainExtensionAttribute

调用DescribeDomainExtensionAttribute查询已添加的扩展域名属性。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeDomainExtensionAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeDomainExtensionAttribute|要执行的操作。取值：**DescribeDomainExtensionAttribute**。 |
|DomainExtensionId|String|是|de-bp1rp7ta191dv|扩展域名ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Domain|String|www.example.com|域名。 |
|DomainExtensionId|String|de-bp1rp7ta191dv|扩展域名ID。 |
|ListenerPort|Integer|443|负载均衡实例HTTPS监听的前端端口，取值：**1**~**65535**。 |
|LoadBalancerId|String|lb-bp1o94dp5i6\*\*\*\*\*earr9g6d1l|负载均衡实例ID。 |
|RequestId|String|48C1B671-C6DB-4DDE-9B30-10557E36CDE0|请求ID。 |
|ServerCertificateId|String|231579085529123\_166f82\*\*\*\*\*\*\_1714763408\_709981430|域名使用的服务器证书ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeDomainExtensionAttribute
&DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeDomainExtensionAttributeResponse>
  <ListenerPort>443</ListenerPort>
  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
  <RequestId>48C1B671-C6DB-4DDE-9B30-10557E36CDE0</RequestId>
  <ServerCertificateId>231579085529123_166f82******_1714763408_709981430</ServerCertificateId>
  <LoadBalancerId>lb-bp1o94dp5i6*****earr9g6d1l</LoadBalancerId>
  <Domain>www.example.com</Domain>
</DescribeDomainExtensionAttributeResponse>
```

`JSON` 格式

```
{"ListenerPort":"443",
"DomainExtensionId":"de-bp1rp7ta191dv",
"RequestId":"48C1B671-C6DB-4DDE-9B30-10557E36CDE0",
"ServerCertificateId":"231579085529123_166f82******_1714763408_709981430",
"LoadBalancerId":"lb-bp1o94dp5i6*****earr9g6d1l",
"Domain":"www.example.com"}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

