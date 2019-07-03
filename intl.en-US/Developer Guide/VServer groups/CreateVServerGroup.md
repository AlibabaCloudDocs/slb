# CreateVServerGroup {#doc_api_Slb_CreateVServerGroup .reference}

Creates a VServer group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateVServerGroup) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateVServerGroup| The name of this action.

 Value: **CreateVServerGroup**

 |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahltv0mw| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|BackendServers|String|No|\[\{'ServerId':'vm-233','Port':'80','Weight':'100'\},\{'ServerId':'vm-232','Port':'90','Weight':'100'\},\{'ServerId':'vm-231','Port':'70','Weight':'100'\}\]| Optional. The list of backend servers to be added to the VServer group.

 The value is a JSON string with the JsonList structure. For each request, the list can contain up to 20 backend servers.

 -   **ServerId**: the backend server ID, which is the ECS instance ID. It is a required parameter of string type.
-   **Port**: the port used by the backend server. It is a required parameter of integer type with the value range of 1 to 65535.
-   **Weight**: the weight of the backend server. It is a required parameter of integer type with the value range of 0 to 100.

 |
|VServerGroupName|String|No|Group1| Optional. The name of the VServer group.

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
|└Description|String|VServer group| A description of the VServer group.

 |
|└Type|String|Type| The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateVServerGroup
&LoadBalancerId=lb-bp1qjwo61pqz3ahltv0mw
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateVServerGroupResponse>
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
</CreateVServerGroupResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
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
```

## Error codes {#section_tqp_1dk_gvr .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

