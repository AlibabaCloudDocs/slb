# DescribeMasterSlaveServerGroups {#doc_api_835008 .reference}

Queries the created active/standby server groups.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeMasterSlaveServerGroups| The name of this action. Value: **DescribeMasterSlaveServerGroups**

 |
|LoadBalancerId|String|Yes|lb-bp14zi0n66zpg6ohffzaa| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|IncludeListener|Boolean|No|false| Optional. Indicates whether to return the associated listener information. Default value: **false**

 |

## Response elements {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|MasterSlaveServerGroups| | | A list of active/standby server groups.

 |
|└MasterSlaveServerGroupId|String|rsp-0bfucwuotx| The ID of the active/standby server group.

 |
|└MasterSlaveServerGroupName|String|Group3| The name of the active/standby server group.

 |
|└AssociatedObjects| | | Associated information.

 |
|└Listeners| | | A list of associated listeners.

 |
|└Port|Integer|80| The listening port.

 |
|└Protocol|String|tcp| The protocol used by the listener.

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/?LoadBalancerId=lb-bp14zi0n66zpg6ohffzaa
&RegionId=cn-hangzhou
&Action=DescribeMasterSlaveServerGroups
&IncludeListener=
&Tags={"tagKey":"Key1","tagValue":"Value1"}
&<CommonParameters>

```

Response examples

`XML` format

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

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"265989FE-136B-4D6A-B549-FD40E7A6692D",
	"MasterSlaveServerGroups":{
		"MasterSlaveServerGroup":[
			{
				"MasterSlaveServerGroupId":"rsp-bp1nlyu1366z7",
				"MasterSlaveServerGroupName":"Group3",
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

## Errors { .section}

[See common errors.](https://error-center.aliyun.com/status/product/Slb)

