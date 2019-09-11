# AddBackendServers {#doc_api_Slb_AddBackendServers .reference}

调用AddBackendServers添加后端服务器。

**说明：** 如果一次请求中添加多个相同的ECS实例，只会取第一个，其他相同实例会被忽略。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=AddBackendServers&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddBackendServers|要执行的操作。

 取值：**AddBackendServers**。

 |
|BackendServers|String|是|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.11.1" \}, \{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168.11.2" \}\]|要添加的后端服务器列表。

 服务器组列表需要包含以下参数：

 -   ServerId：ECS实例ID。
-   Weight：后端服务器的权重，取值：0~100。默认值为100。如果值为0，则不会将请求转发给该后端服务器。
-   Type：后端服务器类型，取值：
    -   ecs: ECS实例（默认）
    -   eni：弹性网卡实例

 **说明：** 

-   后端服务器（ECS实例）必须是运行中才可以加入负载均衡实例，每次调用最多可添加20个后端服务器。
-   只有性能保障型实例支持添加eni类型的后端服务器。

 |
|LoadBalancerId|String|是|lb-2ze7o5h52g02kkzz\*\*\*\*\*\*|负载均衡实例ID。

 |
|RegionId|String|是|cn-beijing|负载均衡实例的ID。

 您可以通过调用[DescribeRegions](~~27584~~)获取地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|lb-2ze7o5h52g02kkzz\*\*\*\*|负载均衡实例ID。

 |
|BackendServers| | |后端服务器列表。

 |
|ServerId|String|i-2zej4lxhjoq1icu\*\*\*\*\*|ECS实例ID或ENI的实例ID。

 |
|Weight|String|100|后端服务器的权重。

 取值：**0~100**

 默认值为**100**，如果值为**0**，则不会将请求转发给该后端服务器。

 |
|Description|String|后端服务器|后端服务器描述。

 |
|Type|String|ecs|后端服务器类型。

 -   ecs：ECS实例（默认）
-   eni：弹性网卡实例

 |
|RequestId|String|34B82C81-F13B-4EEB-99F6-A048C67CC830|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddBackendServers
&LoadBalancerId=lb-2ze7o5h52g02kkzz******
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
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

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-2zej4lxhjoq1icue****",
				"Weight":100,
				"Type":"ecs"
			},
			{
				"ServerId":"i-2ze1u9ywulp5pbvv****",
				"Weight":100,
				"Type":"ecs"
			}
		]
	},
	"RequestId":"34B82C81-F13B-4EEB-99F6-A048C67CC830",
	"LoadBalancerId":"lb-2ze7o5h52g02kkzze****"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|The specified load balancer does not support the network type of the ECS instance.|负载均衡实例不支持此种网络类型的ECS实例，请您换一种网络类型的ECS后再重试。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

