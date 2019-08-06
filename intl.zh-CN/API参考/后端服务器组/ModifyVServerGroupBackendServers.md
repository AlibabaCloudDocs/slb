# ModifyVServerGroupBackendServers {#doc_api_Slb_ModifyVServerGroupBackendServers .reference}

调用ModifyVServerGroupBackendServers替换服务器组中的后端服务器。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=ModifyVServerGroupBackendServers&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ModifyVServerGroupBackendServers|要执行的操作。

 取值：**ModifyVServerGroupBackendServers**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|VServerGroupId|String|是|rsp-cige6j5e7p|服务器组ID。

 |
|NewBackendServers|String|否|\[\{'ServerId':'vm-235','Port':'8080','Weight':'100'\},\{'ServerId':'vm-236','Port':'70','Weight':'100'\}\]|新的后端服务器列表。

 单次调用每个服务器组最多可调用20个后端服务器。

 |
|OldBackendServers|String|否|\[\{'ServerId':'vm-233','Port':'80'\},\{'ServerId':'vm-232','Port':'90'\}\]|要被替换的后端服务器列表。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6j5e7p|服务器组ID。

 |
|BackendServers| | |后端服务器列表。

 |
|ServerId|String|vm-236|ECS实例ID或ENI的实例ID。

 |
|Port|Integer|70|后端服务器使用的端口。

 |
|Weight|Integer|100|后端服务器的权重。

 |
|Description|String|后端服务器描述。|后端服务器描述。

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

http(s)://[Endpoint]/?Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ModifyVServerGroupBackendServersResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
	  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>vm-400</ServerId>
			      <Port>80</Port>
			      <Weight>100</Weight>
		    </BackendServer>
		    <BackendServer>
			      <ServerId>vm-401</ServerId>
			      <Port>90</Port>
			      <Weight>100</Weight>
		    </BackendServer>
	  </BackendServers>
</ModifyVServerGroupBackendServersResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"ModifyVServerGroupBackendServersResponse":{
		"BackendServers":{
			"BackendServer":[
				{
					"ServerId":"vm-400",
					"Port":"80",
					"Weight":"100"
				},
				{
					"ServerId":"vm-401",
					"Port":"90",
					"Weight":"100"
				}
			]
		},
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
		"VServerGroupId":"rsp-cige6j5e7p"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

