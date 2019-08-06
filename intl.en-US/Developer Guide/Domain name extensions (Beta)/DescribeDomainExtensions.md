# DescribeDomainExtensions {#doc_api_Slb_DescribeDomainExtensions .reference}

Queries the added domain name extensions.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeDomainExtensions) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeDomainExtensions| The name of this action.

 Value: **DescribeDomainExtensions**

 |
|ListenerPort|Integer|Yes|443| The frontend port used by the HTTPS listener of the SLB instance. Value range: **1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earr9g6d1l| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|DomainExtensionId|String|No|de-bp1rp7ta191dv| Optional. The ID of the domain name extension.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|DomainExtensions| | | A list of domain name extensions.

 |
|└Domain|String|www.example.com| The domain name.

 |
|└DomainExtensionId|String|de-bp1rp7ta191dv| The ID of the domain name extension.

 |
|└ServerCertificateId|String|1231579085529123\_166f8204689\_1714763408\_709981430| The ID of the certificate used by the domain name.

 |
|RequestId|String|48C1B671-C6DB-4DDE-9B30-10557E36CDE0| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeDomainExtensions
&ListenerPort=443
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeDomainExtensionsResponse>
  <RequestId>CCC710F8-285C-415F-9211-9BD6BF7BB997</RequestId>
  <DomainExtensions>
    <DomainExtension>
      <ServerCertificateId>123157908xxxxxx_166f8204689_1714763408_70xxx</ServerCertificateId>
      <Domain>*.example2.com</Domain>
      <DomainExtensionId>de-bp1k4chwdnhxd</DomainExtensionId>
    </DomainExtension>
  </DomainExtensions>
</DescribeDomainExtensionsResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"48C1B671-C6DB-4DDE-9B30-10557E36CDE0",
	"DomainExtensions":{
		"DomainExtension":[
			{
				"ServerCertificateId":"123157908xxxxxx_166f8204689_1714763408_70xxx",
				"Domain":"*.example1.com",
				"DomainExtensionId":"de-bp1rp7ta191dv"
			}
		]
	}
}
```

## Error codes {#section_tg1_wgu_chk .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

