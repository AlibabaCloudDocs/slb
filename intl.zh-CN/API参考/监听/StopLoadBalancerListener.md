# StopLoadBalancerListener {#doc_api_Slb_StopLoadBalancerListener .reference}

调用StopLoadBalancerListener停止监听。

在调用该接口时，注意：

-   接口调用成功后，监听进入stopped状态。
-   当监听所属负载均衡实例的状态为locked时，调用此接口会失败。

**说明：** 停止监听会使访问中断，请谨慎操作。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=StopLoadBalancerListener&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StopLoadBalancerListener|要执行的操作。

 取值：**StopLoadBalancerListener**。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-bp13jaf5qli5xmgl1miup|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |

## 返回数据 {#resultMapping .section}

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
<StopLoadBalancerListenerResponse>
			  <RequestId>21D2B318-650E-4B0B-A3B5-693D462247B3</RequestId>
		</StopLoadBalancerListenerResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"21D2B318-650E-4B0B-A3B5-693D462247B3"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

