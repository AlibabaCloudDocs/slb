# SetVServerGroupAttribute {#doc_api_Slb_SetVServerGroupAttribute .reference}

Modifies the configurations of a VServer group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetVServerGroupAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetVServerGroupAttribute|The name of this action. Value: **SetVServerGroupAttribute**

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p|The ID of the VServer group.

 |
|BackendServers|String|No|\[\{'ServerId':'vm-233','Port':'80','Weight':'100'\},\{'ServerId':'vm-232','Port':'90','Weight':'100'\},\{'ServerId':'vm-231','Port':'70','Weight':'100'\}\]|Optional. The list of the backend servers in the VServer group.

 Up to 20 backend servers can be added through one API call.

 |
|VServerGroupName|String|No|Group1|Optional. The name of the VServer group. You can modify the name of the VServer group as needed.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroupId|String|rsp-cige6j5e7p|The ID of the VServer group.

 |
|VServerGroupName|String|Group1|The name of the VServer group.

 |
|BackendServers| | |A list of backend servers.

 |
|└ServerId|String|vm-231|The ECS instance ID or ENI ID.

 |
|└Port|Integer|70|The port used by the backend server.

 |
|└Weight|Integer|100|The weight of the backend server.

 |
|└Description|String|A description of the VServer group|A description of the VServer group.

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

http(s)://[Endpoint]/? Action=SetVServerGroupAttribute
&RegionId=cn-hangzhou 
&VServerGroupId=rsp-cige6j5e7p 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetVServerGroupAttribute> 
  <BackendServers> 
    <BackendServer> 
      <ServerId>i-bp1ek6yd7jvkxk5y1*****</ServerId>
      <Port>80</Port> 
      <Weight>100</Weight>
      <Type>ecs</Type>
    </BackendServer>
  </BackendServers> 
  <RequestId>A4FDF333-F904-4540-88FC-ED6F87AEFFCB</RequestId>
  <VServerGroupId>rsp-bp1d2e3qel****</VServerGroupId>
  <VServerGroupName>test1</VServerGroupName>
</SetVServerGroupAttribute> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"A4FDF333-F904-4540-88FC-ED6F87AEFFCB",
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-bp1ek6yd7jvkx*****",
				"Port":80,
				"Weight":100,
				"Type":"ecs"
			}
		]
	},
	"VServerGroupId":"rsp-bp1d2e3*****",
	"VServerGroupName":"test1"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

