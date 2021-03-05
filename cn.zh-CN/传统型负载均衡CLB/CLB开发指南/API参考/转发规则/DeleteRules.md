# DeleteRules

调用DeleteRules删除转发规则。

## 限制说明

要删除的转发规则列表不能为空，并且可删除的转发规则条目数不能超过10条。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DeleteRules&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteRules|要执行的操作。

 取值：**DeleteRules**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|RuleIds|String|是|\["rule-bp1z9ce\*\*\*\*\*\*","rule-bp1tuc\*\*\*\*\*\*4"\]|要删除的转发规则列表。

 **说明：** 要删除的转发规则列表不能为空，并且可删除的转发规则条目数不能超过10条。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteRules
&RegionId=cn-hangzhou
&RuleIds=["rule-bp1z9ce******","rule-bp1tuc******4"]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DeleteRulesResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteRulesResponse>
```

`JSON`格式

```
{
"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|OperationFailed.ListenerStatusNotSupport|The status of the listener does not support this operation. Please try again later.|监听当前的状态不支持此操作，请稍后重试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

