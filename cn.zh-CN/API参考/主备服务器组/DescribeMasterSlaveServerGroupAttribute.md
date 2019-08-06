# DescribeMasterSlaveServerGroupAttribute {#doc_api_Slb_DescribeMasterSlaveServerGroupAttribute .reference}

调用DescribeMasterSlaveServerGroupAttribute查询指定主备服务器组的详细信息。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroupAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeMasterSlaveServerGroupAttribute|要执行的操作。

 取值：**DescribeMasterSlaveServerGroupAttribute**。

 |
|MasterSlaveServerGroupId|String|是|rsp-cige6j5e7p|主备服务器组ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|MasterSlaveServerGroupId|String|rsp-cige6j5e7p|主备服务器组ID。

 |
|MasterSlaveServerGroupName|String|Group1|主备服务器组的名称。

 |
|MasterSlaveBackendServers| | |主备服务器组列表。

 |
|ServerId|String|vm-233|ECS实例ID或者ENI的实例ID。

 |
|Port|Integer|90|后端服务器使用的端口。

 |
|Weight|Integer|100|后端服务器的权重。

 |
|ServerType|String|Slave|服务器类型，取值：**Master（默认值）| Slave**。

 |
|Description|String|主备服务器组描述。|主备服务器组描述。

 |
|Type|String|ecs|后端服务器类型，取值：

 -   **ecs**：ECS实例（默认）
-   **eni**：弹性网卡实例

 |
|LoadBalancerId|String|lb-14fadafw4343affllxxxx|关联的负载均衡实例ID。

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeMasterSlaveServerGroupAttribute
&MasterSlaveServerGroupId=rsp-cige6j5e7p
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeMasterSlaveServerGroupAttributeResponse>
    <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    <MasterSlaveServerGroupId>rsp-cige6j5e7p</MasterSlaveServerGroupId>
    <MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-233</ServerId>
                <Port>80</Port>
                <Weight>100</Weight>
                <ServerType>Master</ServerType>
          </MasterSlaveBackendServers>
          <MasterSlaveBackendServers>
                <ServerId>vm-232</ServerId>
                <Port>90</Port>
                <Weight>100</Weight>
                <ServerType>Slave</ServerType>
          </MasterSlaveBackendServers>
    </MasterSlaveBackendServers>
</DescribeMasterSlaveServerGroupAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"DescribeMasterSlaveServerGroupAttributeResponse":{
		"MasterSlaveBackendServers":{
			"MasterSlaveBackendServers":[
				{
					"ServerId":"vm-233",
					"Port":"80",
					"Weight":"100",
					"ServerType":"Master"
				},
				{
					"ServerId":"vm-232",
					"Port":"90",
					"Weight":"100",
					"ServerType":"Slave"
				}
			]
		},
		"MasterSlaveServerGroupId":"rsp-cige6j5e7p",
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
	}
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

