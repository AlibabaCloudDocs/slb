# SetVServerGroupAttribute

Modifies the configurations of a vServer group.

This operation allows you to modify only the name of a vServer group and the weights of the backend servers in the vServer group.

-   If you want to modify backend servers in a specified vServer group, call the [ModifyVServerGroupBackendServers](~~35220~~) operation.
-   If you want to add backend servers to a specified vServer group, call the [AddVServerGroupBackendServers](~~35218~~) operation.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer automatically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetVServerGroupAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetVServerGroupAttribute|The operation that you want to perform.

 Set the value to **SetVServerGroupAttribute**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the Server Load Balancer \(SLB\) instance is deployed. This parameter cannot be modified. |
|VServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the vServer group. This parameter cannot be modified. |
|VServerGroupName|String|No|Group1|The name of the vServer group. You can specify a custom name for the vServer group. |
|BackendServers|String|No|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. \*\*. \*\*", "Port":"80","Description":"test-113" \}\]|The backend servers in the vServer group.

 You can add up to 20 backend servers in each call.

 -   **ServerId**: the ID of the backend server. You can specify the ID of an Elastic Compute Service \(ECS\) instance or an elastic network interface \(ENI\). This parameter is required and must be set to a string.
-   **Port**: the port that is used by the backend server. This parameter is required and must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: the weight of the backend server. This parameter is required and must be set to an integer. You can modify this parameter. Valid values: 0 to 100.
-   **Description**: the description of the backend server. This parameter is optional and can be modified. You must set this parameter to a string. The description must be 1 to 80 characters in length, and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: the instance type of the backend server. This parameter must be set to a string. Valid values:
    -   ecs: ECS instance. This is the default value.
    -   eni: ENI.
-   **ServerIp**: the IP address of an ECS instance or ENI.

 Examples:

 -   ECS instance: `[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   ENI: `[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   ENI with multiple IP addresses: `[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]` |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*|The ID of the vServer group. |
|VServerGroupName|String|Group1|The name of the vServer group. |
|BackendServers|Array of BackendServer| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|i-bp1ek6yd7jvkx\*\*\*\*\*|The ID of the ECS instance or ENI. |
|Port|Integer|70|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Description|String|The description of the backend server.|The description of the backend server. |
|Type|String|ecs|The type of the backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=SetVServerGroupAttribute
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetVServerGroupAttributeResponse>
  <BackendServers>
        <BackendServer>
              <ServerId>i-bp1ek6yd7jvkx*****</ServerId>
              <Port>80</Port>
              <Weight>100</Weight>
              <Type>ecs</Type>
        </BackendServer>
  </BackendServers>
  <RequestId>A4FDF333-F904-4540-88FC-ED6F87AEFFCB</RequestId>
  <VServerGroupId>rsp-bp1d2e3*****</VServerGroupId>
  <VServerGroupName>test1</VServerGroupName>
</SetVServerGroupAttributeResponse>
```

`JSON` format

```
{
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-bp1ek6yd7jvkx*****", 
                "Port": 80, 
                "Weight": 100, 
                "Type": "ecs"
            }
        ]
    }, 
    "RequestId": "A4FDF333-F904-4540-88FC-ED6F87AEFFCB", 
    "VServerGroupId": "rsp-bp1d2e3*****", 
    "VServerGroupName": "test1"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

