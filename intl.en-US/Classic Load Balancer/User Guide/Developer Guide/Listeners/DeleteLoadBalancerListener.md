# DeleteLoadBalancerListener

Deletes a listener.

**Note:** A listener can be deleted only when it is in the **stopped** or **running** state.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancerListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteLoadBalancerListener|The name of this action.

 Value: **DeleteLoadBalancerListener** |
|ListenerPort|Integer|Yes|80|The frontend listening port used by the listener.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5xm\*\*\*\*\*\*\*\*|The ID of the Server Load Balancer \(SLB\) instance to which the listener belongs. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs. |
|ListenerProtocol|String|No|https|The frontend listening protocol used by the listener.

 **Note:** This parameter is required when listeners with different protocols use the same port. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DeleteLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xm********
&<CommonParameters>

```

Response example

`XML` format

```
<DeleteLoadBalancerListenerResponse>
			  <RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
		</DeleteLoadBalancerListenerResponse>
```

`JSON` format

```
{
	"RequestId":"791D8B68-AE0F-4174-AF54-088C8B3C5D54"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

