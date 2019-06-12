# AddBackendServers {#doc_api_Slb_AddBackendServers .reference}

Adds backend servers.

**Note:** If two or more same ECS instances are added in a request, only the first ECS instance is added.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddBackendServers) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddBackendServers| The name of this action. Value:**AddBackendServers**

 |
|BackendServers|String|Yes|\[\{"ServerId":"i-2zej4lxhjoq1icue6kup","Weight":"100"\},\{"ServerId":"i-2ze1u9ywulp5pbvvc7hv","Weight":"100"\}\]| The list of backend servers to be added.

 The list must contain the following parameters:

 -   ServerId: the ID of the ECS instance.
-   Weight: the weight of the backend server. Value range: 0 to 100. Default value: 100. If the weight value of a backend server is 0, no request is distributed to this server.
-   Type: the type of the backend server. Valid values:
    -   ecs: ECS instance \(default\)
    -   eni: Elastic Network Interface \(ENI\)

 **Note:** Only backend servers \(ECS instances\) in the running state can be added. You can add up to 20 backend servers at a time.

 |
|LoadBalancerId|String|Yes|lb-2ze7o5h52g02kkzze7lru| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-beijing| The ID of the region to which the SLB instance belongs.

 To query the region ID, call the[DescribeRegions](~~27584~~)API.

 |
|OwnerAccount|String|No|OwnerAccount| Optional. The account.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|LoadBalancerId|String|lb-2ze7o5h52g02kkzze7lru| The ID of the SLB instance.

 |
|BackendServers| | | A list of backend servers.

 |
|└ServerId|String|i-2zej4lxhjoq1icue6kup| The ECS instance ID or ENI instance ID.

 |
|└Weight|String|100| The weight of the backend server.

 Value range: **0 to 100**

 Default value: **100**. If the value is **0**, no requests are forwarded to the backend server.

 |
|└Description|String|Backend server| A description of the backend server.

 |
|└Type|String|ecs| The type of backend server.

 -   ecs: ECS instance \(Default\)
-   eni: Elastic Network Interface \(ENI\)

 |
|RequestId|String|34B82C81-F13B-4EEB-99F6-A048C67CC830| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=AddBackendServers
&LoadBalancerId=lb-2ze7o5h52g02kkzze7lru 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<AddBackendServersResponse> 
  <BackendServers> 
    <BackendServer> 
      <ServerId>i-2zej4lxhjoq1icue6kup</ServerId> 
      <Weight>100</Weight> 
      <Type>ecs</Type> 
    </BackendServer> 
    <BackendServer> 
      <ServerId>i-2ze1u9ywulp5pbvvc7hv</ServerId> 
      <Weight>100</Weight> 
      <Type>ecs</Type> 
    </BackendServer> 
  </BackendServers> 
  <RequestId>34B82C81-F13B-4EEB-99F6-A048C67CC830</RequestId> 
  <LoadBalancerId>lb-2ze7o5h52g02kkzze7lru</LoadBalancerId> 
</AddBackendServersResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"BackendServers":{
		"BackendServer":[
			{
				"ServerId":"i-2zej4lxhjoq1icue6kup",
				"Weight":100,
				"Type":"ecs"
			},
			{
				"ServerId":"i-2ze1u9ywulp5pbvvc7hv",
				"Weight":100,
				"Type":"ecs"
			}
		]
	},
	"RequestId":"34B82C81-F13B-4EEB-99F6-A048C67CC830",
	"LoadBalancerId":"lb-2ze7o5h52g02kkzze7lru"
}
```

## Error codes {#section_c6p_vt5_uxp .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter|The specified load balancer does not support the network type of the ECS instance.|SLB instances do not support ECS instances of this network type. Please change the ECS network type and try again.|

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

