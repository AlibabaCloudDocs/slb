# DeleteMasterSlaveServerGroup {#doc_api_Slb_DeleteMasterSlaveServerGroup .reference}

调用DeleteMasterSlaveServerGroup删除指定的主备服务器组。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DeleteMasterSlaveServerGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteMasterSlaveServerGroup|要执行的操作。

 取值：**DeleteMasterSlaveServerGroup**。

 |
|MasterSlaveServerGroupId|String|是|rsp-cige6j5e7p|主备服务器组ID。

 **说明：** 如果主备服务器组正在使用中，无法删除。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteMasterSlaveServerGroup
&MasterSlaveServerGroupId=rsp-cige6j5e7p
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteMasterSlaveServerGroupResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteMasterSlaveServerGroupResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

