# ListTLSCipherPolicies

Queries TLS policies.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=ListTLSCipherPolicies&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ListTLSCipherPolicies|The operation that you want to perform. Set the value to **ListTLSCipherPolicies**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. |
|TLSCipherPolicyId|String|Yes|tls-bp1lp2076qx4e\*\*\*\*\*\*bridp|The ID of the TLS policy. |
|Name|String|No|tls-policy\*\*\*\*\*-test|The name of the TLS policy. The name must be 2 to 128 characters in length, and can contain letters, digits, periods \(.\), underscores \(\_\), and hyphens \(-\). It must start with a letter. |
|IncludeListener|Boolean|No|false|Specifies whether to return the information about the associated listener. Valid values: **true** and **false**. Default value: false. |
|NextToken|String|No|cae\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*f0a|The position where the query starts. If this parameter is left empty, the query starts from the beginning. |
|MaxItems|Integer|No|20|The maximum number of TLS policies that can be queried in this call. Valid values: **1** to **100**. If this parameter is left empty, the default value **20** is used. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|IsTruncated|Boolean|false|Indicates whether the query ends. Valid values:

 -   **true**: The current page is the last page to return.
-   **false**: The current page is not the last page to return. |
|NextToken|String|caeba0bbb2be03f84eb48b699f0a\*\*\*\*|Indicates the position where the query started. If this parameter was left empty, the query started from the beginning. |
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |
|TLSCipherPolicies|Array of TLSCipherPolicy| |The list of TLS policies. |
|Ciphers|List|ECDHE-ECDSA-AES128-SHA|The supported cipher suites, which are determined by the TLS protocol version.

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
|CreateTime|Long|1608273800000|The timestamp when the query was started. |
|InstanceId|String|tls-bp1lp2076qx4e\*\*\*\*\*\*bridp|The ID of the TLS policy. |
|Name|String|tls-policy\*\*\*\*\*-test|The name of the TLS policy. |
|RelateListeners|Array of RelateListener| |The associated listener. |
|LoadBalancerId|String|lb-bp1b6c719dfa08ex\*\*\*\*\*|The ID of the SLB instance. |
|Port|Integer|80|The listening port. Valid values: **1** to **65535**. |
|Protocol|String|HTTPS|The listener protocol. Valid values: **TCP**, **UDP**, **HTTP**, and **HTTPS**. |
|Status|String|normal|The state of the TLS policy. Valid values:

 -   **configuring**: The policy is being configured.
-   **normal**: The policy is normal. |
|TLSVersions|List|TLSv1.0|The supported TLS protocol versions. |
|TotalCount|Integer|1000|The total number of TLS policies that were returned in this call. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ListTLSCipherPolicies
&RegionId=cn-hangzhou
&TLSCipherPolicyId=tls-bp1lp2076qx4e******bridp
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ListTLSCipherPoliciesResponse>
  <TotalCount>1000</TotalCount>
  <NextToken>caeba0bbb2be03f84eb48b699f0a****</NextToken>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
  <TLSCipherPolicies>
        <Status>normal</Status>
        <InstanceId>tls-bp1lp2076qx4e******bridp</InstanceId>
        <CreateTime>1608273800000</CreateTime>
        <Name>tls-policy*****-test</Name>
  </TLSCipherPolicies>
  <TLSCipherPolicies>
        <RelateListeners>
              <LoadBalancerId>lb-bp1b6c719dfa08ex*****</LoadBalancerId>
              <Protocol>HTTPS</Protocol>
              <Port>80</Port>
        </RelateListeners>
  </TLSCipherPolicies>
  <TLSCipherPolicies>
        <Ciphers>ECDHE-ECDSA-AES128-SHA</Ciphers>
        <TLSVersions>TLSv1.0</TLSVersions>
  </TLSCipherPolicies>
  <IsTruncated>false</IsTruncated>
</ListTLSCipherPoliciesResponse>
```

`JSON` format

```
{"TotalCount":"1000",
"NextToken":"caeba0bbb2be03f84eb48b699f0a****",
"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984",
"TLSCipherPolicies":
[
    {
        "Status":"normal",
    "InstanceId":"tls-bp1lp2076qx4e******bridp",
    "CreateTime":"1608273800000",
    "Name":"tls-policy*****-test"
    },
    {
        "RelateListeners":[
        {
            "LoadBalancerId":"lb-bp1b6c719dfa08ex*****",
            "Protocol":"HTTPS",
            "Port":"80"
            }
            ]
            },
            {
                "Ciphers":"ECDHE-ECDSA-AES128-SHA",
                "TLSVersions":"TLSv1.0"
                }
                ],
                "IsTruncated":"false"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

