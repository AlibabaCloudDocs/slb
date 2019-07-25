# UploadCACertificate {#doc_api_Slb_UploadCACertificate .reference}

Uploads a CA certificate.

You can only upload one CA certificate each time. After a CA certificate is uploaded, the certificate ID, name, and fingerprint are returned.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=UploadCACertificate) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|UploadCACertificate| The name of this action.

 Value: **UploadCACertificate**

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the CA certificate belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|CACertificate|String|Yes|test| The content of the CA certificate to be uploaded.

 |
|CACertificateName|String|No|mycacert01| Optional. The name of the CA certificate.

 |
|ResourceGroupId|String|No|rg-atstuj3rtoptyui| Optional. The ID of the enterprise resource group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|CACertificateId|String|139a00604ad-cn-east-hangzhou-01| The ID of the CA certificate.

 |
|CACertificateName|String|mycacert01| The name of the CA certificate.

 |
|Fingerprint|String|02:DF:AB:ED| The fingerprint of the CA certificate.

 |
|CommonName|String|.example.com| The domain name of the CA certificate.

 |
|CreateTime|String|2017-08-31T02:49:05Z| The time at which the CA certificate is uploaded.

 |
|CreateTimeStamp|Long|1504147745000| The timestamp indicating when the CA certificate is uploaded.

 |
|ExpireTime|String|2024-11-21T06:04:25Z| The time at which the CA certificate expires.

 |
|ExpireTimeStamp|Long|1732169065000| The timestamp indicating when the CA certificate expires.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |
|ResourceGroupId|String|rg-atstuj3rtoptyui| The ID of the enterprise resource group.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=UploadCACertificate
&RegionId=cn-hangzhou
&CACertificate=test
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<UploadCACertificateResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <ServerCertificateId>idkp-234-cn-test-02</ServerCertificateId>
  <ServerCertificateName>mycacert01</ServerCertificateName>
  <Fingerprint>02:DF:AB:ED</Fingerprint>
</UploadCACertificateResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"ServerCertificateId":"idkp-234-cn-test-02",
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"ServerCertificateName":"mycacert01",
	"Fingerprint":"02:DF:AB:ED"
}
```

## Error codes {#section_ajr_jsx_fcm .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

