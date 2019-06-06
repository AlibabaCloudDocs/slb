# RemoveBackendServers {#doc_api_874453 .reference}

Removes backend servers.

**Note:** If the ECS instance to be removed does not exist in the specified backend server group, the action is ignored and no error is returned.

## Debug {#apiExplorer .section}

We recommend that you use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to call APIs, generate SDK code examples, perform debug operations, and search for APIs.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|RemoveBackendServers|The name of this action. Value: **RemoveBackendServers**

 |
|BackendServers|String|Yes|\[\{"ServerId":"i-2zej4lxhjoq1icue6kup","Weight":"100"\},\{"ServerId":"i-2ze1u9ywulp5pbvvc7hv","Weight":"100"\}\]|The backend servers to be removed.

 **Note:** Up to 20 backend servers can be removed at a time.

 |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahltv0mw|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-east-hangzhou-01|The ID of the region to which the SLB instance belongs.

 |
|OwnerAccount|String|No|OwnerAccount|Optional. The ID of the account.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01|The ID of the SLB instance.

 |
|BackendServers|N/A|N/A|A list of backend servers.

 |
|└Description|String|Backend servers|A description of the backend server group.

 |
|└ServerId|String|vm-232|The alias of the backend server ID. Value: the ECS instance ID.

 |
|└Type|String|ecs|The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|└Weight|Integer|100|The weight of the backend server. Value range: 0 to 100.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=RemoveBackendServers
&BackendServers=["vm-233","vm-234"]
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<RemoveBackendServersResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
  <BackendServers>
    <BackendServer>
      <ServerId>vm-231</ServerId>
      <Weight>100</Weight>
    </BackendServer>
    <BackendServer>
      <ServerId>vm-232</ServerId>
      <Weight>100</Weight>
    </BackendServer>
  </BackendServers>
</RemoveBackendServersResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"vm-233",
				"Weight":100
			},
			{
				"ServerId":"vm-234",
				"Weight":100
			}
		]
	},
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"LoadBalancerId":"139a00604ad-cn-east-hangzhou-01"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

