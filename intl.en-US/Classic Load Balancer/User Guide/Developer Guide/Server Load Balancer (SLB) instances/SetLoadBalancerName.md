# SetLoadBalancerName

Modifies the name of a Server Load Balancer \(SLB\) instance.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerName|The name of this action.

 Value: **SetLoadBalancerName** |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08e\*\*\*\*\*\*|The ID of the SLB instance. |
|LoadBalancerName|String|Yes|abc1|The name of the SLB instance.

 The name must be 2 to 128 characters in length. It can contain letters, numbers, periods \(.\), underscores \(\_\), and hyphens \(-\). |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=SetLoadBalancerName
&LoadBalancerId=lb-bp1b6c719dfa08e******
&LoadBalancerName=abc1
&<CommonParameters>

```

Response example

`XML` format

```
<SetLoadBalancerStatusResponse>
	  <RequestId>3C7F675E-9F82-4806-BA47-FF57E3ACC850</RequestId>
</SetLoadBalancerStatusResponse>
```

`JSON` format

```
{
	"RequestId":"3C7F675E-9F82-4806-BA47-FF57E3ACC850"
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

