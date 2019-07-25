# DeleteLoadBalancer {#doc_api_Slb_DeleteLoadBalancer .reference}

Deletes a Pay-As-You-Go SLB instance.

**Note:** When you delete a Pay-As-You-Go SLB instance, all associated configurations \(such as listeners or tags\) are deleted at the same time.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancer) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteLoadBalancer| The name of this action.

 Value: **DeleteLoadBalancer**

 |
|LoadBalancerId|String|Yes|lb-bp1h66tp5uat84khmqc9e| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteLoadBalancer
&LoadBalancerId=lb-bp1h66tp5uat84khmqc9e
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteLoadBabalancerResponse>
  <RequestId>E3F602B8-A162-4683-A7EC-49364E597259</RequestId>
</DeleteLoadBabalancerResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"0D9B7343-AC1F-498C-A18A-78FE14A7C3A3"
}
```

If you enable the deletion protection function, the following error is reported when you delete an SLB instance.

-   JSON format

    ``` {#codeblock_wmu_p1v_con}
    
        {
    	"RequestId": "7B7AB375-1EA6-4A18-9D1C-F258F2D57638",
    	"HostId": "slb.aliyuncs.com",
    	"Code": "OperationDenied.DeleteProtectionIsOn",
    	"Message": "The loadbalancer can't be deleted due to DeleteProtection is enabled."
         }
       
    ```

-   XML format

    ``` {#codeblock_8zw_rnh_m8c}
    
       <? xml version="1.0" encoding="UTF-8" ? >
            <DeleteLoadBabalancerResponse>
    	<RequestId>7B7AB375-1EA6-4A18-9D1C-F258F2D57638</RequestId>
    	<HostId>slb.aliyuncs.com</HostId>
    	<Code>OperationDenied.DeleteProtectionIsOn</Code>
    	<Message>The loadbalancer can't be deleted due to DeleteProtection is enabled. </Message>
           </DeleteLoadBabalancerResponse>
       
    ```


## Error codes {#section_hpp_3y4_h7g .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

