# SetBackendServers {#doc_api_Slb_SetBackendServers .reference}

Sets the weights of backend severs.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetBackendServers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetBackendServers| The name of this action.

 Value: **SetBackendServers**

 |
|BackendServers|String|Yes|\[\{"ServerId":"vm-233","Weight":"0"\},\{"ServerId":"vm-234","Weight":"0"\}\]| The list of backend servers to be added.

 **Note:** Only backend servers \(ECS instances\) in the running state can be added. You can add up to 20 backend servers at a time.

 |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahltv0mw| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoadBalancerId|String|139a00604ad-cn-east-hangzhou-01| The ID of the SLB instance.

 |
|BackendServers| | | A list of backend servers.

 |
|└ServerId|String|vm-234| The ID of the ECS instance.

 |
|└Weight|String|100| The weight of the backend server.

 |
|└Description|String|Backend server| A description of the backend server.

 |
|└Type|String|ecs| The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetBackendServers
&LoadBalancerId=lb-bp1qjwo61pqz3ahltv0mw
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetBackendServersResponse>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <LoadBalancerId>139a00604ad-cn-east-hangzhou-01</LoadBalancerId>
  <BackendServers>
    <BackendServer>
      <ServerId>eni-231</ServerId>
      <Weight>100</Weight>
      <Type>eni</Type>
    </BackendServer>
    <BackendServer>
      <ServerId>eni-233</ServerId>
      <Weight>100</Weight>
      <Type>eni</Type>
    </BackendServer>
  </BackendServers>
</SetBackendServersResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"eni-231",
				"Weight":"100",
				"Type":"eni"
			},
			{
				"ServerId":"eni-233",
				"Weight":"100",
				"Type":"eni"
			}
		]
	},
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"LoadBalancerId":"139a00604ad-cn-east-hangzhou-01"
}
```

## Error codes {#section_9u8_hqw_4dg .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

