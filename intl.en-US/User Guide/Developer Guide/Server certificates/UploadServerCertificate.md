# UploadServerCertificate

Uploads a server certificate.

You can upload only one server certificate and its private key in each request.

The request is successful only when the server certificate and its private key are both uploaded. If the server certificate or its private key is not uploaded, the request fails. After a server certificate and its private key are uploaded, the fingerprints of all server certificates under your account are returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=UploadServerCertificate&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|UploadServerCertificate|The operation that you want to perform.

 Set the value to **UploadServerCertificate**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the server certificate is created.

 You can call the [DescribeRegions](~~27584~~) operation to query region IDs. |
|AliCloudCertificateId|String|No|730912673xxxxxx\_15d97e7709a\_71445759hr\_7892\*\*\*\*\*\*|The ID of the certificate from the Alibaba Cloud certificate service.

 This parameter is required if you use a certificate from the Alibaba Cloud certificate service. |
|AliCloudCertificateName|String|No|testcertkey|The name of the certificate from the Alibaba Cloud certificate service. |
|AliCloudCertificateRegionId|String|No|cn-hangzhou|The region where the certificate from the Alibaba Cloud certificate service is created. |
|ServerCertificate|String|No|test|The public key certificate that you want to upload.

 **Note:** This parameter is required if you use a third-party certificate. |
|PrivateKey|String|No|wmsa\*\*\*\*\*|The private key of the server certificate that you want to upload.

 **Note:** This parameter is required if you use a third-party certificate. |
|ServerCertificateName|String|No|mycert01|The name of the server certificate that you want to upload.

 The name must be 1 to 80 characters in length. It must start with letters or Chinese characters. It can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). |
|ResourceGroupId|String|No|rg-atstuj3rto\*\*\*\*|The ID of the enterprise resource group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ServerCertificateId|String|xxxxidkp-123-cn-test\*\*\*\*\*\*|The ID of the server certificate. |
|Fingerprint|String|01:DF:AB:\*\*|The fingerprint of the server certificate. |
|ServerCertificateName|String|mycert01|The name of the server certificate. |
|RegionId|String|cn-hangzhou|The ID of the region where the server certificate is created. |
|AliCloudCertificateId|String|730912xxxxx\_15d97e7709a\_71445759hr\_7\*\*\*\*\*\*\*|The ID of the server certificate that is from the Alibaba Cloud certificate service. |
|AliCloudCertificateName|String|testcert\*\*\*|The name of the server certificate that is from the Alibaba Cloud certificate service. |
|IsAliCloudCertificate|Integer|0|Indicates whether the server certificate is from the Alibaba Cloud certificate service. Valid values:

 -   0: The server certificate is from the Alibaba Cloud certificate service.
-   1: The server certificate is from a third-party service. |
|ResourceGroupId|String|rg-atstuj3rt\*\*\*\*\*\*|The ID of the enterprise resource group. |
|CreateTime|String|2017-08-31T02:49:05Z|The time when the server certificate was created. |
|CreateTimeStamp|Long|1504147745000|The timestamp when the server certificate was created. |
|ExpireTime|String|1504147745000|The time when the server certificate expires. |
|ExpireTimeStamp|Long|1504147745000|The timestamp when the server certificate expires. |
|CommonName|String|test|The domain name. The domain name is the same as the common name field of the server certificate. |
|SubjectAlternativeNames|List|test|The list of alternate domain names for the server certificate is returned. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=UploadServerCertificate
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<UploadServerCertificateResponse>
	  <CommonName>*.example1.com</CommonName>
	  <RegionIdAlias>cn-hangzhou</RegionIdAlias>
	  <ResourceGroupId>rg-acfmxazb4*****</ResourceGroupId>
	  <Fingerprint>68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d</Fingerprint>
	  <ServerCertificateId>12315790xxxxxxxx3_166f8204689_1714763408_7099****</ServerCertificateId>
	  <ExpireTimeStamp>1558161264000</ExpireTimeStamp>
	  <AliCloudCertificateId>150173**</AliCloudCertificateId>
	  <ExpireTime>2019-05-18T06:34:24Z</ExpireTime>
	  <RegionId>cn-hangzhou</RegionId>
	  <RequestId>C87620A7-3608-48D0-BC41-A83FB4FF0EC6</RequestId>
	  <ServerCertificateName>*.example1.com</ServerCertificateName>
	  <IsAliCloudCertificate>1</IsAliCloudCertificate>
	  <AliCloudCertificateName>slb</AliCloudCertificateName>
</UploadServerCertificateResponse>
```

`JSON` format

```
{
    "CommonName": "*.example1.com",
    "RegionIdAlias": "cn-hangzhou",
    "ResourceGroupId": "rg-acfmxazb4p*****",
    "Fingerprint": "68:08:1a:f8:2c:97:69:a3:a1:e6:16:41:4b:ca:4f:5d:ee:a5:ef:0d",
    "ServerCertificateId": "12315790xxxxxxxx3_166f8204689_1714763408_709******",
    "AliCloudCertificateId": "15017**",
    "ExpireTime": "2019-05-18T06:34:24Z",
    "RegionId": "cn-hangzhou",
    "RequestId": "C87620A7-3608-48D0-BC41-A83FB4FF0EC6",
    "ServerCertificateName": "*.example1.com",
    "IsAliCloudCertificate": 1,
    "AliCloudCertificateName": "slb"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

