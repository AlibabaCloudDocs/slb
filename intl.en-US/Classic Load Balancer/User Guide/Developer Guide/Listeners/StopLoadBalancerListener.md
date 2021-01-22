# StopLoadBalancerListener

Stops a listener.

Before you make this API call, note the following:

-   After the API call is successfully made, the listener enters the stopped state.
-   If the Server Load Balancer \(SLB\) instance to which the listener to be stopped belongs is in the locked state, this API call cannot be made.

**Note:** If you stop the listener, your services will be disrupted. Exercise caution when you perform this action.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=StopLoadBalancerListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|StopLoadBalancerListener|The name of this action.

 Value: **StopLoadBalancerListener** |
|ListenerPort|Integer|Yes|80|The frontend listening port used by the listener.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5xmgl\*\*\*\*\*\*|The ID of the SLB instance to which the listener belongs. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |
|ListenerProtocol|String|No|https|The frontend listening protocol used by the SLB instance.

 **Note:** This parameter is required when listeners with different protocols use the same port. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=StopLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xmgl1miup
&<CommonParameters>

```

Response example

`XML` format

```
<StopLoadBalancerListenerResponse>
			  <RequestId>21D2B318-650E-4B0B-A3B5-693D462247B3</RequestId>
		</StopLoadBalancerListenerResponse>
```

`JSON` format

```
{
	"RequestId":"21D2B318-650E-4B0B-A3B5-693D462247B3"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

