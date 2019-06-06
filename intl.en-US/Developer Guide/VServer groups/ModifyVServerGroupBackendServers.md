# ModifyVServerGroupBackendServers {#doc_api_879384 .reference}

Modifies the backend servers in a VServer group.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyVServerGroupBackendServers|The name of this action. Value: **ModifyVServerGroupBackendServers**

 |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SLB instance.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p|The ID of the VServer group.

 |
|NewBackendServers|String|No|\[\{'ServerId':'vm-235','Port':'8080','Weight':'100'\},\{'ServerId':'vm-236','Port':'70','Weight':'100'\}\]|The list of new backend servers to be added.

 In one call, a VServer group can contain up to 20 backend servers.

 **Note:** Make sure the number of backend servers in **NewBackendServers** is the same as that in **OldBackendServers**.

 |
|OldBackendServers|String|No|\[\{'ServerId':'vm-233','Port':'80'\},\{'ServerId':'vm-232','Port':'90'\}\]|The list of backend servers to be removed.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroupId|String|rsp-cige6j5e7p|The ID of the VServer group.

 |
|BackendServers|N/A|N/A|A list of backend servers.

 |
|└ServerId|String|vm-236|The ECS instance ID or ENI ID.

 |
|└Port|Integer|70|The port used by the backend server.

 |
|└Weight|Integer|100|The weight of the backend server.

 |
|└Description|String|A description of the backend server|A description of the backend server.

 |
|└Type|String|ecs|The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<ModifyVServerGroupBackendServers>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
  <BackendServers>
    <BackendServer>
      <ServerId>vm-400</ServerId>
      <Port>80</Port>
      <Weight>100</Weight>
    </BackendServer>
    <BackendServer>
      <ServerId>vm-401</ServerId>
      <Port>90</Port>
      <Weight>100</Weight>
    </BackendServer>
  </BackendServers>
</ModifyVServerGroupBackendServers>

```

`JSON` format

``` {#json_return_success_demo}
{
	"ModifyVServerGroupBackendServersResponse":{
		"BackendServers":{
			"BackendServer":[
				{
					"ServerId":"vm-400",
					"Port":"80",
					"Weight":"100"
				},
				{
					"ServerId":"vm-401",
					"Port":"90",
					"Weight":"100"
				}
			]
		},
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
		"VServerGroupId":"rsp-cige6j5e7p"
	}
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

