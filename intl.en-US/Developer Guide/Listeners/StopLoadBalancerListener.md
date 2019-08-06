# StopLoadBalancerListener {#doc_api_883865 .reference}

You can call the StopLoadBalancerListener API to stop a listener.

Before you call the API, note the following:

-   After the API is successfully called, the listener changes to the stopped status.
-   If the status of the SLB instance to which the listener belongs is locked, the API cannot be called.

**Note:** If you stop the listener, your services will be disrupted. Exercise caution when performing this action.

## Debug {#apiExplorer .section}

Click [here](https://api.aliyun.com/#product=Slb&api=StopLoadBalancerListener) to perform a debug operation in OpenAPI Explorer and automatically generate an SDK code example.

## Request parameters {#parameters .section}

|Name|Type|Required?|Example value|Description|
|----|----|---------|-------------|-----------|
|Action|String|Yes|StopLoadBalancerListener| The action to perform. Valid value:**StopLoadBalancerListener**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance. Valid values:**1–65535**

 |
|LoadBalancerId|String|Yes|lb-bp13jaf5qli5xmgl1miup| The ID of the SLB instance

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the SLB instance belongs.

 You can query the region ID by referring to the list of[regions and zones](~~40654~~)or by calling the[DescribeRegions](~~25609~~)API.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=StopLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xmgl1miup
&<Common request parameters>

```

Normal response examples

`XML` format

``` {#xml_return_success_demo}
<StopLoadBanancerListenerStatusResponse>
  <RequestId>21D2B318-650E-4B0B-A3B5-693D462247B3</RequestId>
</StopLoadBanancerListenerStatusResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"21D2B318-650E-4B0B-A3B5-693D462247B3"
}
```

Error response example

`JSON` format

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## Error codes {#section_7fh_wql_3h6 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

