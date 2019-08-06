# DeleteServerCertificate {#doc_api_Slb_DeleteServerCertificate .reference}

Deletes a server certificate.

**Note:** You cannot delete a certificate that is in use.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteServerCertificate) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteServerCertificate| The name of this action.

 Value: **DeleteServerCertificate**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|ServerCertificateId|String|Yes|123157xxxxxxx\_166f8204689\_1714763408\_709981430| The ID of the server certificate.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteServerCertificate
&ServerCertificateId=123157xxxxxxx_166f8204689_1714763408_709981430
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteServerCertificateResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteServerCertificateResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_1d8_yqg_q09 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

