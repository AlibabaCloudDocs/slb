# ModifyLoadBalancerInstanceSpec {#doc_api_Slb_ModifyLoadBalancerInstanceSpec .reference}

使用ModifyLoadBalancerInstanceSpec修改负载均衡的实例规格。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ModifyLoadBalancerInstanceSpec&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyLoadBalancerInstanceSpec|要执行的操作。

 取值：**ModifyLoadBalancerInstanceSpec**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08exfuca5|负载均衡实例ID。

 |
|LoadBalancerSpec|String|是|slb.s2.small|负载均衡实例的规格。取值：

 -   slb.s1.small

 -   slb.s2.small
-   slb.s2.medium
-   slb.s3.small
-   slb.s3.medium
-   slb.s3.large

 每个地域支持的规格不同。关于每种规格的说明，参见[性能保障型实例](~~27657~~)。

 **说明：** 将共享型实例变更为保障型实例，SLB将有小概率可能性出现短暂的业务中断（10秒-30秒），建议您在业务低谷期进行变配，或者使用GSLB将业务调度至其他的SLB实例后，再进行变配操作。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|AutoPay|Boolean|否|true|是否自动付费。

 -   取值为**true**则自动支付订单。
-   取值为**false**则需要在订单中心中进行支付。

 **说明：** 仅对预付费实例有效。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|OrderId|Long|201429619788910|预付费实例的订单ID。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=ModifyLoadBalancerInstanceSpec
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&LoadBalancerSpec=slb.s2.small
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyLoadBalancerInstanceSpecResponse>
     <RequestId>D456A34A-6E40-4379-8DAF-9175760FE215</RequestId>
  </ModifyLoadBalancerInstanceSpecResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"D456A34A-6E40-4379-8DAF-9175760FE215"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|ModifySpecNotAllowed|LoadBalancerSpec not allowed for this instance|该负责均衡不支持这种实例规格。|
|400|Operation.NotAllowed|Operation Denied. Unfinished purchase exists.|不允许该操作，存在未完成的购买订单。|

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

