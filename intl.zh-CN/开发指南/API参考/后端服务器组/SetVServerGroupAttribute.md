# SetVServerGroupAttribute

调用SetVServerGroupAttribute修改虚拟服务器组的配置。

该接口只能用于修改后端服务器的权重和虚拟服务器名称：

-   如果您需要修改后端服务器组，请参见接口[ModifyVServerGroupBackendServers](~~35220~~)。
-   如果您需要添加后端服务器，请参见接口[AddVServerGroupBackendServers](~~35218~~)。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetVServerGroupAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetVServerGroupAttribute|要执行的操作。

 取值：**SetVServerGroupAttribute**。 |
|RegionId|String|是|cn-hangzhou|负载均衡地域ID，不可更改。 |
|VServerGroupId|String|是|rsp-cige6\*\*\*\*\*\*|后端服务器组ID，不可更改。 |
|VServerGroupName|String|否|Group1|虚拟服务器组名称，可自定义更改。 |
|BackendServers|String|否|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.\*\*.\*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.\*\*.\*\*", "Port":"80","Description":"test-113" \}\]|虚拟服务器组列表。

 单次调用最多可添加20个后端服务器。

 -   **ServerId**：String类型，必选，后端服务器的实例ID或ENI实例ID。
-   **Port**：Integer类型，必选，后端服务器使用的端口，取值范围：1~65535。
-   **Weight**（可更改）：Integer类型，必选，后端服务器的权重，取值范围：0~100。
-   **Description**（可更改）：String类型，非必选，后端服务器描述，长度为1~80个字符，允许包含字母、数字、短横线（-）、正斜杠（/）、点号（.）和下划线（\_），支持中文。
-   **Type**：String类型，表示后端服务器的实例类型，取值：
    -   ecs: ECS实例（默认）。
    -   eni：弹性网卡实例。
-   **ServerIp**：ECS或者ENI的实例IP。

 示例说明如下：

 -   挂载ECS示例：`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]` |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*|服务器组ID。 |
|VServerGroupName|String|Group1|虚拟服务器组名称。 |
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|i-bp1ek6yd7jvkx\*\*\*\*\*|ECS实例ID或ENI实例ID。 |
|Port|Integer|70|后端服务器使用的端口。 |
|Weight|Integer|100|后端服务器的权重。 |
|Description|String|后端服务器组描述。|后端服务器组描述。 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SetVServerGroupAttributeResponse>
  <BackendServers>
        <BackendServer>
              <ServerId>i-bp1ek6yd7jvkx*****</ServerId>
              <Port>80</Port>
              <Weight>100</Weight>
              <Type>ecs</Type>
        </BackendServer>
  </BackendServers>
  <RequestId>A4FDF333-F904-4540-88FC-ED6F87AEFFCB</RequestId>
  <VServerGroupId>rsp-bp1d2e3*****</VServerGroupId>
  <VServerGroupName>test1</VServerGroupName>
</SetVServerGroupAttributeResponse>
```

`JSON` 格式

```
{
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-bp1ek6yd7jvkx*****", 
                "Port": 80, 
                "Weight": 100, 
                "Type": "ecs"
            }
        ]
    }, 
    "RequestId": "A4FDF333-F904-4540-88FC-ED6F87AEFFCB", 
    "VServerGroupId": "rsp-bp1d2e3*****", 
    "VServerGroupName": "test1"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

