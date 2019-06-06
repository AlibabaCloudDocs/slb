# UploadServerCertificate {#doc_api_Slb_UploadServerCertificate .reference}

调用UploadServerCertificate上传服务器证书。

一次只能上传一份服务器证书和对应的私钥。

该接口保证事务性，即上传的证书和私钥要么都上传成功，要么都不成功。上传成功后，返回该用户的所有服务器证书列表的Fingerprint。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=UploadServerCertificate)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|UploadServerCertificate|要执行的操作。取值：**UploadServerCertificate**

 |
|RegionId|String|是|cn-hangzhou|服务器证书的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|AliCloudCertificateId|String|否|730912673xxxxxx\_15d97e7709a\_71445759hr\_789289731|阿里云的云上证书ID。

 使用阿里云的云上证书，该参数必选。

 |
|AliCloudCertificateName|String|否|testcertkey|阿里云的云上证书名称。

 |
|PrivateKey|String|否|wmsad!q23|需要上传的私钥。

 |
|ResourceGroupId|String|否|rg-atstuj3rto\*\*\*\*|企业资源组ID。

 |
|ServerCertificate|String|否|test|要上传的公钥证书。

 |
|ServerCertificateName|String|否|mycert01|要上传的服务器证书的名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ServerCertificateId|String|xxxxidkp-123-cn-test-01|服务器证书ID。

 |
|ServerCertificateName|String|mycert01|服务器证书名称。

 |
|Fingerprint|String|01:DF:AB:CD|服务器证书的指纹。

 |
|AliCloudCertificateId|String|730912xxxxx\_15d97e7709a\_71445759hr\_789289731|阿里云证书服务中的服务器证书ID。

 |
|AliCloudCertificateName|String|testcertkey|阿里云证书服务中的服务器证书名称。

 |
|CommonName|String|test|域名，对应证书的Common Name字段。

 |
|CreateTime|String|2017-08-31T02:49:05Z|证书创建时间。

 |
|CreateTimeStamp|Long|1504147745000|证书创建时间戳。

 |
|ExpireTime|String|1504147745000|证书过期时间。

 |
|ExpireTimeStamp|Long|1504147745000|证书过期时间戳。

 |
|IsAliCloudCertificate|Integer|0|是否为阿里云证书服务中的证书。

 -   0：表示不是阿里云证书。
-   1：表示是阿里云证书。

 |
|RegionId|String|cn-hangzhou|证书所属的地域ID。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |
|SubjectAlternativeNames| |test|数组格式，返回证书的备用域名列表。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=UploadServerCertificate
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<UploadServerCertificateResponse>
  <CommonName>*.example1.com</CommonName>
  <RegionIdAlias>cn-hangzhou</RegionIdAlias>
  <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
  <Fingerprint>68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d</Fingerprint>
  <ServerCertificateId>12315790xxxxxxxx3_166f8204689_1714763408_709981430</ServerCertificateId>
  <ExpireTimeStamp>1558161264000</ExpireTimeStamp>
  <AliCloudCertificateId>1501739</AliCloudCertificateId>
  <ExpireTime>2019-05-18T06:34:24Z</ExpireTime>
  <RegionId>cn-hangzhou</RegionId>
  <RequestId>C87620A7-3608-48D0-BC41-A83FB4FF0EC6</RequestId>
  <ServerCertificateName>*.example1.com</ServerCertificateName>
  <IsAliCloudCertificate>1</IsAliCloudCertificate>
  <AliCloudCertificateName>slb</AliCloudCertificateName>
</UploadServerCertificateResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ServerCertificateId":"12315790xxxxxxxx3_166f8204689_1714763408_70998143",
	"CommonName":"*.example1.com",
	"RegionIdAlias":"cn-hangzhou",
	"AliCloudCertificateId":"1501739",
	"ExpireTime":"2019-05-18T06:34:24Z",
	"RequestId":"C87620A7-3608-48D0-BC41-A83FB4FF0EC6",
	"RegionId":"cn-hangzhou",
	"ResourceGroupId":"rg-acfmxazb4ph6aiy",
	"ServerCertificateName":"*.example1.com",
	"IsAliCloudCertificate":1,
	"AliCloudCertificateName":"slb",
	"Fingerprint":"68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

