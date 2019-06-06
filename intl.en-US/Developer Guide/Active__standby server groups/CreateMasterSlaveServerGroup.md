# CreateMasterSlaveServerGroup {#doc_api_879478 .reference}

Creates an active/standby server group.

An active/standby server group can only contain two ECS instances. One is the active backend server and the other one is the standby backend server.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateMasterSlaveServerGroup| The name of this action. Value: **CreateMasterSlaveServerGroup**

 |
|LoadBalancerId|String|Yes|lb-bp1hv944r69al4j9jkmvx| The ID of the SLB instance.

 |
|MasterSlaveBackendServers|String|Yes|\[\{'ServerId':'vm-233','Port':'80','Weight':'100','ServerType':'Master'\},\{'ServerId':'vm-232','Port':'90','Weight':'100''ServerType':'Slave'\}\]| A list of backend servers in the active/standby server group.

 An active/standby server group can contain a maximum of two backend servers.

 If you do not specify this parameter, an empty list is created.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |
|MasterSlaveServerGroupName|String|No|Group1| Optional. The name of the active/standby server group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|MasterSlaveServerGroupId|String|rsp-cige6j5e7p| The ID of the active/standby server group.

 |
|MasterSlaveBackendServers| | | A list of backend servers in the active/standby server group.

 |
|└ServerId|String|vm-232| The ID of the ECS instance or ENI to be added.

 |
|└Port|Integer|90| The port used by the backend server.

 |
|└Weight|Integer|100| The weight of the backend server.

 |
|└ServerType|String|Slave| The backend server type.

 Valid values: Master | Slave. Default value: Master.

 |
|└Description|String|A description of the active/standby server group| A description of the active/standby server group.

 |
|└Type|String|ecs| The backend server type. Valid values:

 -   **ecs** : ECS instance \(default\)
-   **eni** : Elastic Network Interface \(ENI\)

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateMasterSlaveServerGroup
&LoadBalancerId=lb-bp1hv944r69al4j9jkmvx
&MasterSlaveBackendServers=[{'ServerId':'vm-233','Port':'80','Weight':'100','ServerType':'Master'},{'ServerId':'vm-232','Port':'90','Weight':'100''ServerType':'Slave'}]
&RegionId=cn-hangzhou
&<CommonParameters>
			
```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateMasterSlaveServerGroup>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <MasterSlaveServerGroupId>rsp-cige6j5e7p</MasterSlaveServerGroupId>
  <MasterSlaveBackendServers>
    <MasterSlaveBackendServers>
      <ServerId>vm-233</ServerId>
      <Port>80</Port>
      <Weight>100</Weight>
      <ServerType>Master</ServerType>
    </MasterSlaveBackendServers>
    <MasterSlaveBackendServers>
      <ServerId>vm-232</ServerId>
      <Port>90</Port>
      <Weight>100</Weight>
      <ServerType>Slave</ServerType>
    </MasterSlaveBackendServers>
  </MasterSlaveBackendServers>
</CreateMasterSlaveServerGroup>
			
```

`JSON` format

``` {#json_return_success_demo}
{
	"CreateMasterSlaveServerGroup":{
		"MasterSlaveBackendServers":{
			"MasterSlaveBackendServers":[
				{
					"ServerId":"vm-233",
					"Port":"80",
					"Weight":"100",
					"ServerType":"Master"
				},
				{
					"ServerId":"vm-232",
					"Port":"90",
					"Weight":"100",
					"ServerType":"Slave"
				}
			]
		},
		"MasterSlaveServerGroupId":"rsp-cige6j5e7p",
		"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
	}
}
```

## Error codes { .section}

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|BACKEND\_SERVERS\_NUM\_MUST\_BE\_TWO|Backend servers num must be 2.|The number of backend servers must be 2.|
|400|BACKEND\_SERVERS\_HAVE\_SAME\_PORT\_AND\_SERVERID|Backend servers have same port and serverId.|A virtual server with the same port and server ID already exists in the backend VServer group.|
|400|BACKEND\_SERVERS\_CAN\_ONLY\_CONTAIN\_ONE\_MASTER\_AND\_ONE\_SLAVE|Backend servers can only contain one master and one slave.|The active/standby server group can contain only one active server and one standby server.|
|400|BACKEND\_SERVER\_ID\_CAN\_NOT\_EMPTY|Backend server id can not empty.|You must enter a backend server ID.|
|400|INVALID\_SERVER\_TYPE|Invalid server type.|The server type is invalid.|
|400|BACKEND\_SERVER\_PORT\_CAN\_NOT\_EMPTY|Backend server port can not empty.|You must specify a backend server port.|
|400|RealServerPortNotSupport|Real server port not support.|The backend server port is not supported.|

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

