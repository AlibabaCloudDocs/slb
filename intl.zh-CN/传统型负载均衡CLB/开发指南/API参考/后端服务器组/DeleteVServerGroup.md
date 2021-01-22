# DeleteVServerGroup

调用DeleteVServerGroup删除服务器组。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DeleteVServerGroup&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteVServerGroup|要执行的操作。

 取值：**DeleteVServerGroup**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|VServerGroupId|String|是|rsp-cige6j\*\*\*\*\*|服务器组ID。

 **说明：** 如果服务器组被引用，将无法删除。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DeleteVServerGroup
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j*****
&<公共请求参数>
```

正常返回示例

`JSON` 格式

```
{
"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

`XML` 格式

```
<DeleteVServerGroupResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteVServerGroupResponse>
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

