# DescribeDomainExtensionAttribute

Queries the attributes of an additional certificate.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeDomainExtensionAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeDomainExtensionAttribute|The operation that you want to perform. Set the value to **DescribeDomainExtensionAttribute**. |
|DomainExtensionId|String|Yes|de-bp1rp7ta191dv|The ID of the additional certificate. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|Domain|String|www.example.com|The domain name. |
|DomainExtensionId|String|de-bp1rp7ta191dv|The ID of the additional certificate. |
|ListenerPort|Integer|443|The frontend port of the HTTPS listener that is configured for the SLB instance. Valid values: **1** to **65535**. |
|LoadBalancerId|String|lb-bp1o94dp5i6\*\*\*\*\*earr9g6d1l|The ID of the SLB instance. |
|RequestId|String|48C1B671-C6DB-4DDE-9B30-10557E36CDE0|The ID of the request. |
|ServerCertificateId|String|231579085529123\_166f82\*\*\*\*\*\*\_1714763408\_709981430|The ID of the server certificate that is used by the domain name. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeDomainExtensionAttribute
&DomainExtensionId=de-bp1rp7ta191dv
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeDomainExtensionAttributeResponse>
  <ListenerPort>443</ListenerPort>
  <DomainExtensionId>de-bp1rp7ta191dv</DomainExtensionId>
  <RequestId>48C1B671-C6DB-4DDE-9B30-10557E36CDE0</RequestId>
  <ServerCertificateId>231579085529123_166f82******_1714763408_709981430</ServerCertificateId>
  <LoadBalancerId>lb-bp1o94dp5i6*****earr9g6d1l</LoadBalancerId>
  <Domain>www.example.com</Domain>
</DescribeDomainExtensionAttributeResponse>
```

`JSON` format

```
{"ListenerPort":"443",
"DomainExtensionId":"de-bp1rp7ta191dv",
"RequestId":"48C1B671-C6DB-4DDE-9B30-10557E36CDE0",
"ServerCertificateId":"231579085529123_166f82******_1714763408_709981430",
"LoadBalancerId":"lb-bp1o94dp5i6*****earr9g6d1l",
"Domain":"www.example.com"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

