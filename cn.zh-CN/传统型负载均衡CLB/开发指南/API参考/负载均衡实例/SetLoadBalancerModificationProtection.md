# SetLoadBalancerModificationProtection

调用SetLoadBalancerModificationProtection设置负载均衡实例修改保护状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerModificationProtection&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerModificationProtection|要执行的操作：**SetLoadBalancerModifyProtection**。 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08e\*\*\*\*\*|负载均衡实例的ID |
|ModificationProtectionStatus|String|是|ConsoleProtection|负载均衡删除保护状态。

 -   **NonProtection**：不限制修改保护。设置后会清除之前设置的ModificationProtectionReason。
-   **ConsoleProtection**：实例控制台修改保护状态。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|ModificationProtectionReason|String|否|配置变更|设置修改保护状态的原因。

 长度为1~80个英文或中文字符，必须以大小字母或中文开头，可包含数字、英文句点（.）、下划线（\_）和短划线（-）。

 仅在ModificationProtectionStatus为**ConsoleProtection**时有效。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|791D8B68-AE0F-4174-AF54-088C8B3C5D54|请求ID |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetLoadBalancerModificationProtection
&LoadBalancerId=lb-bp1b6c719dfa08e*****
&ModificationProtectionStatus=ConsoleProtection
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<RequestId>791D8B68-AE0F-4174-AF54-088C8B3C5D54</RequestId>
```

`JSON` 格式

```
{"RequestId":"791D8B68-AE0F-4174-AF54-088C8B3C5D54"}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

