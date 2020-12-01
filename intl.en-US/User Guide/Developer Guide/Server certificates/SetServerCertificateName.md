# SetServerCertificateName

Sets a name for a server certificate.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=SetServerCertificateName&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetServerCertificateName|The name of this action.

 Value: **SetServerCertificateName** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the Server Load Balancer \(SLB\) instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~). |
|ServerCertificateId|String|Yes|139a00604ad-cn-east-hangzhou-01|The ID of the server certificate. |
|ServerCertificateName|String|Yes|abc|The name of the server certificate.

 The name must be 1 to 80 characters in length. It must start with an English letter. It can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FE7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=SetServerCertificateName
&RegionId=cn-hangzhou
&ServerCertificateId=139a00604ad-cn-east-hangzhou-01
&ServerCertificateName=abc
&<CommonParameters>

```

Response example

`XML` format

```
<SetServerCertificateNameResponse>
      <RequestId>CEF72CEB-54B6-4AE8-B225-F876FE7BA984</RequestId>
</SetServerCertificateNameResponse>
```

`JSON` format

```
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FE7BA984"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

