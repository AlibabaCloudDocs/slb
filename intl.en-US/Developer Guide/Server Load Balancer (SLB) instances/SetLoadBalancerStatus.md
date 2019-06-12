# SetLoadBalancerStatus {#doc_api_Slb_SetLoadBalancerStatus .reference}

Sets the status of an SLB instance.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerStatus) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerStatus| The name of this action. Value: **SetLoadBalancerStatus**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08exfuca5| The ID of the SLB instance.

 |
|LoadBalancerStatus|String|Yes|active| The status of the SLB instance. Valid value: **active | inactive**

 -   active \(default value\)

If you set the status of an SLB instance to active, the listeners in the instance can distribute traffic according to the specified rules.

By default, the SLB instance status is **active**.

-   inactive

If you set the status of an SLB instance to **inactive**, the listeners in the instance stops distributing traffic.


 **Note:** The instance status changes to**inactive**if all the listeners of the instance are deleted.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID of an SLB instance, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |
|OwnerAccount|String|No|OwnerAccount| OwnerAccount

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerStatus
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5 
&LoadBalancerStatus=active 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerStatusResponse> 
  <RequestId>E6DDFE22-F019-4F34-B8DD-FD14973450A6</RequestId> 
</SetLoadBalancerStatusResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"E6DDFE22-F019-4F34-B8DD-FD14973450A6"
}
```

## Error codes {#section_5ak_zs6_dui .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

