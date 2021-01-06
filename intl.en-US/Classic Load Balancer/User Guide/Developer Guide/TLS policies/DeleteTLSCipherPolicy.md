# DeleteTLSCipherPolicy

Deletes a TLS policy.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DeleteTLSCipherPolicy&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DeleteTLSCipherPolicy|The operation that you want to perform. Set the value to **DeleteTLSCipherPolicy**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. |
|TLSCipherPolicyId|String|Yes|tls-bp1lp2076qx4ebridp\*\*\*\*\*\*|The ID of the TLS policy. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DeleteTLSCipherPolicy
&RegionId=cn-hangzhou
&TLSCipherPolicyId=tls-bp1lp2076qx4ebridp******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DeleteTLSCipherPolicyResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteTLSCipherPolicyResponse>
```

`JSON` format

```
{"RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

