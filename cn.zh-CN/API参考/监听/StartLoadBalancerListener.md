# StartLoadBalancerListener {#doc_api_Slb_StartLoadBalancerListener .reference}

调用StartLoadBalancerListener启动监听。

启动监听。

在调用该接口时，注意：

-   监听状态必须为stopped时，才可以调用该接口。
-   接口调用成功后，监听进入starting状态。
-   当监听所属负载均衡实例的状态为locked时，调用此接口会失败。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=StartLoadBalancerListener)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|StartLoadBalancerListener|要执行的操作。取值：**StartLoadBalancerListener**

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。取值：1-65535

 |
|LoadBalancerId|String|是|lb-bp13jaf5qli5xmgl1miup|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=StartLoadBalancerListener
&ListenerPort=80
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<StartLoadBalancerListenerResponse>
  <RequestId>CC000321-00F2-49B8-9BCA-60D822414960</RequestId>
</StartLoadBalancerListenerResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"CC000321-00F2-49B8-9BCA-60D822414960"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

