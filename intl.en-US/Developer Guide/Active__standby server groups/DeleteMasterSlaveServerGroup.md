# DeleteMasterSlaveServerGroup {#doc_api_Slb_DeleteMasterSlaveServerGroup .reference}

Deletes an active/standby server group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteMasterSlaveServerGroup) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteMasterSlaveServerGroup| The name of this action.

 Value: **DeleteMasterSlaveServerGroup**

 |
|MasterSlaveServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the active/standby server group.

 **Note:** An active/standby server group in use cannot be deleted.

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteMasterSlaveServerGroup
&MasterSlaveServerGroupId=rsp-cige6j5e7p
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteMasterSlaveServerGroupResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteMasterSlaveServerGroupResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Error codes {#section_q3b_68h_ovf .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

