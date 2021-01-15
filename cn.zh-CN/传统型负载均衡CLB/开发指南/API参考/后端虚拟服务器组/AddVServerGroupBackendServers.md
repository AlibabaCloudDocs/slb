# AddVServerGroupBackendServers

调用AddVServerGroupBackendServers向指定的后端服务器组中添加后端服务器。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddVServerGroupBackendServers|要执行的操作。

 取值：**AddVServerGroupBackendServers**。 |
|BackendServers|String|是|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.\*\*.\*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.\*\*.\*\*", "Port":"80","Description":"test-113" \}\]|服务器列表。单次调用最多可添加20个后端服务器。

 服务器列表需要包含以下参数：

 -   **ServerId**：后端服务器的实例ID。为ECS实例ID或者ENI实例ID。
-   **Port**：必选参数，表示后端服务器使用的端口。取值范围：**1~65535**。
-   **Weight**：后端服务器的权重，取值范围：**0**~**100**。默认值为**100**。如果值为0，则不会将请求转发给该后端服务器。
-   **Type**：后端服务器类型，取值：
    -   **ecs**： ECS实例（默认）。
    -   **eni**：弹性网卡实例。
-   **Description**：String类型，非必选，后端服务器描述，长度为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、英文句点（.）和下划线（\_）。
-   **ServerIp**：ECS或者ENI的实例IP。

 示例说明如下：

 -   挂载ECS示例：`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]` |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|VServerGroupId|String|是|rsp-cige6\*\*\*\*\*\*|服务器组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*\*|服务器组ID。 |
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|vm-231|ECS实例ID或者ENI的实例ID。 |
|Port|Integer|70|后端服务器使用的端口。 |
|Weight|Integer|100|后端服务器的权重。 |
|Description|String|后端服务器组|后端服务器组描述。 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AddVServerGroupBackendServers
&BackendServers=[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<AddVServerGroupBackendServersResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
      <VServerGroupId>rsp-cige6*****</VServerGroupId>
      <BackendServers>
            <BackendServer>
                  <ServerId>vm-233</ServerId>
                  <Port>80</Port>
                  <Weight>100</Weight>
            </BackendServer>
            <BackendServer>
                  <ServerId>vm-232</ServerId>
                  <Port>90</Port>
                  <Weight>100</Weight>
            </BackendServer>
            <BackendServer>
                  <ServerId>vm-231</ServerId>
                  <Port>70</Port>
                  <Weight>100</Weight>
            </BackendServer>
      </BackendServers>
</AddVServerGroupBackendServersResponse>
```

`JSON` 格式

```
{
  "AddVServerGroupBackendServers": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "VServerGroupId": "rsp-cige6j*****",
    "BackendServers": {
      "BackendServer": [
        {
          "ServerId": "vm-233",
          "Port": "80",
          "Weight": "100"
        },
        {
          "ServerId": "vm-232",
          "Port": "90",
          "Weight": "100"
        },
        {
          "ServerId": "vm-231",
          "Port": "70",
          "Weight": "100"
        }
      ]
    }
  }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

