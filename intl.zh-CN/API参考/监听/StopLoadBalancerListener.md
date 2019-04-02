# StopLoadBalancerListener {#doc_api_883865 .reference}

使用StopLoadBalancerListener停止监听。

在调用该接口时，注意：

-   接口调用成功后，监听进入stopped状态。
-   当监听所属负载均衡实例的状态为locked时，调用此接口会失败。

**说明：** 停止监听会使访问中断，请谨慎操作。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=StopLoadBalancerListener)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StopLoadBalancerListener|要执行的操作。取值：**StopLoadBalancerListener**

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。取值：**1-65535**

 |
|LoadBalancerId|String|是|lb-bp13jaf5qli5xmgl1miup|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=StopLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=lb-bp13jaf5qli5xmgl1miup
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StopLoadBanancerListenerStatusResponse>
  <RequestId>21D2B318-650E-4B0B-A3B5-693D462247B3</RequestId>
</StopLoadBanancerListenerStatusResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"21D2B318-650E-4B0B-A3B5-693D462247B3"
}
```

异常返回示例

`JSON` 格式

``` {#json_return_failed_demo}
{
	"Message":"The specified parameter is not valid.",
	"RequestId":"0669D684-69D8-408E-A4FA-B9011E0F4E66",
	"HostId":"slb-pop.aliyuncs.com",
	"Code":"InvalidParameter"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

