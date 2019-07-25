# SetCACertificateName {#doc_api_Slb_SetCACertificateName .reference}

Sets the name of a CA Certificate.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetCACertificateName) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetCACertificateName| The name of this action.

 Value: **SetCACertificateName**

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the CA certificate belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|CACertificateId|String|Yes|139a00604ad-cn-east-hangzhou-01| The ID of the CA certificate.

 |
|CACertificateName|String|Yes|mycacert02| The name of the CA certificate.

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

http(s)://[Endpoint]/? Action=SetCACertificateName
&RegionId=cn-hangzhou
&CACertificateId=139a00604ad-cn-east-hangzhou-01
&CACertificateName=mycacert02
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetCACertificateNameResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
</SetCACertificateNameResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
}
```

## Error codes {#section_htp_nex_lwc .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

