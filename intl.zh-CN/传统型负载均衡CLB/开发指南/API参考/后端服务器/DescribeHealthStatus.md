# DescribeHealthStatus

调用DescribeHealthStatus查询后端服务器的健康状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeHealthStatus&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeHealthStatus|要执行的操作。

 取值：**DescribeHealthStatus**。 |
|LoadBalancerId|String|是|lb-bp1qjwo61pqz3ah\*\*\*\*\*\*|负载均衡实例ID。 |
|ListenerPort|Integer|否|80|负载均衡实例前端使用的端口。

 取值：**1~65535**

 **说明：** 不设置该参数表示获取所有端口的健康检查状态。 |
|ListenerProtocol|String|否|https|负载均衡实例前端使用的协议。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|BackendServers|Array of BackendServer| |后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|i-bp1h5u3fv54ytf\*\*\*\*\*|ECS实例ID或者ENI实例ID。 |
|ServerHealthStatus|String|abnormal|后端服务器的健康状况。

 -   **normal**：后端服务器健康。
-   **abnormal**：后端服务器不健康。
-   **unavailable**：未完成健康检查。 |
|EniHost|String|192.168.\*\*.\*\*|弹性网卡IP。 |
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。 |
|Port|Integer|70|负载均衡实例后端使用的端口。 |
|Protocol|String|https|负载均衡实例前端使用的协议。 |
|ServerIp|String|192.168.\*\*.\*\*|ECS实例的IP。 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**（默认）：ECS实例。
-   **eni**：弹性网卡实例。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeHealthStatus
&LoadBalancerId=lb-bp1qjwo61pqz3ah******
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeHealthStatusResponse>
  <RequestId>E69BA4CE-2B55-45EC-94CA-E47B16759459</RequestId>
  <BackendServers>
        <BackendServer>
              <ListenerPort>80</ListenerPort>
              <ServerId>i-bp1h5u3fv54ytf0******</ServerId>
              <Port>80</Port>
              <ServerIp>192.168.0.**</ServerIp>
              <ServerHealthStatus>abnormal</ServerHealthStatus>
              <Protocol>http</Protocol>
        </BackendServer>
        <BackendServer>
              <ListenerPort>8080</ListenerPort>
              <ServerId>i-bp1h5u3fv54ytf0******</ServerId>
              <Port>80</Port>
              <ServerIp>192.168.0.**</ServerIp>
              <ServerHealthStatus>abnormal</ServerHealthStatus>
              <Protocol>tcp</Protocol>
        </BackendServer>
  </BackendServers>
</DescribeHealthStatusResponse>
```

`JSON`格式

```
{
    "RequestId": "E69BA4CE-2B55-45EC-94CA-E47B16759459", 
    "BackendServers": {
        "BackendServer": [
            {
                "ListenerPort": 80, 
                "ServerId": "i-bp1h5u3fv54ytf*****", 
                "Port": 80, 
                "ServerIp": "192.168.**.**", 
                "ServerHealthStatus": "abnormal", 
                "Protocol": "http"
            }, 
            {
                "ListenerPort": 8080, 
                "ServerId": "i-bp1h5u3fv54ytf0******", 
                "Port": 80, 
                "ServerIp": "192.168.**.**", 
                "ServerHealthStatus": "abnormal", 
                "Protocol": "tcp"
            }
        ]
    }
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

