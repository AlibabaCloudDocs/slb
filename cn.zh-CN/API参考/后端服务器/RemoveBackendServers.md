# RemoveBackendServers {#doc_api_Slb_RemoveBackendServers .reference}

调用RemoveBackendServers移除后端服务器。

**说明：** 如果要移除的后端服务器不在指定的负载均衡实例的服务器列表中，会直接忽略，不会报错。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=RemoveBackendServers&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveBackendServers|要执行的操作。

 取值：**RemoveBackendServers**。

 |
|BackendServers|String|是|\[\{"ServerId":"i-2zej4lxhjoq1icue6kup","Weight":"100"\},\{"ServerId":"i-2ze1u9ywulp5pbvvc7hv","Weight":"100"\}\]|要移除的后端服务器。

 **说明：** 一次调用最多可以移除20个后端服务器。

 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3ahl\*\*\*\*\*|负载均衡实例ID。

 |
|RegionId|String|是|cn-east-hangzhou-01|负载均衡实例的地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01|负载均衡实例ID。

 |
|BackendServers| | |后端服务器列表。

 |
|Description|String|后端服务器|后端服务器组描述。

 |
|ServerId|String|vm-232|后端服务器名称Id，为ECS实例Id。

 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|Weight|Integer|100|后端服务器的权重，范围为**0~100**。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=RemoveBackendServers
&BackendServers=[{"ServerId":"i-2zej4lxhjoq1icue6kup","Weight":"100"},{"ServerId":"i-2ze1u9ywulp5pbvvc7hv","Weight":"100"}]
&LoadBalancerId=lb-bp1qjwo61pqz3ahl*****
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveBackendServersResponse>
		  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
	  <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>vm-231</ServerId>
			      <Weight>100</Weight>
		    </BackendServer>
		    <BackendServer>
			      <ServerId>vm-232</ServerId>
			      <Weight>100</Weight>
		    </BackendServer>
	  </BackendServers>
		</RemoveBackendServersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"vm-233",
				"Weight":100
			},
			{
				"ServerId":"vm-234",
				"Weight":100
			}
		]
	},
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"LoadBalancerId":"139a00604ad-cn-east-hangzhou-01"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

