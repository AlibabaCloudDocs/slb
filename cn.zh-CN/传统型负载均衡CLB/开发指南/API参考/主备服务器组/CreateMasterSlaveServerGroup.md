# CreateMasterSlaveServerGroup

调用CreateMasterSlaveServerGroup创建主备服务器组。一组主备服务器组只能包含两个ECS实例，一个为主服务器，另一个为备服务器。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateMasterSlaveServerGroup&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateMasterSlaveServerGroup|要执行的操作。

 取值：**CreateMasterSlaveServerGroup**。 |
|LoadBalancerId|String|是|lb-bp1hv944r69al4j\*\*\*\*\*\*|负载均衡实例ID。 |
|MasterSlaveBackendServers|String|是|\[\{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","ServerType":"Master","Description":"test-112" \}, \{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","ServerType":"Slave","Description":"test-112" \}\]|主备服务器组列表。

 取值：是一个Json string，其结构是一个JsonList。一次请求中，列表最多支持20个元素。

 -   **ServerId**：String类型，必选，后端服务器实例ID。
-   **Port**：Integer类型，必选，后端服务器使用的端口，取值范围：**1**~**65535**。
-   **Weight**：Integer类型，必选，后端服务器的权重，取值范围：**0**~**100**。
-   **Description**：String类型，非必选，后端服务器描述，长度为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、半角句号（.）和下划线（\_）字符，支持中文。
-   **ServerType**：String类型，表示后端服务器的主备类型，取值：
    -   **Master**：主服务器。
    -   **Slave**：备服务器。
-   **Type**：String类型，表示后端服务器的实例类型，取值：
    -   **ecs**：ECS实例（默认）。
    -   **eni**：弹性网卡实例。
-   **ServerIp**：ECS或者ENI的实例IP。

 一个主备服务器组最多可包含2个后端服务器。

 如果不指定该参数，则创建一个空的主备服务器组列表。

 示例说明如下：

 -   挂载ECS：`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","ServerType":"Master","Description":"test-112" }, { "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","ServerType":"Slave","Description":"test-112" }]`

 -   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "Port":"80","ServerType":"Master","Description":"test-112" }, { "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","ServerType":"Slave","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni","ServerIp": "192.168.**.**", "Port":"80","ServerType":"Master","Description":"test-112" }, { "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni","ServerIp": "192.168.**.**", "Port":"80","ServerType":"Slave","Description":"test-112" }]` |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|MasterSlaveServerGroupName|String|否|Group1|主备虚拟服务器组名称。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MasterSlaveServerGroupId|String|rsp-cige6j\*\*\*\*\*\*|主备服务器组ID。 |
|MasterSlaveBackendServers|Array of MasterSlaveBackendServer| |主备服务器组列表。 |
|MasterSlaveBackendServer| | | |
|ServerId|String|vm-2h\*\*\*\*|要添加的ECS实例ID或者ENI实例ID。 |
|Port|Integer|90|后端服务器使用的端口。 |
|Weight|Integer|100|后端服务器的权重。 |
|ServerType|String|Slave|服务器类型。

 取值：**Master**（默认值）或**Slave**。 |
|Description|String|主备服务器组描述。|主备服务器组描述。 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateMasterSlaveServerGroup
&LoadBalancerId=lb-bp1hv944r69al4j******
&MasterSlaveBackendServers=[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs",  "Port":"80","ServerType":"Master","Description":"test-112" },  { "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs",  "Port":"80","ServerType":"Slave","Description":"test-112" }]
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateMasterSlaveServerGroupResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
      <MasterSlaveServerGroupId>rsp-cige******</MasterSlaveServerGroupId>
      <MasterSlaveBackendServers>
            <MasterSlaveBackendServers>
        	      <ServerId>vm-gtgt***</ServerId>
        	      <Port>80</Port>
        	      <Weight>100</Weight>
			      <ServerType>Master</ServerType>
            </MasterSlaveBackendServers>
            <MasterSlaveBackendServers>
        	      <ServerId>vm-tygtyg****</ServerId>
        	      <Port>90</Port>
        	      <Weight>100</Weight>
			      <ServerType>Slave</ServerType>
            </MasterSlaveBackendServers>
      </MasterSlaveBackendServers>
</CreateMasterSlaveServerGroupResponse>
```

`JSON` 格式

```
{
  "CreateMasterSlaveServerGroup": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "MasterSlaveServerGroupId": "rsp-cige6*****",
    "MasterSlaveBackendServers": {
      "MasterSlaveBackendServers": [
        {
          "ServerId": "vm-hhhh****",
          "Port": "80",
          "Weight": "100",
          "ServerType": "Master"
        },
        {
          "ServerId": "vm-gggg***",
          "Port": "90",
          "Weight": "100",
          "ServerType": "Slave"
        }
      ]
    }
  }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|BACKEND\_SERVERS\_NUM\_MUST\_BE\_TWO|Backend servers num must be 2.|后端服务器数量必须是2。|
|400|BACKEND\_SERVERS\_HAVE\_SAME\_PORT\_AND\_SERVERID|Backend servers have same port and serverId.|后端服务器组中已存在具有相同的端口和服务器ID的虚拟服务器。|
|400|BACKEND\_SERVERS\_CAN\_ONLY\_CONTAIN\_ONE\_MASTER\_AND\_ONE\_SLAVE|Backend servers can only contain one master and one slave.|主备虚拟服务器组只能包含一个主服务器和一个备服务器。|
|400|BACKEND\_SERVER\_ID\_CAN\_NOT\_EMPTY|Backend server id can not empty.|后端服务器ID不能为空。|
|400|INVALID\_SERVER\_TYPE|Invalid server type.|非法的服务器类型。|
|400|BACKEND\_SERVER\_PORT\_CAN\_NOT\_EMPTY|Backend server port can not empty.|后端服务器端口不允许为空。|
|400|RealServerPortNotSupport|Real server port not support.|后端服务器端口不支持。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

