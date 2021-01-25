# SetBackendServers

调用SetBackendServers设置后端服务器权重。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetBackendServers&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetBackendServers|要执行的操作。

 取值：**SetBackendServers**。 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3a\*\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |
|BackendServers|String|是|\[\{ "ServerId": "ecs-\*\*\*\*\*\*FmYAXG", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" \}\]|要添加的后端服务器列表。

 取值：是一个Json string，其结构是一个JsonList。一次请求中，列表最多支持20个元素。

 -   **ServerId**：String类型，必选，后端服务器的实例ID。
-   **Port**：Integer类型，后端服务器使用的端口，取值范围：**1**~**65535**。
-   **Weight**：Integer类型，后端服务器的权重，取值范围：**0**~**100**。
-   **Description**：String类型，非必选，后端服务器描述，长度为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、半角句号（.）和下划线（\_）。
-   **Type**：String类型，表示后端服务器的实例类型，取值：
    -   **ecs**（默认）：ECS实例。
    -   **eni**：弹性网卡实例。只有性能保障型实例支持添加eni类型的后端服务器。
-   **ServerIp**：ECS或者ENI的实例IP。

 示例说明如下：

 -   挂载ECS示例：`[{ "ServerId": "ecs-******FmYAXG", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]`

 **说明：**

-   只有运行中的后端服务器才能被加入负载均衡实例，每次调用最多可添加20个后端服务器。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|lb-bp1qjwo61pqz3a\*\*\*\*\*\*|负载均衡实例ID。 |
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|eni-hhshhs\*\*\*\*|后端服务器ID。 |
|Weight|String|100|后端服务器的权重。 |
|Description|String|后端服务器|后端服务器描述。 |
|Type|String|eni|后端服务器类型，取值：

 -   **ecs**（默认）：ECS实例。
-   **eni**：弹性网卡实例。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SetBackendServers
&LoadBalancerId=lb-bp1qjwo61pqz3a******
&BackendServers=[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs",  "Port":"80","Description":"test-112" }]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<SetBackendServersResponse>
      <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
      <LoadBalancerId>lb-dhf13*******</LoadBalancerId>
      <BackendServers>
            <BackendServer>
                  <ServerId>eni-hg231**</ServerId>
                  <Weight>100</Weight>
                              <Type>eni</Type>
            </BackendServer>
            <BackendServer>
                  <ServerId>eni-hfhf***</ServerId>
                  <Weight>100</Weight>
                              <Type>eni</Type>
            </BackendServer>
      </BackendServers>
</SetBackendServersResponse>
```

`JSON`格式

```
{
    "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
    "LoadBalancerId": "139a00604ad-cn-ea******",
    "BackendServers": {
      "BackendServer": [
        {
          "ServerId": "eni-hg231**",
          "Weight": "100",
          "Type": "eni"
        },
        {
          "ServerId": "eni-hhshhs****",
          "Weight": "100",
          "Type": "eni"
        }
      ]
    }
  }
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

