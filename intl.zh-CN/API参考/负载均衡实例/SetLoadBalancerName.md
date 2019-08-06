# SetLoadBalancerName {#doc_api_Slb_SetLoadBalancerName .reference}

调用SetLoadBalancerName修改负载均衡实例的名称。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerName|要执行的操作。

 取值：**SetLoadBalancerName**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08exfuca5|负载均衡实例ID。

 |
|LoadBalancerName|String|是|abc1|负载均衡实例的名称。

 长度为2-128个英文或中文字符，必须以大小字母或中文开头，可包含数字，点号（.），下划线（\_）和短横线（-）。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

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

http(s)://[Endpoint]/?Action=SetLoadBalancerName
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&LoadBalancerName=abc1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerStatusResponse>
	  <RequestId>3C7F675E-9F82-4806-BA47-FF57E3ACC850</RequestId>
</SetLoadBalancerStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"3C7F675E-9F82-4806-BA47-FF57E3ACC850"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

