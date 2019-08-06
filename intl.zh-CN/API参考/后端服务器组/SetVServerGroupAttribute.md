# SetVServerGroupAttribute {#doc_api_Slb_SetVServerGroupAttribute .reference}

调用SetVServerGroupAttribute修改虚拟服务器组的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetVServerGroupAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetVServerGroupAttribute|要执行的操作。

 取值：**SetVServerGroupAttribute**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡地域ID。

 |
|VServerGroupId|String|是|rsp-cige6j5e7p|服务器组ID。

 |
|BackendServers|String|否|\[\{'ServerId':'vm-233','Port':'80','Weight':'100'\},\{'ServerId':'vm-232','Port':'90','Weight':'100'\},\{'ServerId':'vm-231','Port':'70','Weight':'100'\}\]|虚拟服务器组列表。

 单次调用最多可添加20个后端服务器。

 |
|VServerGroupName|String|否|Group1|虚拟服务器组名称。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6j5e7p|服务器组ID。

 |
|VServerGroupName|String|Group1|虚拟服务器组名称。

 |
|BackendServers| | |后端服务器列表。

 |
|ServerId|String|vm-231|ECS实例ID或ENI实例ID。

 |
|Port|Integer|70|后端服务器使用的端口。

 |
|Weight|Integer|100|后端服务器的权重。

 |
|Description|String|后端服务器组描述。|后端服务器组描述。

 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetVServerGroupAttribute>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>i-bp1ek6yd7jvkxk5y1*****</ServerId>
			      <Port>80</Port>
			      <Weight>100</Weight>
			      <Type>ecs</Type>
		    </BackendServer>
	  </BackendServers>
	  <RequestId>A4FDF333-F904-4540-88FC-ED6F87AEFFCB</RequestId>
	  <VServerGroupId>rsp-bp1d2e3qel****</VServerGroupId>
	  <VServerGroupName>test1</VServerGroupName>
    </SetVServerGroupAttribute>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"A4FDF333-F904-4540-88FC-ED6F87AEFFCB",
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-bp1ek6yd7jvkx*****",
				"Port":80,
				"Weight":100,
				"Type":"ecs"
			}
		]
	},
	"VServerGroupId":"rsp-bp1d2e3*****",
	"VServerGroupName":"test1"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

