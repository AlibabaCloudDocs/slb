# SetLoadBalancerStatus {#doc_api_Slb_SetLoadBalancerStatus .reference}

调用SetLoadBalancerStatus设置负载均衡实例的状态。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerStatus&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerStatus|要执行的操作。

 取值：**SetLoadBalancerStatus**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08exfuca5|负载均衡实例的ID。

 |
|LoadBalancerStatus|String|是|active|负载均衡实例状态。取值：**active|inactive**。

 -   active（默认值）

当负载均衡实例的状态为active时，实例中的监听可以根据规则转发接收的流量。

实例创建后的状态默认为**active**。

-   inactive

当负载均衡实例的状态为**inactive**时，实例中的监听不会再转发接收的流量。


 **说明：** 当一个实例下的所有监听都被删除后，实例状态会被自动改为**inactive**。

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

http(s)://[Endpoint]/?Action=SetLoadBalancerStatus
&LoadBalancerId=lb-bp1b6c719dfa08exfuca5
&LoadBalancerStatus=active
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerStatusResponse>
			  <RequestId>E6DDFE22-F019-4F34-B8DD-FD14973450A6</RequestId>
		</SetLoadBalancerStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"E6DDFE22-F019-4F34-B8DD-FD14973450A6"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

