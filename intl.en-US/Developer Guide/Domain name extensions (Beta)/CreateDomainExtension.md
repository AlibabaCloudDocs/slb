# CreateDomainExtension {#doc_api_881520 .reference}

You can call the CreateDomainExtension API to create a domain name extension.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=CreateDomainExtension) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|CreateDomainExtension|The action to perform. Valid value: **CreateDomainExtension**

 |
|Domain|String|Yes|\*.example1.com|The domain name

 |
|ListenerPort|Integer|Yes|443|The frontend port used by the HTTPS listener of the SLB instance. Valid values: **1–65535**

 |
|LoadBalancerId|String|Yes|lb-bp1o94dp5i6earr9g6d1l|The ID of the SLB instance

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs

 |
|ServerCertificateId|String|Yes|123157908552\*\*\*\*\_166f8204689\_1714763408\_709981430|The ID of the certificate used by the domain name

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|DomainExtensionId|String|de-bp1rp7ta191dv|The ID of the created domain name extension

 |
|ListenerPort|Integer|80|The frontend port used by the SLB instance

 |
|RequestId|String|A6E7EFC9-0938-40CA-877D-9BEDBD21D357|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Domain=*.example1.com
&ListenerPort=443
&LoadBalancerId=lb-bp1o94dp5i6earr9g6d1l
&RegionId=cn-hangzhou
&ServerCertificateId=123157908552****_166f8204689_1714763408_709981430
&Action=CreateDomainExtension
&Tags={"tagKey":"Key1","tagValue":"Value1"}
&<CommonParameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<CreateDomainExtension>
  <RequestId>A6E7EFC9-0938-40CA-877D-9BEDBD21D357</RequestId>
  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
  <ListenerPort>443</ListenerPort>
</CreateDomainExtension>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"A6E7EFC9-0938-40CA-877D-9BEDBD21D357",
	"DomainExtensionId":"de-bp1rp7ta191dv",
	"ListenerPort":443
}
```

Error response example

## Error codes { .section}

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

