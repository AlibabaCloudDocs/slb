# DeleteMasterSlaveServerGroup

Deletes an active/standby server group.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DeleteMasterSlaveServerGroup&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteMasterSlaveServerGroup|The name of this action.

 Value: **DeleteMasterSlaveServerGroup** |
|MasterSlaveServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the active/standby server group to be deleted.

 **Note:** An active/standby server group in use cannot be deleted. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the associated Server Load Balancer \(SLB\) instance belongs. |
|OwnerAccount|String|No| | |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DeleteMasterSlaveServerGroup
&MasterSlaveServerGroupId=rsp-cige6******
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`JSON` format

```

{
"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
	
```

`XML` format

```
<DeleteMasterSlaveServerGroupResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteMasterSlaveServerGroupResponse>
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

