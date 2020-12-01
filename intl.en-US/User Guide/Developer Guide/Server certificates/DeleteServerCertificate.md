# DeleteServerCertificate

Deletes a server certificate.

**Note:** You cannot delete server certificates that are in use.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DeleteServerCertificate&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteServerCertificate|The operation that you want to perform.

 Set the value to **DeleteServerCertificate**. |
|ServerCertificateId|String|Yes|123157xxxxxxx\_166f8204689\_1714763408\_7099\*\*\*\*\*\*\*|The ID of the server certificate. |
|RegionId|String|Yes|cn-hangzhou|The region where the Server Load Balancer \(SLB\) instance is created.

 You can call the [DescribeRegions](~~27584~~) operation to query region IDs. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=DeleteServerCertificate
&ServerCertificateId=123157xxxxxxx_166f8204689_1714763408_7099*******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteServerCertificateResponse>
		  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId></DeleteServerCertificateResponse>
```

`JSON` format

```
{

"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|CertificateAndPrivateKeyIsRefered|The specified certificate is bound to listeners. You cannot delete it.|The error message returned because the server certificate cannot be deleted when the certificate is associated with a listener.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

