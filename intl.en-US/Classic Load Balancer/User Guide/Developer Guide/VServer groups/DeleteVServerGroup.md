# DeleteVServerGroup

Deletes a VServer group.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DeleteVServerGroup&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteVServerGroup|The name of this action.

 Value: **DeleteVServerGroup** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the associated Server Load Balancer \(SLB\) instance belongs. |
|VServerGroupId|String|Yes|rsp-cige6j\*\*\*\*\*|The ID of the VServer group to be deleted.

 **Note:** If the VServer group is in use, it cannot be deleted. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DeleteVServerGroup
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j*****
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
<DeleteVServerGroupResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteVServerGroupResponse>
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

