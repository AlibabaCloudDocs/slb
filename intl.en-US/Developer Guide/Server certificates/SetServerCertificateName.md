# SetServerCertificateName {#doc_api_Slb_SetServerCertificateName .reference}

Sets the name of a server certificate.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetServerCertificateName) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetServerCertificateName| The name of this action.

 Value: **SetServerCertificateName**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|ServerCertificateId|String|Yes|139a00604ad-cn-east-hangzhou-01| The ID of the server certificate.

 |
|ServerCertificateName|String|Yes|abc| The name of the server certificate.

 The name must be 1 to 80 characters in length and start with an English letter or a Chinese character. It can contain numbers, underscores \(\_\), periods \(.\), and hyphens \(-\).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FE7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetServerCertificateName
&RegionId=cn-hangzhou
&ServerCertificateId=139a00604ad-cn-east-hangzhou-01
&ServerCertificateName=abc
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetServerCertificateNameResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
</SetServerCertificateNameResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
}
```

## Error codes {#section_we9_60z_3li .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

