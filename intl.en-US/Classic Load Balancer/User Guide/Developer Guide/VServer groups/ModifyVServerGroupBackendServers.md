# ModifyVServerGroupBackendServers

Replaces backend servers in a specified VServer group.

You can call this operation to replace the backend servers in the specified VServer group. If you want to modify the configuration of the backend servers, such as their weights, see [SetVServerGroupAttribute](~~35217~~).

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=ModifyVServerGroupBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|ModifyVServerGroupBackendServers|The operation that you want to perform.

 Set the value to **ModifyVServerGroupBackendServers**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |
|VServerGroupId|String|Yes|rsp-cige6j\*\*\*\*\*\*|The ID of the VServer group. |
|OldBackendServers|String|No|\[\{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" \}\]|The list of backend servers to be replaced.

 The value of this parameter is a JSON string with a JSON List structure. You can specify up to 20 elements in a list in a request.

 -   **ServerId**: the instance ID of the backend server. This parameter is required and must be set to a string.
-   **Port**: the port that is used by the backend server. This parameter is required and must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: the weight of the backend server. This parameter is required and must be set to an integer. Valid values: 0 to 100.
-   **Description**: the description of the backend server. This parameter is optional. The description must be a string. The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: the instance type of the backend server. This parameter must be set to a string. Valid values:
    -   ecs: Elastic Compute Service \(ECS\) instance. This is the default value.
    -   eni: elastic network interface \(ENI\).
-   **ServerIp**: the IP address of an ECS instance or ENI.

 Examples:

 -   ECS instance:`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port": "80", "Description": "test-112" }].`
-   ENI:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   ENI with multiple IP addresses:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]` |
|NewBackendServers|String|No|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. \*\*. \*\*", "Port":"80","Description":"test-113" \}\]|The list of new backend servers.

 You can specify a maximum of 20 backend servers for each VServer group in each call.

 The value of this parameter is a JSON string with a JSON List structure. You can specify up to 20 elements in a list in a request.

 -   **ServerId**: the instance ID of the backend server. This parameter is required and must be set to a string.
-   **Port**: the port that is used by the backend server. This parameter is required and must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: the weight of the backend server. This parameter is required and must be set to an integer. Valid values: 0 to 100.
-   **Description**: the description of the backend server. This parameter is optional. The description must be a string and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: the instance type of the backend server. This parameter must be set to a string. Valid values:
    -   ecs: ECS instance. This is the default value.
    -   eni: ENI.
-   **ServerIp**: the IP address of an ECS instance or ENI.

 Examples:

 -   ECS instance:`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port": "80", "Description": "test-112" }].`
-   ENI:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   ENI with multiple IP addresses:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]` |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*\*|The ID of the VServer group. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|vm-236|The ID of the ECS instance or ENI. |
|Port|Integer|70|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Description|String|The description of the backend server.|The description of the backend server. |
|Type|String|ecs|Type: the type of the backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<ModifyVServerGroupBackendServersResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
	  <VServerGroupId>rsp-cige6j*****</VServerGroupId>
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
</ModifyVServerGroupBackendServersResponse>
```

`JSON` format

```
{
  "ModifyVServerGroupBackendServersResponse": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "VServerGroupId": "rsp-cige6j*****",
    "BackendServers": {
      "BackendServer": [
        {
          "ServerId": "vm-400",
          "Port": "80",
          "Weight": "100"
        },
        {
          "ServerId": "vm-401",
          "Port": "90",
          "Weight": "100"
        }
      ]
    }
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

