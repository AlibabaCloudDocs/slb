# DeleteVServerGroup {#doc_api_Slb_DeleteVServerGroup .reference}

Deletes a VServer group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DeleteVServerGroup) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DeleteVServerGroup| The name of this action.

 Value: **DeleteVServerGroup**

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the VServer group.

 **Note:** If the VServer group is in use, it cannot be deleted.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DeleteVServerGroup
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DeleteVServerGroupResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
</DeleteVServerGroupResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
}
```

## Error codes {#section_bdc_2ai_zl5 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

