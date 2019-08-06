# RemoveVServerGroupBackendServers {#doc_api_Slb_RemoveVServerGroupBackendServers .reference}

调用RemoveVServerGroupBackendServers从指定的后端服务器组中移除后端服务器。

**说明：** 如果**BackendServers**中参数的某些后端服务器不存在于这个虚拟服务器组中，会直接忽略，不会报错。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=RemoveVServerGroupBackendServers&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveVServerGroupBackendServers|要执行的操作。

 取值：**RemoveVServerGroupBackendServers**。

 |
|BackendServers|String|是|\[\{'ServerId':'vm-233','Port':'80'\},\{'ServerId':'vm-232','Port':'90'\}\]|服务器组列表。

 单次调用每个服务器组最多可包含20个后端服务器。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|VServerGroupId|String|是|rsp-cige6j5e7p|服务器组ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6j5e7p|服务器组ID。

 |
|BackendServers| | |后端服务器列表。

 |
|ServerId|String|vm-230|ECS实例ID或ENI的实例ID。

 |
|Port|Integer|80|后端服务器使用的端口。

 |
|Weight|Integer|100|后端服务器的权重。

 |
|Description|String|后端服务器组描述。|后端服务器组描述。

 |
|Type|String|ecs|Type后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=RemoveVServerGroupBackendServers
&BackendServers=[{'ServerId':'vm-233','Port':'80'},{'ServerId':'vm-232','Port':'90'}]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveVServerGroupBackendServersResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
	  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>vm-231</ServerId>
			      <Port>70</Port>
			      <Weight>100</Weight>
                              <Type>ecs</Type>
		    </BackendServer>
	  </BackendServers>
</RemoveVServerGroupBackendServersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RemoveVServerGroupBackendServersResponse":{
		"BackendServers":{
			"BackendServer":{
				"ServerId":"vm-231",
				"Port":"70",
				"Weight":"100",
				"Type":"ecs"
			}
		},
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
		"VServerGroupId":"rsp-cige6j5e7p"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

