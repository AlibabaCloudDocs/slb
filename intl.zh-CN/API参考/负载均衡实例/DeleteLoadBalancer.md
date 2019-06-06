# DeleteLoadBalancer {#doc_api_879500 .reference}

使用DeleteLoadBalancer删除后付费的负载均衡实例。

**说明：** 如果负载均衡实例上还有监听或者绑定了相应的标签，也会一并被删除。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancer)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLoadBalancer|要执行的操作，取值：**DeleteLoadBalancer**

 |
|LoadBalancerId|String|是|lb-bp1h66tp5uat84khmqc9e|负载均衡实例的ID。

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

/?Action=DeleteLoadBalancer
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLoadBabalancerResponse>
  <RequestId>E3F602B8-A162-4683-A7EC-49364E597259</RequestId>
</DeleteLoadBabalancerResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0D9B7343-AC1F-498C-A18A-78FE14A7C3A3"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Operation.NotAllowed|Operation Denied. Unfinished order exists.|不允许该操作，存在未完成的购买订单。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

