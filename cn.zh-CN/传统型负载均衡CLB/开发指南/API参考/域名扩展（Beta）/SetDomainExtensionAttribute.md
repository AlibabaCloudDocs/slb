# SetDomainExtensionAttribute

调用SetDomainExtensionAttribute修改扩展域名的证书。

**说明：** 性能共享型实例的监听不支持扩展域名。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetDomainExtensionAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetDomainExtensionAttribute|要执行的操作。

 取值：**SetDomainExtensionAttribute**。 |
|DomainExtensionId|String|是|de-bp1rp7ta\*\*\*\*\*|需要修改的扩展域名ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|ServerCertificateId|String|是|1231579xxxxxxxx\_166f8204689\_1714763408\_709981xxx|新的证书ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetDomainExtensionAttribute
&DomainExtensionId=de-bp1rp7ta*****
&RegionId=cn-hangzhou
&ServerCertificateId=1231579xxxxxxxx_166f8204689_1714763408_709981xxx
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<SetDomainExtensionAttributeResponse>
    <RequestId>149A2470-F010-4437-BF68-xxxxx</RequestId>
</SetDomainExtensionAttributeResponse>
```

`JSON`格式

```
{
    "RequestId": "B1435A8D-5AE2-4EB2-9590-xxxxxx"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

