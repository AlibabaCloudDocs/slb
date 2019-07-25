# DescribeMasterSlaveServerGroups {#doc_api_Slb_DescribeMasterSlaveServerGroups .reference}

调用DescribeMasterSlaveServerGroups查询主备服务器组列表。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroups)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeMasterSlaveServerGroups|要执行的操作。

 取值：**DescribeMasterSlaveServerGroups**。

 |
|LoadBalancerId|String|是|lb-bp14zi0n66zpg6ohffzaa|负载均衡实例ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |
|IncludeListener|Boolean|否|false|是否返回关联的监听信息，默认值：**false**。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|MasterSlaveServerGroups| | |主备服务器组列表。

 |
|└MasterSlaveServerGroupId|String|rsp-0bfucwuotx|主备服务器组ID。

 |
|└MasterSlaveServerGroupName|String|Group3|主备服务器组的名称。

 |
|└AssociatedObjects| | |关联信息。

 |
|└Listeners| | |监听列表。

 |
|└Port|Integer|80|监听端口。

 |
|└Protocol|String|tcp|监听协议。

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeMasterSlaveServerGroups
&LoadBalancerId=lb-bp14zi0n66zpg6ohffzaa
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeMasterSlaveServerGroupsResponse>
  <RequestId>2631BB5E-B576-4925-BDED-07A66D23E5DE</RequestId>
  <MasterSlaveServerGroups>
    <MasterSlaveServerGroup>
      <MasterSlaveServerGroupId>rsp-bp1ro3mwp2x2m</MasterSlaveServerGroupId>
      <MasterSlaveServerGroupName>test</MasterSlaveServerGroupName>
    </MasterSlaveServerGroup>
  </MasterSlaveServerGroups>
</DescribeMasterSlaveServerGroupsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"265989FE-136B-4D6A-B549-FD40E7A6692D",
	"MasterSlaveServerGroups":{
		"MasterSlaveServerGroup":[
			{
				"MasterSlaveServerGroupId":"rsp-bp1nlyu1366z7",
				"MasterSlaveServerGroupName":"主备1",
				"AssociatedObjects":{
					"Listeners":{
						"Listener":[]
					}
				}
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

