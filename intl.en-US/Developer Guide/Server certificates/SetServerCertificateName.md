# SetServerCertificateName {#doc_api_875287 .reference}

You can call the SetServerCertificateName API to set the name for a server certificate.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=SetServerCertificateName) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|SetServerCertificateName|The action to perform. Valid value: **SetServerCertificateName**.

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the SLB instance belongs.

 You can query the region ID by calling the [DescribeRegions](~~27584~~) API.

 |
|ServerCertificateId|String|Yes|139a00604ad-cn-east-hangzhou-01|The ID of the server certificate

 |
|ServerCertificateName|String|Yes|abc|The name of the server certificate.

 The name must be 1 to 80 characters in length, must start with English letters or Chinese characters, and can contain numbers, underscores \(\_\), periods \(.\), and hyphens \(-\).

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FE7BA984|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

https://slb.aliyuncs.com/
&Action=SetServerCertificateName
&RegionId=cn-hangzhou
&ServerCertificateId=123157908552****_166f8204689_1714763408_709981430
&ServerCertificateName=.example1.com
&<CommonParameters>

```

Normal response examples

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

