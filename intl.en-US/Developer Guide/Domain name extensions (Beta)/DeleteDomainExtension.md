# DeleteDomainExtension {#doc_api_Slb_DeleteDomainExtension .reference}

Deletes a domain name extension.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteDomainExtension) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteDomainExtension| The name of this action.

 Value: **DeleteDomainExtension**

 |
|DomainExtensionId|String|Yes|de-bp1rp7ta191dv| The ID of the domain name extension to be deleted.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|149A2470-F010-4437-BF68-343D5099C19D| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteDomainExtension
&DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteDomainExtensionResponse>
  <RequestId>149A2470-F010-4437-BF68-343D5099C19D</RequestId>
</DeleteDomainExtensionResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"5B45BED9-4D41-47B0-ADD6-47A5624516C7"
}
```

## Error codes {#section_56i_cgk_qlc .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

