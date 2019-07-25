# SetDomainExtensionAttribute {#doc_api_Slb_SetDomainExtensionAttribute .reference}

Modifies the certificate of a domain name extension.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetDomainExtensionAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetDomainExtensionAttribute| The name of this action.

 Value: **SetDomainExtensionAttribute**

 |
|DomainExtensionId|String|Yes|de-bp1rp7ta191dv| The ID of the domain name extension to be modified.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|ServerCertificateId|String|Yes|1231579xxxxxxxx\_166f8204689\_1714763408\_709981xxx| The ID of the new certificate.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetDomainExtensionAttribute
&DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&ServerCertificateId=1231579xxxxxxxx_166f8204689_1714763408_709981xxx
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetDomainExtensionAttributeResponse>
  <RequestId>149A2470-F010-4437-BF68-xxxxx</RequestId>
</SetDomainExtensionAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"B1435A8D-5AE2-4EB2-9590-xxxxxx"
}
```

## Error codes {#section_vr4_zwx_0ws .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

