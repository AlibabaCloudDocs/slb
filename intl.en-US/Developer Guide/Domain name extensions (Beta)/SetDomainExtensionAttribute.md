# SetDomainExtensionAttribute {#doc_api_834951 .reference}

You can call the SetDomainExtensionAttribute API to modify the certificate of a domain name extension.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=SetDomainExtensionAttribute) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|SetDomainExtensionAttribute|The action to perform. Valid value: **SetDomainExtensionAttribute**

 |
|DomainExtensionId|String|Yes|de-bp1rp7ta191dv|The ID of the domain name extension to be modified

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs

 |
|ServerCertificateId|String|Yes|123157908552\*\*\*\*\_166f8204689\_1714763408\_709981430|The ID of the new certificate

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&ServerCertificateId=1231579085529123_166f8204689_1714763408_709981430
&Action=SetDomainExtensionAttribute
&Tags={"tagKey":"Key1","tagValue":"Value1"}
&<CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<SetDomainExtensionAttributeResponse>
  <RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
</SetDomainExtensionAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"B1435A8D-5AE2-4EB2-9590-FF239E4642D1"
}
```

Error response example

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

