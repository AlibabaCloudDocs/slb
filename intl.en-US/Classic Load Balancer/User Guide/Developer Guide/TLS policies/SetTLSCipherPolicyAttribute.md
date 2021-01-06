# SetTLSCipherPolicyAttribute

Configures a TLS policy.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetTLSCipherPolicyAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetTLSCipherPolicyAttribute|The operation that you want to perform. Set the value to **SetTLSCipherPolicyAttribute**. |
|Ciphers.N|RepeatList|Yes|DES-CBC3-SHA|The supported cipher suites, which are determined by the TLS protocol version.

 The specified cipher suites must be supported by at least one TLS protocol version that you select. For example, if you set the TLSVersions.N parameter to TLSv1.3, you can specify only cipher suites that are supported by this protocol version.

 TLSv1.0 and TLSv1.1 support the following cipher suites:

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA AES256-SHA
-   DES-CBC3-SHA

 TLSv1.2 supports the following cipher suites:

 -   ECDHE-ECDSA-AES128-SHA
-   ECDHE-ECDSA-AES256-SHA
-   ECDHE-RSA-AES128-SHA
-   ECDHE-RSA-AES256-SHA
-   AES128-SHA AES256-SHA
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
-   AES128-SHA256 AES256-SHA256

 TLSv1.3 supports the following cipher suites:

 -   TLS\_AES\_128\_GCM\_SHA256
-   TLS\_AES\_256\_GCM\_SHA384
-   TLS\_CHACHA20\_POLY1305\_SHA256
-   TLS\_AES\_128\_CCM\_SHA256
-   TLS\_AES\_128\_CCM\_8\_SHA256 |
|Name|String|Yes|tls-policy\*\*\*\*\*-test|The name of the TLS policy. The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. |
|TLSCipherPolicyId|String|Yes|tls-bp1lp2076qx4e\*\*\*\*\*\*bridp|The ID of the TLS policy. |
|TLSVersions.N|RepeatList|Yes|TLSv1.0|The supported TLS protocol versions. Valid values: **TLSv1.0**, **TLSv1.1**, **TLSv1.2**, and **TLSv1.3**. |
|access\_key\_id|String|No|acc-nacl-hp34s2h0xx1ht4nwo\*\*\*\*|The AccessKey ID. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |
|TaskId|String|72dcd26b-f12d-4c27-b3af\*\*\*\*-18f6aed5|The ID of the asynchronous task. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=SetTLSCipherPolicyAttribute
&Ciphers.1=DES-CBC3-SHA
&Name=tls-policy*****-test
&RegionId=cn-hangzhou
&TLSCipherPolicyId=tls-bp1lp2076qx4e******bridp
&TLSVersions.1=TLSv1.0
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetTLSCipherPolicyAttributeReaponse>
  <TaskId>72dcd26b-f12d-4c27-b3af****-18f6aed5</TaskId>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</SetTLSCipherPolicyAttributeReaponse>
```

`JSON` format

```
{"TaskId":"72dcd26b-f12d-4c27-b3af****-18f6aed5",
"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

