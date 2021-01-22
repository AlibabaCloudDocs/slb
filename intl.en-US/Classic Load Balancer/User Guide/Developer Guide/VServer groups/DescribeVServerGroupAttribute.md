# DescribeVServerGroupAttribute

Queries the details of a VServer group.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeVServerGroupAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeVServerGroupAttribute|The name of this action.

 Value: **DescribeVServerGroupAttribute** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the associated Server Load Balancer \(SLB\) instance belongs. |
|VServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the VServer group to be queried. |
|OwnerAccount|String|No| | |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |
|VServerGroupId|String|rsp-cige6\*\*\*\*\*|The ID of the VServer group. |
|VServerGroupName|String|Group1|The name of the VServer group. |
|LoadBalancerId|String|lb-jfakd\*\*\*\*\*|The ID of the SLB instance. |
|BackendServers|Array| |The list of backend servers in the VServer group. |
|ServerId|String|vm-233|The instance ID of the backend server. |
|Port|Integer|90|The port used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Type|String|ecs|The type of the backend server. Valid values:

 -   **ecs**: ECS instance \(Default\)
-   **eni**: ENI |
|Description|String|The description of the VServer group.|The description of the VServer group. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DescribeVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<CommonParameters>

```

Response example

`JSON` format

```
{
  "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
  "VServerGroupId": "rsp-cige6******",
  "VServerGroupName": "Group1",
  "BackendServers": {
    "BackendServer": [
      {
        "ServerId": "vm-233",
        "Port": "80",
        "Weight": "100"
      },
      {
        "ServerId": "vm-232",
        "Port": "90",
        "Weight": "100"
      }
    ]
  }
}
```

`XML` format

```
<DescribeVServerGroupAttributeResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
	  <VServerGroupId>rsp-cige6******</VServerGroupId>
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

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

