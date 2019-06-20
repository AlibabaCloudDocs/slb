# SetLoadBalancerDeleteProtection {#doc_api_Slb_SetLoadBalancerDeleteProtection .reference}

调用SetLoadBalancerDeleteProtection设置实例删除保护状态。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerDeleteProtection)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerDeleteProtection|要执行的操作。

 取值：**SetLoadBalancerDeleteProtection**。

 |
|DeleteProtection|String|是|off|负载均衡删除保护状态。

 取值：**on|off**。

 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08e\*\*\*\*\*|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|791D8B68-AE0F-4174-AF54-088C8B3C5D54|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetLoadBalancerDeleteProtection
&DeleteProtection=off
&LoadBalancerId=lb-bp1b6c719dfa08e*****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerDeleteProtectionResponse>
  <RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
</SetLoadBalancerDeleteProtectionResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"791D8B68-AE0F-4174-AF54-088C8B3C5D54"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

