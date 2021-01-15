# ModifyLoadBalancerInternetSpec

调用ModifyLoadBalancerInternetSpec修改公网负载均衡实例的计费方式。

修改公网负载均衡实例的计费方式，包括：

-   调整按带宽计费实例的带宽峰值，修改完成后，立即生效。
-   从按流量计费转换为按带宽计费。计费类型的变更从第二天凌晨开始生效。
-   从按带宽计费转换为按流量计费。计费类型的变更从第二天凌晨开始生效。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInternetSpec&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyLoadBalancerInternetSpec|要执行的操作。

 取值：**ModifyLoadBalancerInternetSpec**。 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08ex\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |
|InternetChargeType|String|否|paybytraffic|公网类型实例的付费方式。取值：

 -   **paybybandwidth**：按带宽计费。
-   **paybytraffic**：按流量计费 。

 **说明：** 如果不指定该参数，则表示保持原有的计费方式。 |
|Bandwidth|Integer|否|10|按固定带宽计费方式的公网类型实例的带宽峰值。

 取值：**1**~**5000** Mbps（各地域的带宽峰值会有不同）。

 **说明：** 按流量计费的实例不需要指定该参数（即**InternetChargeType**为**paybytraffic**）。 |
|AutoPay|Boolean|否|false|是否是自动支付预付费公网实例的账单。

 取值：**true**或**false**（默认）。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|Long|201429619788910|预付费实例的订单ID。 |
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifyLoadBalancerInternetSpec
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ModifyLoadBalancerInternetSpecResponse>
      <RequestId>E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED</RequestId>
</ModifyLoadBalancerInternetSpecResponse>
```

`JSON` 格式

```
{
    "RequestId": "E4DD2D80-8DC0-4A2E-BFBA-BE983A31AFED"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|不允许该操作，存在未完成的购买订单。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

