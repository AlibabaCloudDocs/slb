# DescribeHealthStatus {#doc_api_Slb_DescribeHealthStatus .reference}

调用DescribeHealthStatus查询后端服务器的健康状态。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeHealthStatus&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeHealthStatus|要执行的操作。

 取值：**DescribeHealthStatus**。

 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3ahltv0mw|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|ListenerPort|Integer|否|80|负载均衡实例前端使用的端口。

 取值：**1-65535**

 **说明：** 不设置该参数表示获取所有端口的健康检查状态。

 |
|ListenerProtocol|String|否|https|负载均衡实例前端使用的协议。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|BackendServers| | |后端服务器列表。

 |
|ServerId|String|vm-234|ECS实例ID或者ENI的实例ID。

 |
|ServerHealthStatus|String|abnormal|后端服务器的健康状况。

 -   **normal**：后端服务器健康。
-   **abnormal**：后端服务器不健康。
-   **unavailable**：未完成健康检查。

 |
|EniHost|String|192.168.0.1|弹性网卡IP。

 |
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。

 |
|Port|Integer|70|负载均衡实例后端使用的端口。

 |
|Protocol|String|https|负载均衡实例前端使用的协议。

 |
|ServerIp|String|192.168.0.2|ECS实例的IP。

 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeHealthStatus
&LoadBalancerId=lb-bp1qjwo61pqz3ahltv0mw
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeHealthStatusResponse>
	  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>vm-233</ServerId>
			      <ServerHealthStatus>normal</ServerHealthStatus>
		    </BackendServer>
		    <BackendServer>
			      <ServerId>vm-234</ServerId>
			      <ServerHealthStatus>abnormal</ServerHealthStatus>
		    </BackendServer>
	  </BackendServers>
</DescribeHealthStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"196EC328-B566-4226-B435-8697723205EF",
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-bp1do02x7n4nua4k72um",
				"ServerHealthStatus":"abnormal",
				"Port":80,
				"ListenerPort":443
			}
		]
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

