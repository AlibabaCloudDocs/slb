# UploadServerCertificate {#doc_api_890447 .reference}

You can call the UploadServerCertificate API to upload a server certificate.

This transactional API allows you to upload only one server certificate and corresponding private key at a time.

This means that the server certificate and the private key must both be uploaded successfully. Otherwise, the upload fails. After the certificate and private key are successfully uploaded, the fingerprints of all server certificates under your account are returned.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=UploadServerCertificate) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|UploadServerCertificate|The action to perform. Valid value: **UploadServerCertificate**

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the server certificate belongs.

 You can query the region ID by calling the [DescribeRegions](~~27584~~) API.

 |
|AliCloudCertificateId|String|No|7309126735407682\_15d97e7709a\_71445759hr\_789289731|The certificate ID from the Alibaba Cloud SSL Certificates Service.

 This parameter is required if you use a certificate from the Alibaba Cloud SSL Certificates Service.

 |
|AliCloudCertificateName|String|No|testcertkey|The certificate name from the Alibaba Cloud SSL Certificates Service

 |
|PrivateKey|String|No|wmsad! q23|The private key to be uploaded

 |
|ResourceGroupId|String|No|rg-atstuj3rtoptyui|The ID of the enterprise resource group

 |
|ServerCertificate|String|No|test|The public key certificate to be uploaded

 |
|ServerCertificateName|String|No|mycert01|The name of the server certificate to be uploaded

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|ServerCertificateId|String|idkp-123-cn-test-01|The ID of the server certificate

 |
|ServerCertificateName|String|mycert01|The name of the server certificate

 |
|Fingerprint|String|01:DF:AB:CD|The fingerprint of the server certificate

 |
|AliCloudCertificateId|String|7309126735407682\_15d97e7709a\_71445759hr\_789289731|The server certificate ID from the Alibaba Cloud SSL Certificate Service

 |
|AliCloudCertificateName|String|testcertkey|The server certificate name from the Alibaba Cloud SSL Certificate Service

 |
|CommonName|String|test|The domain name that corresponds to the common name field of the certificate

 |
|CreateTime|String|2017-08-31T02:49:05Z|The time at which the certificate is created

 |
|CreateTimeStamp|Long|1504147745000|The timestamp that indicates when the certificate is created

 |
|ExpireTime|String|1504147745000|The time at which the certificate expires

 |
|ExpireTimeStamp|Long|1504147745000|The timestamp that indicates when the certificate expires

 |
|IsAliCloudCertificate|Integer|0|Whether or not the certificate is from the Alibaba Cloud SSL Certificate Service.

 -   0: No
-   1: Yes

 |
|RegionId|String|cn-hangzhou|The ID of the region to which the certificate belongs

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui|The ID of the enterprise resource group

 |
|SubjectAlternativeNames| |test|A list of alternate domain names for the certificate is returned in array format.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=UploadServerCertificate
&RegionId=cn-hangzhou
&<CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<UploadServerCertificateResponse>
  <CommonName>*.example1.com</CommonName>
  <RegionIdAlias>cn-hangzhou</RegionIdAlias>
  <ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
  <Fingerprint>68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d</Fingerprint>
  <ServerCertificateId>123157908552****_166f8204689_1714763408_709981430</ServerCertificateId>
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

`JSON` format

``` {#json_return_success_demo}
{
	"CommonName":"*.example1.com",
	"RegionIdAlias":"cn-hangzhou",
	"ResourceGroupId":"rg-acfmxazb4ph6aiy",
	"Fingerprint":"68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d",
	"ServerCertificateId":"123157908552****_166f8204689_1714763408_709981430",
	"ExpireTimeStamp":1558161264000,
	"AliCloudCertificateId":"1501739",
	"ExpireTime":"2019-05-18T06:34:24Z",
	"RegionId":"cn-hangzhou",
	"RequestId":"C87620A7-3608-48D0-BC41-A83FB4FF0EC6",
	"ServerCertificateName":"*.example1.com",
	"IsAliCloudCertificate":1,
	"AliCloudCertificateName":"slb"
}
```

## Error codes { .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|InvalidParameter|The specified ServerCertificate and PrivateKey fail to validate.|The parameter Bandwidth is invalid. Please check that the parameter is correct.|

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

