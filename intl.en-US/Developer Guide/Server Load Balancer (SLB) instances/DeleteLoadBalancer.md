# DeleteLoadBalancer {#doc_api_879500 .reference}

Call the DeleteLoadBalancer API to delete a Pay-As-You-Go SLB instance.

**Note:** When you delete a Pay-As-You-Go SLB instance, all associated configurations \(such as listeners or tags\) are deleted at the same time.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancer) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteLoadBalancer|The action to perform. Valid value: **DeleteLoadBalancer**

 |
|LoadBalancerId|String|Yes|lb-bp1h66tp5uat84khmqc9e|The ID of the SLB instance

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the SLB instance belongs.

 You can query the region ID by calling the [DescribeRegions](~~27584~~) API.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=DeleteLoadBalancer
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<CommonParameters>

```

Normal response examples

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

## Error codes { .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Operation.NotAllowed|Operation Denied. Unfinished order exists.|The operation is not allowed. An unfinished purchase order exists.|

[Click here to view the error codes.](https://error-center.aliyun.com/status/product/Slb)

