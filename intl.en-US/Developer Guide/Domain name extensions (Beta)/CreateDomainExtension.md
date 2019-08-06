# CreateDomainExtension {#doc_api_Slb_CreateDomainExtension .reference}

Creates a domain name extension.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateDomainExtension) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateDomainExtension| The name of this action.

 Value: **CreateDomainExtension**

 |
|Domain|String|Yes|\*.example1.com| The domain name to be created.

 |
|ListenerPort|Integer|Yes|443| The frontend port of the HTTPS listener.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earrxxxxxx| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|ServerCertificateId|String|Yes|123157xxxxxxx\_166f820xxxxxx\_1714763408\_709981xxxx| The ID of the certificate used by the domain name.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|DomainExtensionId|String|de-bp1rp7ta19xxxx| The ID of the created domain name extension.

 |
|ListenerPort|Integer|80| The frontend port used by the SLB instance.

 |
|RequestId|String|A6E7EFC9-0938-40CA-877D-9BEDBD21D357| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateDomainExtension
&Domain=*.example1.com
&ListenerPort=443
&LoadBalancerId=lb-bp1o94dp5i6earrxxxxxx
&RegionId=cn-hangzhou
&ServerCertificateId=123157xxxxxxx_166f820xxxxxx_1714763408_709981xxxx
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateDomainExtensionResponse>
  <RequestId>A6E7EFC9-0938-40CA-877D-9BEDBD21D357</RequestId>
  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
  <ListenerPort>443</ListenerPort>
</CreateDomainExtensionResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"A6E7EFC9-0938-40CA-877D-9BEDBD21D357",
	"DomainExtensionId":"de-bp1rp7ta191dv",
	"ListenerPort":443
}
```

## Error codes {#section_5iu_nzn_vcw .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

