# DeleteCACertificate {#doc_api_Slb_DeleteCACertificate .reference}

Deletes a CA certificate.

**Note:** CA certificates in use cannot be deleted.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteCACertificate) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteCACertificate| The name of this action.

 Value: **DeleteCACertificate**

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the CA certificate belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|CACertificateId|String|Yes|123157908xxxxxxx\_15c73d77203\_-986300114\_-2110544xxx| The ID of the CA certificate.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteCACertificate
&RegionId=cn-hangzhou
&CACertificateId=123157908xxxxxxx_15c73d77203_-986300114_-2110544xxx
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteCACertificateResponse>
  <RequestId>CEFxxxxx72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteCACertificateResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEFxxxx72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_hxx_oz3_wu6 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

