# DeleteMasterSlaveServerGroup {#doc_api_1025812 .reference}

Deletes an active/standby server group.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteMasterSlaveServerGroup| The name of this action. Value: **DeleteMasterSlaveServerGroup**

 |
|MasterSlaveServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the active/standby server group to be deleted.

 **说明：** An active/standby server group in use cannot be deleted.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |

## Response elements {#resultMapping .section}

|Name|Type|Example value|Description|
|----|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? MasterSlaveServerGroupId=rsp-cige6j5e7p
&RegionId=cn-hangzhou
&Action=DeleteMasterSlaveServerServerGroup
&Tags={"tagKey":"Key1","tagValue":"Value1"}
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

## Errors {#section_vy2_jcc_ygb .section}

[See common errors.](https://error-center.aliyun.com/status/product/Slb)

