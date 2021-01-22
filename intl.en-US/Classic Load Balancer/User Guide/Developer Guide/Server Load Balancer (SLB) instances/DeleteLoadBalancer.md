# DeleteLoadBalancer

Deletes a Server Load Balancer \(SLB\) instance.

**Note:** After you delete an SLB instance, the listeners and tags of the SLB instance are deleted too.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancer&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteLoadBalancer|The name of this action.

 Value: **DeleteLoadBalancer** |
|LoadBalancerId|String|Yes|lb-bp1h66tp5uat8\*\*\*\*\*\*\*\*|The ID of the SLB instance to be deleted. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DeleteLoadBalancer
&LoadBalancerId=lb-bp1h66tp5uat8********
&<CommonParameters>

```

Response example

`XML` format

```
<DeleteLoadBabalancerResponse>
	  <RequestId>E3F602B8-A162-4683-A7EC-49364E597259</RequestId>
</DeleteLoadBabalancerResponse>
```

`JSON` format

```
{
	"RequestId":"0D9B7343-AC1F-498C-A18A-78FE14A7C3A3"
}
```

If you enable the deletion protection function for the SLB instance, the following error will be reported when you delete the SLB instance.

-   JSON format

    ```
    
        {
    	"RequestId": "7B7AB375-1EA6-4A18-9D1C-F258F2D57638",
    	"HostId": "slb.aliyuncs.com",
    	"Code": "OperationDenied.DeleteProtectionIsOn",
    	"Message": "The loadbalancer can't be deleted due to DeleteProtection is enabled."
         }
       
    ```

-   XML format

    ```
    
       <? xml version="1.0" encoding="UTF-8" ? >
            <DeleteLoadBabalancerResponse>
    	<RequestId>7B7AB375-1EA6-4A18-9D1C-F258F2D57638</RequestId>
    	<HostId>slb.aliyuncs.com</HostId>
    	<Code>OperationDenied.DeleteProtectionIsOn</Code>
    	<Message>The loadbalancer can't be deleted due to DeleteProtection is enabled. </Message>
           </DeleteLoadBabalancerResponse>
       
    ```


## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

