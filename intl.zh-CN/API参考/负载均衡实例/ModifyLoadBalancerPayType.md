# ModifyLoadBalancerPayType {#doc_api_Slb_ModifyLoadBalancerPayType .reference}

调用ModifyLoadBalancerPayType将后付费实例转换为预付费实例。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerPayType&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyLoadBalancerPayType|要执行的操作。

 取值：**ModifyLoadBalancerPayType**。

 |
|Duration|Integer|是|1|计费时长。

 -   如果**PricingCycle**为**month**，取值**1-9**。
-   如果**PricingCycle**为**year**，取值**1-3**。

 |
|LoadBalancerId|String|是|lb-test|负载均衡实例的ID。

 |
|PayType|String|是|PrePay|实例的计费类型，取值：

 -   **PayOnDemand**：按量付费。

 |
|PricingCycle|String|是|month|计费周期。

 取值：**year|month** 。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|AutoPay|Boolean|否|true|是否自动付费。取值：**true|false**

 -   **true**：自动续费。
-   **false（默认值）**：不自动续费。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|OrderId|Long|201429619788910|预付费实例的订单ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyLoadBalancerPayType
&LoadBalancerId=lb-test
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyLoadBalancerPayTypeResponse>
			  <RequestId>B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8</RequestId>
	  <OrderId>202778336800296</OrderId>
		</ModifyLoadBalancerPayTypeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"OrderId":202778336800296,
	"RequestId":"B680E8A4-E2A2-4E85-80DB-A0E6D4038CF8"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|不允许该操作，存在未完成的购买订单。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

