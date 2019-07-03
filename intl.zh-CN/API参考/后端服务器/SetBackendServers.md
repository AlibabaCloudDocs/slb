# SetBackendServers {#doc_api_Slb_SetBackendServers .reference}

调用SetBackendServers设置后端服务器权重。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetBackendServers)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetBackendServers|要执行的操作。

 取值：**SetBackendServers**。

 |
|BackendServers|String|是|\[\{"ServerId":"vm-233","Weight":"0"\},\{"ServerId":"vm-234","Weight":"0"\}\]|要添加的后端服务器列表。

 **说明：** 后端服务器（ECS实例）必须是运行中才可以加入负载均衡实例，一次最多可调用20个后端服务器。

 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3ahltv0mw|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01|负载均衡实例ID。

 |
|BackendServers| | |后端服务器列表。

 |
|└ServerId|String|vm-234|ECS实例ID。

 |
|└Weight|String|100|后端服务器的权重。

 |
|└Description|String|后端服务器|后端服务器描述。

 |
|└Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetBackendServers
&LoadBalancerId=lb-bp1qjwo61pqz3ahltv0mw
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetBackendServersResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
  <BackendServers>
    <BackendServer>
      <ServerId>eni-231</ServerId>
      <Weight>100</Weight>
      <Type>eni</Type>
    </BackendServer>
    <BackendServer>
      <ServerId>eni-233</ServerId>
      <Weight>100</Weight>
      <Type>eni</Type>
    </BackendServer>
  </BackendServers>
</SetBackendServersResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"eni-231",
				"Weight":"100",
				"Type":"eni"
			},
			{
				"ServerId":"eni-233",
				"Weight":"100",
				"Type":"eni"
			}
		]
	},
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"LoadBalancerId":"139a00604ad-cn-east-hangzhou-01"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

