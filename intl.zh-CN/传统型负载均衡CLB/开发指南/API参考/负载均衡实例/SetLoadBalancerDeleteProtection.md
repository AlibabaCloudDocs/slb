# SetLoadBalancerDeleteProtection

调用SetLoadBalancerDeleteProtection设置实例删除保护状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerDeleteProtection&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerDeleteProtection|要执行的操作。

 取值：**SetLoadBalancerDeleteProtection**。 |
|DeleteProtection|String|是|off|负载均衡删除保护状态。

 取值：**on\|off**。 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08e\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|791D8B68-AE0F-4174-AF54-088C8B3C5D54|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetLoadBalancerDeleteProtection
&DeleteProtection=off
&LoadBalancerId=lb-bp1b6c719dfa08e*****
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetLoadBalancerDeleteProtectionResponse>
	  <RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
    </SetLoadBalancerDeleteProtectionResponse>
```

`JSON` 格式

```
{
    "RequestId": "791D8B68-AE0F-4174-AF54-088C8B3C5D54"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

