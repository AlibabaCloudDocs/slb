# AddBackendServers

调用AddBackendServers添加后端服务器。

**说明：** 如果一次请求中添加多个相同的ECS实例，只会取第一个，其他相同实例会被忽略。新增后端服务器不能与同监听下已有服务器重复，否则会报错。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=AddBackendServers&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddBackendServers|要执行的操作。

 取值：**AddBackendServers**。 |
|LoadBalancerId|String|是|lb-2ze7o5h52g02kkzz\*\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-beijing|负载均衡实例所属地域的ID。

 您可以通过调用[DescribeRegions](~~27584~~)获取地域ID。 |
|BackendServers|String|是|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.\*\*.\*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.\*\*.\*\*", "Port":"80","Description":"test-113" \}\]|要添加的后端服务器列表，包含以下参数：

 -   **ServerId**：String类型，必选，后端服务器的实例ID，分为ECS实例ID或者ENI实例ID，当**ServerId**参数值为ENI实例ID时，**Type**参数值必选。
-   **Weight**：后端服务器的权重，取值：**0**~**100**。默认值为**100**。

如果值为0，则不会将请求转发给该后端服务器。

-   **Description**：String类型，非必选，后端服务器描述，长度为1~80个字符，支持中文、字母、数字、短划线（-）、正斜线（/）、半角句号（.）和下划线（\_）。
-   **Type**：后端服务器类型，取值：
    -   **ecs**：ECS实例（默认）。
    -   **eni**：弹性网卡实例。

 **说明：** 只有性能保障型实例支持添加eni类型的后端服务器。

 -   **ServerIp**：ECS或者ENI的实例IP。

 示例说明如下：

 -   挂载ECS示例：`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   挂载ENI：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" }]`
-   挂载ENI多IP：`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]`

 **说明：** 必须是状态为运行中的后端服务器才可以加入负载均衡实例，每次调用最多可添加20个后端服务器。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|lb-2ze7o5h52g02kkzz\*\*\*\*|负载均衡实例ID。 |
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|i-2zej4lxhjoq1icu\*\*\*\*\*|ECS实例ID或ENI实例ID。 |
|Weight|String|100|后端服务器的权重。

 取值：**0~100**

 默认值为**100**，如果值为**0**，则不会将请求转发给该后端服务器。 |
|Description|String|后端服务器|后端服务器描述。 |
|Type|String|ecs|后端服务器类型。

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|RequestId|String|34B82C81-F13B-4EEB-99F6-A048C67CC830|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=AddBackendServers
&RegionId=cn-hangzhou
&LoadBalancerId=lb-2ze7o5h52g02kkzz******
&BackendServers=[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.**.**", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166.**.**", "Port":"80","Description":"test-113" }]
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<AddBackendServersResponse>
    <BackendServers>
        <BackendServer>
            <ServerId>i-2zej4lxhjoq1icu*****</ServerId>
            <Weight>100</Weight>
            <Type>ecs</Type>
        </BackendServer>
        <BackendServer>
            <ServerId>i-2ze1u9ywulp5pbv*****</ServerId>
            <Weight>100</Weight>
            <Type>ecs</Type>
        </BackendServer>
    </BackendServers>
    <RequestId>34B82C81-F13B-4EEB-99F6-A048C67CC830</RequestId>
    <LoadBalancerId>lb-2ze7o5h52g02kkzz*****</LoadBalancerId>
</AddBackendServersResponse>
```

`JSON` 格式

```
{
    "RequestId": "34B82C81-F13B-4EEB-99F6-A048C67CC830",
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-2zej4lxhjoq1icue****",
                "Weight": 100,
                "Type": "ecs"
            },
            {
                "ServerId": "i-2ze1u9ywulp5pbvv****",
                "Weight": 100,
                "Type": "ecs"
            }
        ]
    },
    "LoadBalancerId": "lb-2ze7o5h52g02kkzze****"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|The specified load balancer does not support the network type of the ECS instance.|负载均衡实例不支持此种网络类型的ECS实例，请您换一种网络类型的ECS后再重试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

