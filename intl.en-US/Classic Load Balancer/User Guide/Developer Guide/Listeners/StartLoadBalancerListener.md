# StartLoadBalancerListener

You can call this operation to start a listener.

When you call this operation, note the following items:

-   You can call the operation only when the listener is in the Stopped state.
-   After the operation is called, the status of the listener changes to Starting.
-   You cannot call this operation when the SLB instance to which the listener is bound is in the Locked state.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=StartLoadBalancerListener&type=RPC&version=2014-05-15)

## Request Parameter

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|StartLoadBalancerListener|The operation that you want to perform.

 Set the value to **StartLoadBalancerListener**. |
|ListenerPort|Integer|Yes|80|The listener port of the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5\*\*\*\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is deployed.

 You can retrieve the region ID by calling the [DescribeRegions](~~27584~~) operation. |
|ListenerProtocol|String|No|https|The protocol used by the listener of the SLB instance.

 **Note:** If different listeners use the same port, you must specify this parameter. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=StartLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5*********
&<Common request parameters>
```

Sample success responses

`XML` format

```
<StartLoadBalancerListenerResponse>
			  <RequestId>CC000321-00F2-49B8-9BCA-60D822414960</RequestId>
		</StartLoadBalancerListenerResponse>
```

`JSON` format

```
{
    "RequestId": "CC000321-00F2-49B8-9BCA-60D822414960"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

