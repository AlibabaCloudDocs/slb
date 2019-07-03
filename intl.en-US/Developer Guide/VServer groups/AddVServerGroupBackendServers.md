# AddVServerGroupBackendServers {#doc_api_Slb_AddVServerGroupBackendServers .reference}

Adds backend servers to a specified VServer group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddVServerGroupBackendServers| The name of this action.

 Value: **AddVServerGroupBackendServers**

 |
|BackendServers|String|Yes|\[\{'ServerId':'vm-233','Port':'80','Weight':'100'\},\{'ServerId':'vm-232','Port':'90','Weight':'100'\},\{'ServerId':'vm-231','Port':'70','Weight':'100'\}\]| The list of backend servers to be added. Up to 20 backend servers can be added through one API call.

 The list of backend servers requires the following parameters:

 -   **ServerId**: the ECS instance ID.
-   **Port**: the port used by the backend server. **Value range: 1 to 65535**
-   **Weight**: the weight of the backend server. Value range: 0 to 100. Default value: 100. If the value is 0, no requests are forwarded to the backend server.
-   **Type**: the backend server type. Valid values:
    -   **ecs**: ECS instance \(default\)
    -   **eni**: Elastic Network Interface \(ENI\)

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the VServer group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group.

 |
|BackendServers| | | A list of backend servers.

 |
|└ServerId|String|vm-231| The ECS instance ID or ENI ID.

 |
|└Port|Integer|70| The port used by the backend server.

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

http(s)://[Endpoint]/? Action=AddVServerGroupBackendServers
&BackendServers=[{'ServerId':'vm-233','Port':'80','Weight':'100'},{'ServerId':'vm-232','Port':'90','Weight':'100'},{'ServerId':'vm-231','Port':'70','Weight':'100'}]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<AddVServerGroupBackendServersResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
  <BackendServers>
    <BackendServer>
      <ServerId>vm-233</ServerId>
      <Port>80</Port>
      <Weight>100</Weight>
    </BackendServer>
    <BackendServer>
      <ServerId>vm-232</ServerId>
      <Port>90</Port>
      <Weight>100</Weight>
    </BackendServer>
    <BackendServer>
      <ServerId>vm-231</ServerId>
      <Port>70</Port>
      <Weight>100</Weight>
    </BackendServer>
  </BackendServers>
</AddVServerGroupBackendServersResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"AddVServerGroupBackendServers":{
		"BackendServers":{
			"BackendServer":[
				{
					"ServerId":"vm-233",
					"Port":"80",
					"Weight":"100"
				},
				{
					"ServerId":"vm-232",
					"Port":"90",
					"Weight":"100"
				},
				{
					"ServerId":"vm-231",
					"Port":"70",
					"Weight":"100"
				}
			]
		},
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
		"VServerGroupId":"rsp-cige6j5e7p"
	}
}
```

## Error codes {#section_pev_bf3_fqc .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

