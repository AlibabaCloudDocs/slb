# StartLoadBalancerListener {#doc_api_Slb_StartLoadBalancerListener .reference}

Starts a listener.

Before you call this API, note the following:

-   The API can be called only when the listener is in the stopped state.
-   After this API is called successfully, the status of the listener changes to starting.
-   If the status of the SLB instance to which the listener belongs is locked, this API cannot be called.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=StartLoadBalancerListener) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|StartLoadBalancerListener| The name of this action.

 Value: **StartLoadBalancerListener**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5xmgl1miup| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The region ID the SLB instance.

 You can query the region ID by calling [DescribeRegions](~~27584~~).

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=StartLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xmgl1miup
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<StartLoadBalancerListenerResponse>
  <RequestId>CC000321-00F2-49B8-9BCA-60D822414960</RequestId>
</StartLoadBalancerListenerResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"CC000321-00F2-49B8-9BCA-60D822414960"
}
```

## Error codes {#section_6ml_f2b_10v .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

