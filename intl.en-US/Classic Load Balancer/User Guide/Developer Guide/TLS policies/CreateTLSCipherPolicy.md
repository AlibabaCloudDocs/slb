# CreateTLSCipherPolicy

Creates a TLS policy.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateTLSCipherPolicy&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateTLSCipherPolicy|The operation that you want to perform. Set the value to **CreateTLSCipherPolicy**. |
|Ciphers.N|RepeatList|Yes|AES256-SHA256|The supported cipher suites, which are determined by the TLS protocol version.

 TLSv1.0 and TLSv1.1 support the following cipher suites:

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA
-   AES256-SHA
-   DES-CBC3-SHA

 TLSv1.2 supports the following cipher suites:

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA
-   AES256-SHA
-   DES-CBC3-SHA
-   ECDHE-ECDSA-AES128-GCM-SHA256
-   ECDHE-ECDSA-AES256-GCM-SHA384
-   ECDHE-ECDSA-AES128-SHA256
-   ECDHE-ECDSA-AES256-SHA384
-   ECDHE-RSA-AES128-GCM-SHA256
-   ECDHE-RSA-AES256-GCM-SHA384
-   ECDHE-RSA-AES128-SHA256
-   ECDHE-RSA-AES256-SHA384
-   AES128-GCM-SHA256
-   AES256-GCM-SHA384
-   AES128-SHA256
-   AES256-SHA256

 TLSv1.3 supports the following cipher suites:

 -   TLS\_AES\_128\_GCM\_SHA256
-   TLS\_AES\_256\_GCM\_SHA384
-   TLS\_CHACHA20\_POLY1305\_SHA256
-   TLS\_AES\_128\_CCM\_SHA256
-   TLS\_AES\_128\_CCM\_8\_SHA256 |
|Name|String|Yes|TLSPolicy-test\*\*\*\*\*|The name of the TLS policy. The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. |
|TLSVersions.N|RepeatList|Yes|TLSv1.0|The supported TLS protocol versions. Valid values: **TLSv1.0**, **TLSv1.1**, **TLSv1.2**, and **TLSv1.3**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |
|TLSCipherPolicyId|String|tc-policy\*\*\*\*\*\*|The ID of the created TLS policy. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=CreateTLSCipherPolicy
&Ciphers.1=AES256-SHA256
&Name=TLSPolicy-test*****
&RegionId=cn-hangzhou
&TLSVersions.1=TLSv1.0
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateTLSCipherPolicyResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
  <TLSCipherPolicyId>tc-policy******</TLSCipherPolicyId>
</CreateTLSCipherPolicyResponse>
```

`JSON` format

```
{"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
"TLSCipherPolicyId":"tc-policy******"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

