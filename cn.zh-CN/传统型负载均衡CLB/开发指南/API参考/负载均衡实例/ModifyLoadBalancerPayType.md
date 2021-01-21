# ModifyLoadBalancerPayType

调用ModifyLoadBalancerPayType将按量计费实例转换为包年包月实例。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerPayType&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyLoadBalancerPayType|要执行的操作。

取值：**ModifyLoadBalancerPayType**。 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08ex\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |
|PayType|String|是|PrePay|实例的计费类型，取值：

-   **PayOnDemand**：按量计费。
-   **PrePay**：包年包月。

按量计费转为包年包月计费，该参数取值只能为**PrePay**，且该实例之前的计费类型必须为**PayOnDemand**。 |
|PricingCycle|String|是|month|计费周期。

取值：**year**或**month** 。

**说明：** 只有当**PayType**的参数取值为**PrePay**时有效，即仅对按量计费实例有效。 |
|Duration|Integer|是|1|计费时长。

-   如果**PricingCycle**为**month**，取值**1-9**。
-   如果**PricingCycle**为**year**，取值**1-3**。

**说明：** 只有当**PayType**的参数取值为**PrePay**时有效，即仅对按量计费实例有效。 |
|AutoPay|Boolean|否|true|是否自动付费。取值：

-   **true**：自动付费。
-   **false（默认值）**：不自动付费。

**说明：** 只有当`PayType`的参数取值为**PrePay**时有效，即仅对按量计费实例有效。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|OrderId|Long|20142961978891|预付费实例的订单ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ModifyLoadBalancerPayType
&LoadBalancerId=lb-bp1b6c719dfa08ex*****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ModifyLoadBalancerPayTypeResponse>
      <RequestId>B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8</RequestId>
      <OrderId>202778336800296</OrderId>
</ModifyLoadBalancerPayTypeResponse>
```

`JSON`格式

```
{
    "RequestId": "B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8", 
    "OrderId": 202778336800296
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|不允许该操作，存在未完成的购买订单。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

