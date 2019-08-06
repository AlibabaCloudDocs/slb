# DescribeVServerGroupAttribute {#doc_api_Slb_DescribeVServerGroupAttribute .reference}

Queries the details of a VServer group.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroupAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVServerGroupAttribute| The name of this action.

 Value: **DescribeVServerGroupAttribute**

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region to which the SLB instance belongs.

 |
|VServerGroupId|String|Yes|rsp-cige6j5e7p| The ID of the VServer group to be queried.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group.

 |
|VServerGroupName|String|Group1| The name of the VServer group.

 |
|BackendServers| | | A list of backend servers.

 |
|└ServerId|String|vm-233| The ECS instance ID.

 |
|└Port|Integer|90| The port used by the backend server.

 |
|└Weight|Integer|100| The weight of the backend server.

 |
|└Description|String|A description of the VServer group| A description of the VServer group.

 |
|└Type|String|ecs| The backend server type. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: Elastic Network Interface \(ENI\)

 |
|LoadBalancerId|String|lb-jfakd\*\*\*| The ID of the SLB instance.

 |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j5e7p
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeVServerGroupAttributeResponse>
  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
  <VServerGroupId>rsp-cige6j5e7p</VServerGroupId>
  <VServerGroupName>Group1</VServerGroupName>
  <BackendServers>
    <BackendServer>
      <ServerId>vm-232</ServerId>
      <Port>80</Port>
      <Weight>100</Weight>
    </BackendServer>
    <BackendServer>
      <ServerId>vm-233</ServerId>
      <Port>90</Port>
      <Weight>100</Weight>
    </BackendServer>
  </BackendServers>
</DescribeVServerGroupAttributeResponse>

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
			}
		]
	},
	"RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
	"VServerGroupId":"rsp-cige6j5e7p",
	"VServerGroupName":"Group1"
}
```

## Error codes {#section_smw_cok_83i .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

