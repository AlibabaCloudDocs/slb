# DeleteServerCertificate {#doc_api_875320 .reference}

Delete a server certificate.

**Note:** You cannot delete a certificate that is in use.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=DeleteServerCertificate) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|DeleteServerCertificate|The action to perform. Valid value: **DeleteServerCertificate**

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the SLB instance belongs.

 You can query the region ID by calling the [DescribeRegions](~~27584~~) API.

 |
|ServerCertificateId|String|Yes|123157908552\*\*\*\*\_166f8204689\_1714763408\_709981430|The ID of the server certificate

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteServerCertificate
&ServerCertificateId=1231579085529****_166f8204689_1714763408_709981430
&<CommonParameters>

```

Normal response examples

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

Error response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

