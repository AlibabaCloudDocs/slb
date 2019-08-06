# RemoveVServerGroupBackendServers {#doc_api_Slb_RemoveVServerGroupBackendServers .reference}

Removes backend servers from a specified VServer group.

**Note:** If a backend server specified in the **BackendServers** parameter does not exist in the specified VServer group, it is ignored and no error is returned.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=RemoveVServerGroupBackendServers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveVServerGroupBackendServers| The name of this action.

 Value: **RemoveVServerGroupBackendServers**

 |
|BackendServers|String|Yes|\[\{'ServerId':'vm-233','Port':'80'\},\{'ServerId':'vm-232','Port':'90'\}\]| The list of backend servers to be removed from the VServer group.

 Up to 20 backend servers can be removed through one API call.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the VServer group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group.

 |
|BackendServers| | | A list of backend servers in the VServer group.

 |
|└ServerId|String|vm-230| The ECS instance ID or ENI ID.

 |
|└Port|Integer|80| The port used by the backend server.

 |
|└Weight|Integer|100| The weight of the backend server.

 |
|└Description|String|A description of the VServer group| A description of the VServer group.

 |
|└Type|String|ecs| The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=RemoveVServerGroupBackendServers
&BackendServers=[{'ServerId':'vm-233','Port':'80'},{'ServerId':'vm-232','Port':'90'}]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<RemoveVServerGroupBackendServersResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
  <BackendServers>
    <BackendServer>
      <ServerId>vm-231</ServerId>
      <Port>70</Port>
      <Weight>100</Weight>
      <Type>ecs</Type>
    </BackendServer>
  </BackendServers>
</RemoveVServerGroupBackendServersResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RemoveVServerGroupBackendServersResponse":{
		"BackendServers":{
			"BackendServer":{
				"ServerId":"vm-231",
				"Port":"70",
				"Weight":"100",
				"Type":"ecs"
			}
		},
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
		"VServerGroupId":"rsp-cige6j5e7p"
	}
}
```

## Error codes {#section_fcv_wdj_qkm .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

