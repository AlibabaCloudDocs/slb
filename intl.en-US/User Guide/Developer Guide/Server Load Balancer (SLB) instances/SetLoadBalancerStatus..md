# SetLoadBalancerStatus.

Sets the status of a Server Load Balancer \(SLB\) instance.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerStatus&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerStatus|The name of this action.

 Value: **SetLoadBalancerStatus**. |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08e\*\*\*\*\*\*|The ID of the SLB instance. |
|LoadBalancerStatus|String|Yes|active|The status of the SLB instance. Valid values: **active \| inactive**. Default value: active

 -   active:

If you set the status of an SLB instance to active, the listeners in the SLB instance can distribute traffic according to the specified rules.

By default, the status of a newly created SLB instance is **active**.

-   inactive

If you set the status of an SLB instance to **inactive**, the listeners in the SLB instance stop distributing traffic.


 **Note:** If all the listeners of an SLB instance are deleted, the SLB instance automatically enters the **inactive** state. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=SetLoadBalancerStatus
&LoadBalancerId=lb-bp1b6c719dfa08e******
&LoadBalancerStatus=active
&<CommonParameters>

```

Response example

`XML` format

```
<SetLoadBalancerStatusResponse>
			  <RequestId>E6DDFE22-F019-4F34-B8DD-FD14973450A6</RequestId>
		</SetLoadBalancerStatusResponse>
```

`JSON` format

```
{
	"RequestId":"E6DDFE22-F019-4F34-B8DD-FD14973450A6"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

