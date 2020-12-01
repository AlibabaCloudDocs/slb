# UploadCACertificate

Uploads a CA certificate.

You can upload only one CA certificate at a time. After a CA certificate is uploaded, the certificate ID, name, and fingerprint are returned.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=UploadCACertificate&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|UploadCACertificate|The name of this action.

 Value: **UploadCACertificate** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the CA certificate belongs.

 To query the region ID, call [DescribeRegions](~~27584~~). |
|CACertificate|String|Yes|test|The content of the CA certificate to be uploaded. |
|CACertificateName|String|No|mycacert01|The name of the CA certificate. |
|ResourceGroupId|string|No|rg-atstuj3rtoptyui|The ID of the enterprise resource group. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|CACertificateId|String|139a00604ad-cn-east-hangzhou-01|The ID of the CA certificate. |
|CACertificateName|String|mycacert01|The name of the CA certificate. |
|Fingerprint|String|02:DF:AB:ED|The fingerprint of the CA certificate. |
|CommonName|String|.example.com|The domain name of the CA certificate. |
|CreateTime|String|2017-08-31T02:49:05Z|The time when the CA certificate is uploaded. |
|CreateTimeStamp|Long|1504147745000|The timestamp generated when the CA certificate is uploaded. |
|ExpireTime|String|2024-11-21T06:04:25Z|The time when the CA certificate expires. |
|ExpireTimeStamp|Long|1732169065000|The timestamp generated when the CA certificate expires. |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ResourceGroupId|String|rg-atstuj3rtoptyui|The ID of the enterprise resource group. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=UploadCACertificate
&RegionId=cn-hangzhou
&CACertificate=test
&<CommonParameters>

```

Response example

`XML` format

```
<UploadCACertificateResponse>
	    <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
	    <ServerCertificateId>idkp-234-cn-test-02</ServerCertificateId>
	  <ServerCertificateName>mycacert01</ServerCertificateName>
	    <Fingerprint>02:DF:AB:ED</Fingerprint>
</UploadCACertificateResponse>
```

`JSON` format

```
{
	"ServerCertificateId":"idkp-234-cn-test-02",
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"ServerCertificateName":"mycacert01",
	"Fingerprint":"02:DF:AB:ED"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

