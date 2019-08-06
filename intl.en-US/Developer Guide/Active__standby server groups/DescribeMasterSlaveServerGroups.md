# DescribeMasterSlaveServerGroups {#doc_api_Slb_DescribeMasterSlaveServerGroups .reference}

Queries the created active/standby server groups.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeMasterSlaveServerGroups) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeMasterSlaveServerGroups| The name of this action.

 Value: **DescribeMasterSlaveServerGroups**

 |
|LoadBalancerId|String|Yes|lb-bp14zi0n66zpg6ohffzaa| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|IncludeListener|Boolean|No|false| Optional. Indicates whether to return the associated listener information. Default value: **false**

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|MasterSlaveServerGroups| | | A list of active/standby server groups.

 |
|└MasterSlaveServerGroupId|String|rsp-0bfucwuotx| The ID of the active/standby server group.

 |
|└MasterSlaveServerGroupName|String|Group3| The name of the active/standby server group.

 |
|└AssociatedObjects| | | The resources associated with the active/standby server group.

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

http(s)://[Endpoint]/? Action=DescribeMasterSlaveServerGroups
&LoadBalancerId=lb-bp14zi0n66zpg6ohffzaa
&RegionId=cn-hangzhou
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
				"MasterSlaveServerGroupName":"Group1",
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

## Error codes {#section_xjy_556_9dm .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

