# CreateVServerGroup

调用CreateVServerGroup添加后端服务器组并向指定的后端服务器组中添加后端服务器。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateVServerGroup&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateVServerGroup|要执行的操作。

 取值：**CreateVServerGroup**。 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3ahl\*\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡地域ID。 |
|VServerGroupName|String|否|Group1|虚拟服务器组名称。

 长度限制为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、英文句点（.）和下划线（\_）。 |
|BackendServers|String|否|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.\*\*.\*\*", "Port":"80","Description":"test-112" \}, \{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.\*\*.\*\*", "Port":"80","Description":"test-112" \}\]|需要添加的后端服务器。

 取值：是一个Json string，其结构是一个JsonList。一次请求中，列表最多支持20个元素。

 -   **ServerId**：String类型，必选，后端服务器实例ID，为ECS实例ID或者ENI实例ID。
-   **Port**：Integer类型，必选，后端服务器使用的端口，取值范围：**1**~**65535**。
-   **Weight**：Integer类型，必选，后端服务器的权重，取值范围：**0**~**100**。
-   **Description**：String类型，非必选，后端服务器描述，长度为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、英文句点（.）和下划线（\_）。
-   **Type**：String类型，表示后端服务器的实例类型，取值：
    -   **ecs**：ECS实例（默认）。
    -   **eni**：弹性网卡实例。
-   **ServerIp**：ECS或者ENI的实例IP。

 示例说明如下：

 -   挂载ECS示例：`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]` |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*|后端服务器组ID。 |
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|vm-2\*\*\*\*|ECS实例ID或ENI实例ID。 |
|Port|Integer|70|后端服务器使用的端口。 |
|Weight|Integer|100|后端服务器的权重。 |
|Description|String|后端服务器组|后端服务器组描述。 |
|Type|String|Type|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateVServerGroup
&LoadBalancerId=lb-bp1qjwo61pqz3ahl******
&RegionId=cn-hangzhou
&BackendServers= [{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112"  }, { "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112"  }]
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateVServerGroupResponse>
  <VServerGroupId>rsp-bp1i4c******</VServerGroupId>
  <RequestId>3EBBDBAE-8E8B-438F-A109-95C2FDB2C333</RequestId>
  <BackendServers>
        <BackendServer>
              <Type>ecs</Type>
              <ServerId>i-bp1ds2yjlk66********</ServerId>
              <Description>test-11244</Description>
              <Port>80</Port>
              <Weight>100</Weight>
        </BackendServer>
  </BackendServers>
</CreateVServerGroupResponse>
```

`JSON` 格式

```
{
  "VServerGroupId": "rsp-bp1i4c3******",
  "RequestId": "3EBBDBAE-8E8B-438F-A109-95C2FDB2C333",
  "BackendServers": {
    "BackendServer": [
      {
        "Type": "ecs",
        "ServerId": "i-bp1ds2yjlk666******",
        "Description": "test-11244",
        "Port": 80,
        "Weight": 100
      }
    ]
  }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

