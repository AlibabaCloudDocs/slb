# UploadServerCertificate {#doc_api_Slb_UploadServerCertificate .reference}

Uploads a server certificate.

This transactional API allows you to upload only one server certificate and corresponding private key at a time.

This means that the server certificate and the private key must both be uploaded successfully. Otherwise, the upload fails. After the certificate and private key are successfully uploaded, the fingerprints of all server certificates under your account are returned.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=UploadServerCertificate) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|UploadServerCertificate| The name of this action. Value: **UploadServerCertificate**

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the server certificate belongs.

 To query the region ID, call the[DescribeRegions](~~27584~~)API.

 |
|AliCloudCertificateId|String|No|730912673xxxxxx\_15d97e7709a\_71445759hr\_789289731| Optional. The ID of the certificate from the Alibaba Cloud SSL Certificates Service.

 This parameter is required if you use a certificate from the Alibaba Cloud SSL Certificates Service.

 |
|AliCloudCertificateName|String|No|testcertkey| Optional. The name of the certificate from the Alibaba Cloud SSL Certificates Service.

 |
|PrivateKey|String|No|wmsad! q23| Optional. The private key to be uploaded.

 |
|ResourceGroupId|String|No|rg-atstuj3rto\*\*\*\*| Optional. The ID of the enterprise resource group.

 |
|ServerCertificate|String|No|test| Optional. The public key certificate to be uploaded.

 |
|ServerCertificateName|String|No|mycert01| Optional. The name of the server certificate to be uploaded.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ServerCertificateId|String|xxxxidkp-123-cn-test-01| The ID of the server certificate.

 |
|ServerCertificateName|String|mycert01| The name of the server certificate.

 |
|Fingerprint|String|01:DF:AB:CD| The fingerprint of the server certificate.

 |
|AliCloudCertificateId|String|730912xxxxx\_15d97e7709a\_71445759hr\_789289731| The ID of the server certificate from the Alibaba Cloud SSL Certificate Service.

 |
|AliCloudCertificateName|String|testcertkey| The name of the server certificate from the Alibaba Cloud SSL Certificate Service.

 |
|CommonName|String|test| The domain name that corresponds to the common name field of the certificate.

 |
|CreateTime|String|2017-08-31T02:49:05Z| The time when the certificate is created.

 |
|CreateTimeStamp|Long|1504147745000| The timestamp that indicates when the certificate is created.

 |
|ExpireTime|String|1504147745000| The time when the certificate expires.

 |
|ExpireTimeStamp|Long|1504147745000| The timestamp that indicates when the certificate expires.

 |
|IsAliCloudCertificate|Integer|0| Indicates whether or not the certificate is from the Alibaba Cloud SSL Certificate Service.

 -   0: No
-   1: Yes

 |
|RegionId|String|cn-hangzhou| The ID of the region to which the certificate belongs.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The request ID.

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui| The ID of the enterprise resource group.

 |
|SubjectAlternativeNames| |test| A list of alternate domain names for the certificate is returned in array format.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=UploadServerCertificate
&RegionId=cn-hangzhou 
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

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

## Error codes {#section_78q_mvb_paq .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

