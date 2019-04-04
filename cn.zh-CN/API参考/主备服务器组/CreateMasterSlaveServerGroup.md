# CreateMasterSlaveServerGroup {#doc_api_1025811 .reference}

使用CreateMasterSlaveServerGroup创建主备服务器组。一组主备服务器组只能包含两个ECS实例，一个为主服务器，另一个为备服务器。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=CreateMasterSlaveServerGroup)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateMasterSlaveServerGroup|要执行的操作。取值：**CreateMasterSlaveServerGroup**

 |
|LoadBalancerId|String|是|lb-bp1hv944r69al4j9jkmvx|负载均衡实例ID。

 |
|MasterSlaveBackendServers|String|是|\[\{'ServerId':'vm-233','Port':'80','Weight':'100','ServerType':'Master'\},\{'ServerId':'vm-232','Port':'90','Weight':'100''ServerType':'Slave'\}\]|主备服务器组列表。

 一个主备服务器组最多可包含2个后端服务器。

 如果不指定该参数，则创建一个空的主备服务器组列表。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|MasterSlaveServerGroupName|String|否|Group1|主备虚拟服务器组名称。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|MasterSlaveServerGroupId|String|rsp-cige6j5e7p|主备服务器组ID。

 |
|MasterSlaveBackendServers| | |主备服务器组列表。

 |
|└ServerId|String|vm-232|要添加的ECS实例ID或者ENI的实例ID。

 |
|└Port|Integer|90|后端服务器使用的端口。

 |
|└Weight|Integer|100|后端服务器的权重。

 |
|└ServerType|String|Slave|服务器类型。

 取值：**Master**（默认值） **| Slave**

 |
|└Description|String|主备服务器组描述。|主备服务器组描述。

 |
|└Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateMasterSlaveServerGroup
&LoadBalancerId=lb-bp1hv944r69al4j9jkmvx
&MasterSlaveBackendServers=[{'ServerId':'vm-233','Port':'80','Weight':'100','ServerType':'Master'},{'ServerId':'vm-232','Port':'90','Weight':'100''ServerType':'Slave'}]
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateMasterSlaveServerGroup>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <MasterSlaveServerGroupId>rsp-cige6j5e7p</MasterSlaveServerGroupId>
  <MasterSlaveBackendServers>
    <MasterSlaveBackendServers>
      <ServerId>vm-233</ServerId>
      <Port>80</Port>
      <Weight>100</Weight>
      <ServerType>Master</ServerType>
    </MasterSlaveBackendServers>
    <MasterSlaveBackendServers>
      <ServerId>vm-232</ServerId>
      <Port>90</Port>
      <Weight>100</Weight>
      <ServerType>Slave</ServerType>
    </MasterSlaveBackendServers>
  </MasterSlaveBackendServers>
</CreateMasterSlaveServerGroup>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"CreateMasterSlaveServerGroup":{
		"MasterSlaveBackendServers":{
			"MasterSlaveBackendServers":[
				{
					"ServerId":"vm-233",
					"Port":"80",
					"Weight":"100",
					"ServerType":"Master"
				},
				{
					"ServerId":"vm-232",
					"Port":"90",
					"Weight":"100",
					"ServerType":"Slave"
				}
			]
		},
		"MasterSlaveServerGroupId":"rsp-cige6j5e7p",
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
	}
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|BACKEND\_SERVERS\_NUM\_MUST\_BE\_TWO|Backend servers num must be 2.|后端服务器数量必须是2。|
|400|BACKEND\_SERVERS\_HAVE\_SAME\_PORT\_AND\_SERVERID|Backend servers have same port and serverId.|后端服务器组中已存在具有相同的端口和服务器ID的虚拟服务器。|
|400|BACKEND\_SERVERS\_CAN\_ONLY\_CONTAIN\_ONE\_MASTER\_AND\_ONE\_SLAVE|Backend servers can only contain one master and one slave.|主备虚拟服务器组只能包含一个主服务器和一个备服务器。|
|400|BACKEND\_SERVER\_ID\_CAN\_NOT\_EMPTY|Backend server id can not empty.|后端服务器ID不能为空。|
|400|INVALID\_SERVER\_TYPE|Invalid server type.|非法的服务器类型。|
|400|BACKEND\_SERVER\_PORT\_CAN\_NOT\_EMPTY|Backend server port can not empty.|后端服务器端口不允许为空。|
|400|RealServerPortNotSupport|Real server port not support.|后端服务器端口不支持。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

