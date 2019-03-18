# DescribeServerCertificates {#doc_api_1088686 .reference}

使用DescribeServerCertificates查询指定地域的服务器证书列表。

**说明：** 为了保证安全性，只返回证书的指纹和名称，不返回证书和私钥的内容。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeServerCertificates)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeServerCertificates|要执行的操作，取值：**DescribeServerCertificates**

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|ResourceGroupId|String|否|rg-atstuj3rtoptyui|企业资源组ID。

 |
|ServerCertificateId|String|否|12315790xxxxxxx\_166f8204689\_1714763408\_709981430|服务器证书ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ServerCertificates| | |服务器证书列表。

 |
|└ServerCertificateId|String|123157xxxxxxxx\_166f8204689\_1714763408\_709981430-cn-east-hangzhou-02|服务器证书ID。

 |
|└ServerCertificateName|String|slb|服务器证书名称。

 |
|└RegionId|String|cn-hangzhou|服务器证书的地域。

 |
|└Fingerprint|String|68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d|服务器证书的指纹。

 |
|└AliCloudCertificateId|String|7309xxxxxxxx\_15d97e7709a\_71445759hr\_789289731|阿里云证书服务的服务器证书ID。

 |
|└AliCloudCertificateName|String|testcertkey|阿里云证书服务的服务器证书名称。

 |
|└CommonName|String|www.example.com|域名，对应证书的CommonName字段。

 |
|└CreateTime|String|2017-08-31T02:49:05Z|服务器证书上传的时间。

 |
|└CreateTimeStamp|Long|1504147745000|服务器证书上传的时间戳。

 |
|└ExpireTime|String|017-08-31T02:49:05Z|过期时间。

 |
|└ExpireTimeStamp|Long|15041477450|过期时间戳。

 |
|└IsAliCloudCertificate|Integer|0|是否是阿里云证书服务中的证书：

 -   **1**：是
-   **0**：不是

 |
|└ResourceGroupId|String|rg-atstuj3rtoptyui|企业资源组ID。

 |
|└SubjectAlternativeNames| |123|数组格式，返回证书的备用域名列表，对应证书的Subject Alternative Name字段。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeServerCertificates
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeServerCertificatesResponse>
  <RequestId>9FFF450B-CC09-4FFB-900F-E347EB7AA2CC</RequestId>
  <ServerCertificates>
    <ServerCertificate>
      <CreateTimeStamp>1541761156000</CreateTimeStamp>
      <CommonName>*.example1.com</CommonName>
      <RegionIdAlias>cn-hangzhou</RegionIdAlias>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <Fingerprint>68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d</Fingerprint>
      <ServerCertificateId>1231579xxxxxx_166f8204689_1714763408_709981430</ServerCertificateId>
      <ExpireTimeStamp>1558161264000</ExpireTimeStamp>
      <AliCloudCertificateId>1501739</AliCloudCertificateId>
      <ExpireTime>2019-05-18T06:34:24Z</ExpireTime>
      <RegionId>cn-hangzhou</RegionId>
      <CreateTime>2018-11-09T10:59:16Z</CreateTime>
      <ServerCertificateName>*.example1.com</ServerCertificateName>
      <IsAliCloudCertificate>1</IsAliCloudCertificate>
      <AliCloudCertificateName>slb</AliCloudCertificateName>
    </ServerCertificate>
    <ServerCertificate>
      <CreateTimeStamp>1481623069000</CreateTimeStamp>
      <RegionIdAlias>cn-hangzhou</RegionIdAlias>
      <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
      <Fingerprint>cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d</Fingerprint>
      <ServerCertificateId>1231579085529123_158f79de306</ServerCertificateId>
      <ExpireTimeStamp>1732169065000</ExpireTimeStamp>
      <AliCloudCertificateId>0</AliCloudCertificateId>
      <ExpireTime>2024-11-21T06:04:25Z</ExpireTime>
      <RegionId>cn-hangzhou</RegionId>
      <CreateTime>2016-12-13T09:57:49Z</CreateTime>
      <ServerCertificateName>test_certificate</ServerCertificateName>
      <IsAliCloudCertificate>0</IsAliCloudCertificate>
      <AliCloudCertificateName/>
    </ServerCertificate>
  </ServerCertificates>
</DescribeServerCertificatesResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9FFF450B-CC09-4FFB-900F-E347EB7AA2CC",
	"ServerCertificates":{
		"ServerCertificate":[
			{
				"CreateTimeStamp":1541761156000,
				"CommonName":"*.example1.com",
				"RegionIdAlias":"cn-hangzhou",
				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
				"Fingerprint":"68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d",
				"ServerCertificateId":"1231579xxxxxxx_166f8204689_1714763408_709981430",
				"ExpireTimeStamp":1558161264000,
				"AliCloudCertificateId":"1501739",
				"ExpireTime":"2019-05-18T06:34:24Z",
				"RegionId":"cn-hangzhou",
				"CreateTime":"2018-11-09T10:59:16Z",
				"ServerCertificateName":"*.example1.com",
				"IsAliCloudCertificate":1,
				"AliCloudCertificateName":"slb"
			},
			{
				"CreateTimeStamp":1481623069000,
				"RegionIdAlias":"cn-hangzhou",
				"ResourceGroupId":"rg-acfmxazb4ph6aiy",
				"Fingerprint":"cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d",
				"ServerCertificateId":"1231579085529123_158f79de306",
				"ExpireTimeStamp":1732169065000,
				"AliCloudCertificateId":"0",
				"ExpireTime":"2024-11-21T06:04:25Z",
				"RegionId":"cn-hangzhou",
				"CreateTime":"2016-12-13T09:57:49Z",
				"ServerCertificateName":"test_certificate",
				"IsAliCloudCertificate":0,
				"AliCloudCertificateName":""
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

