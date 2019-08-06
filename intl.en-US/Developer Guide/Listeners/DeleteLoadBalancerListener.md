# DeleteLoadBalancerListener {#doc_api_Slb_DeleteLoadBalancerListener .reference}

Deletes a listener.

**Note:** Only a listener in the **stopped** or**running** state can be deleted.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancerListener) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteLoadBalancerListener| The name of this action.

 Value: **DeleteLoadBalancerListener**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5xmgl1miup| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xmgl1miup
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteLoadBalancerListenerResponse>
  <RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
</DeleteLoadBalancerListenerResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"791D8B68-AE0F-4174-AF54-088C8B3C5D54"
}
```

## Error codes {#section_zm9_c9h_ua2 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

