# UploadCACertificate {#doc_api_Slb_UploadCACertificate .reference}

调用UploadCACertificate上传CA证书。

一次只能上传一份CA证书内容。添加成功后，返回该用户的该证书的ID、名称和指纹。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=UploadCACertificate)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UploadCACertificate|要执行的操作。

 取值：**UploadCACertificate**。

 |
|RegionId|String|是|cn-hangzhou|CA证书的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|CACertificate|String|是|test|要上传CA证书的内容。

 |
|CACertificateName|String|否|mycacert01|CA证书名称。

 |
|ResourceGroupId|String|否|rg-atstuj3rtoptyui|企业资源组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|CACertificateId|String|139a00604ad-cn-east-hangzhou-01|CA证书ID。

 |
|CACertificateName|String|mycacert01|CA证书的名称。

 |
|Fingerprint|String|02:DF:AB:ED|CA证书的指纹。

 |
|CommonName|String|.example.com|CA证书的域名。

 |
|CreateTime|String|2017-08-31T02:49:05Z|CA证书上传的时间。

 |
|CreateTimeStamp|Long|1504147745000|CA证书上传的时间戳。

 |
|ExpireTime|String|2024-11-21T06:04:25Z|CA证书的过期时间。

 |
|ExpireTimeStamp|Long|1732169065000|CA证书的过期时间戳。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=UploadCACertificate
&RegionId=cn-hangzhou
&CACertificate=test
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UploadCACertificateResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <ServerCertificateId>idkp-234-cn-test-02</ServerCertificateId>
  <ServerCertificateName>mycacert01</ServerCertificateName>
  <Fingerprint>02:DF:AB:ED</Fingerprint>
</UploadCACertificateResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ServerCertificateId":"idkp-234-cn-test-02",
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"ServerCertificateName":"mycacert01",
	"Fingerprint":"02:DF:AB:ED"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

