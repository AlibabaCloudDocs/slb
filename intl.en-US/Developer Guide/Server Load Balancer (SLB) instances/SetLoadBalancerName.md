# SetLoadBalancerName {#doc_api_Slb_SetLoadBalancerName .reference}

Modifies the name of an SLB instance.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerName| The name of this action.

 Value: **SetLoadBalancerName**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08exfuca5| The ID of the SLB instance.

 |
|LoadBalancerName|String|Yes|abc1| The name of the SLB instance.

 The name must be 2 to 128 characters in length and can contain letters, numbers, Chinese characters, underscores \(\_\), periods \(.\), and hyphens \(-\). It must start with a letter or a Chinese character.

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to[the list of regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerName
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&LoadBalancerName=abc1
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerNameResponse>
  <RequestId>3C7F675E-9F82-4806-BA47-FF57E3ACC850</RequestId>
</SetLoadBalancerNameResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"3C7F675E-9F82-4806-BA47-FF57E3ACC850"
}
```

## Error codes {#section_3pr_d0p_n4p .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

