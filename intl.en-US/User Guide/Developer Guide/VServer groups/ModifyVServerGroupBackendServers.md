# ModifyVServerGroupBackendServers

Replaces backend servers in a VServer group.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=ModifyVServerGroupBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|ModifyVServerGroupBackendServers|The name of this action.

 Value: **ModifyVServerGroupBackendServers** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the associated Server Load Balancer \(SLB\) instance belongs. |
|VServerGroupId|String|Yes|rsp-cige6j\*\*\*\*\*\*|The ID of the VServer group. |
|OwnerAccount|String|No| | |
|OldBackendServers|String|No|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*" \}, \{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*" \}\]|The list of backend servers that you want to remove. |
|NewBackendServers|String|No|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \}, \{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \}\]|The list of backend servers that you want to add.

 Up to 20 backend servers can be included in one API call.

 The value of this parameter is a JSON string with a JSON list structure. Up to 20 elements can be contained in a JSON list in one API call.

 -   **ServerId**: the instance ID of the backend server. This element is required. It is of the string type.
-   **Port**: the port used by the backend server. This element is required. It is of the integer type. Value range: 1 to 65535
-   **Weight**: the weight of the backend server. This element is required. It is of the integer type. Value range: 0 to 100
-   **Description**: the description of the backend server. This element is optional. It is of the string type. The description must be 1 to 80 characters in length. It can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*\*|The ID of the VServer group. |
|BackendServers|Array| |The list of backend servers in the VServer group. |
|ServerId|String|vm-236|The instance ID of the backend server, namely, the ECS instance ID or Elastic Network Interface \(ENI\) instance ID. |
|Port|Integer|70|The port used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Type|String|ecs|The type of the backend server. Valid values:

 -   **ecs**: ECS instance \(default\)
-   **eni**: ENI |
|Description|String|The description of the backend server.|The description of the backend server. |

## Examples

Request example

```


http(s)://[Endpoint]/? Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6j******
&<CommonParameters>
			
```

Response example

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

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

