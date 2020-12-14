# RemoveVServerGroupBackendServers

Deletes a backend server from a specified VServer group.

**Note:** If one or more backend servers specified by **BackendServers** do not exist in the VServer group, the backend servers are ignored and no error message is returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=RemoveVServerGroupBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RemoveVServerGroupBackendServers|The operation that you want to perform.

 Set the value to **RemoveVServerGroupBackendServers**. |
|BackendServers|String|Yes|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. \*\*. \*\*", "Port":"80","Description":"test-113" \}\]|The list of backend servers that you want to delete from the VServer group.

 A VServer group can contain a maximum of 20 backend servers in each call.

 The value of this parameter is a JSON string in the JSON List structure. You can specify up to 20 elements in a JSON List for each request.

 -   **ServerId**: the ID of the backend server. You can specify the ID of an Elastic Compute Service \(ECS\) instance or an elastic network interface \(ENI\). This parameter is required and must be set to a string.
-   **Port**: the port that is used by the backend server. This parameter is required and must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: the weight of the backend server. This parameter is required and must be set to an integer. Valid values: 0 to 100.
-   **Description**: the description of the backend server. This parameter is optional and must be set to a string. The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: the instance type of the backend server. This parameter must be set to a string. Valid values:
    -   ecs: ECS instance. This is the default value.
    -   eni: ENI.
-   **ServerIp**: the IP address of the ECS instance or ENI. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |
|VServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the VServer group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*|The ID of the VServer group. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|vm-230|The ID of the ECS instance or ENI. |
|Port|Integer|80|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Description|String|The description of the VServer group.|The description of the VServer group. |
|Type|String|ecs|Type: the type of backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=RemoveVServerGroupBackendServers
&BackendServers=[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RemoveVServerGroupBackendServersResponse>
	  <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
	  <VServerGroupId>rsp-cige6******</VServerGroupId>
	  <BackendServers>
		    <BackendServer>
			      <ServerId>vm-231</ServerId>
			      <Port>70</Port>
			      <Weight>100</Weight>
                              <Type>ecs</Type>
		    </BackendServer>
	  </BackendServers>
</RemoveVServerGroupBackendServersResponse>
```

`JSON` format

```
{
  "RemoveVServerGroupBackendServersResponse": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "VServerGroupId": "rsp-cige6******",
    "BackendServers": {
      "BackendServer": {
        "ServerId": "vm-231",
        "Port": "70",
        "Weight": "100",
        "Type": "ecs"
      }
    }
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

