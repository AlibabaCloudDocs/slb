# DescribeCACertificates {#doc_api_Slb_DescribeCACertificates .reference}

Queries the list of CA certificates.

**Note:** For security reasons, only the name and the fingerprint are returned instead of the certificate content and the private key.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeCACertificates) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeCACertificates| The name of this action.

 Value: **DescribeCACertificates**

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the CA certificate belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|CACertificateId|String|No|139a00604bd-cn-east-hangzhou-02| Optional. The ID of the CA certificate.

 |
|OwnerAccount|String|No|testuser@aliyun.com| Optional. Your account.

 |
|ResourceGroupId|String|No|rg-atstuj3rtoptyui| Optional. The ID of the enterprise resource group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|CACertificates| | | A list of CA certificates.

 |
|└CACertificateId|String|139a00604bd-cn-east-hangzhou-02| The ID of the CA certificate.

 |
|└CACertificateName|String|test| The name of the CA certificate.

 |
|└RegionId|String|cn-hangzhou| The region to which the CA certificate belongs.

 |
|└Fingerprint|String|AC:BE:FD| The fingerprint of the CA certificate.

 |
|└CommonName|String|.example.com| The domain name of the CA certificate.

 |
|└CreateTime|String|2017-08-31T02:49:05Z| The time when the CA certificate is created.

 |
|└CreateTimeStamp|Long|1504147745000| The timestamp that indicates when the CA certificate is created.

 |
|└ExpireTime|String|2024-11-21T06:04:25Z| The time when the CA certificate expires.

 |
|└ExpireTimeStamp|Long|1732169065000| The timestamp that indicates when the CA certificate expires.

 |
|└ResourceGroupId|String|rg-atstuj3rtoptyui| The ID of the enterprise resource group.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeCACertificates
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeCACertificateResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <CACertificates>
    <CACertificate>
      <CACertificateId>139a00604bd-cn-east-hangzhou-01
        </CACertificateId>
      <CACertificateName>bcd
    </CACertificateName>
      <Fingerprint>AB:CB:DE</Fingerprint>
    </CACertificate>
    <CACertificate>
      <CACertificateId>139a00604bd-cn-east-hangzhou-02</CACertificateId>
      <CACertificateName>cde</CACertificateName>
      <Fingerprint>AC:BE:FD</Fingerprint>
    </CACertificate>
  </CACertificates>
</DescribeCACertificateResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	" CACertificates":{
		"CACertificate":[
			{
				"CACertificateName":"bcd",
				"Fingerprint ":"AB:CB:DE",
				"CACertificateId":"139a00604bd-cn-east-hangzhou-01"
			},
			{
				"CACertificateName":"cde",
				"Fingerprint ":"AC:BE:FD",
				"CACertificateId":"282b00102ac-cn-east-hangzhou-02"
			}
		]
	}
}
```

## Error codes {#section_vnd_h5a_49a .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

