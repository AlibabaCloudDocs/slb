# DescribeMasterSlaveServerGroupAttribute

调用DescribeMasterSlaveServerGroupAttribute查询指定主备服务器组的详细信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroupAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeMasterSlaveServerGroupAttribute|要执行的操作。

 取值：**DescribeMasterSlaveServerGroupAttribute**。 |
|MasterSlaveServerGroupId|String|是|rsp-cige6j\*\*\*\*\*\*|主备服务器组ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|MasterSlaveServerGroupId|String|rsp-cige6\*\*\*\*\*\*|主备服务器组ID。 |
|MasterSlaveServerGroupName|String|Group1|主备服务器组的名称。 |
|MasterSlaveBackendServers|Array| |主备服务器组列表。 |
|MasterSlaveBackendServer| | | |
|ServerId|String|vm-hrf\*\*\*\*\*\*|ECS实例ID或者ENI的实例ID。 |
|Port|Integer|90|后端服务器使用的端口。 |
|Weight|Integer|100|后端服务器的权重。 |
|ServerType|String|Slave|服务器类型，取值：**Master（默认值）\| Slave**。 |
|Description|String|主备服务器组描述。|主备服务器组描述。 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）。
-   **eni**：弹性网卡实例。 |
|LoadBalancerId|String|lb-14fadafw4343a\*\*\*\*\*\*|关联的负载均衡实例ID。 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeMasterSlaveServerGroupAttribute
&MasterSlaveServerGroupId=rsp-cige6j******
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeMasterSlaveServerGroupAttributeResponse>
    <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    <MasterSlaveServerGroupId>rsp-cige6******</MasterSlaveServerGroupId>
    <MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-sshssh****</ServerId>
                <Port>80</Port>
                <Weight>100</Weight>
                <ServerType>Master</ServerType>
          </MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-ffff*****</ServerId>
                <Port>90</Port>
                <Weight>100</Weight>
                <ServerType>Slave</ServerType>
          </MasterSlaveBackendServers>
    </MasterSlaveBackendServers>
</DescribeMasterSlaveServerGroupAttributeResponse>
```

`JSON` 格式

```
{
  "DescribeMasterSlaveServerGroupAttributeResponse": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "MasterSlaveServerGroupId": "rsp-cige6******",
    "MasterSlaveBackendServers": {
      "MasterSlaveBackendServers": [
        {
          "ServerId": "vm-sshssh****",
          "Port": "80",
          "Weight": "100",
          "ServerType": "Master"
        },
        {
          "ServerId": "vm-ffff*****",
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

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

