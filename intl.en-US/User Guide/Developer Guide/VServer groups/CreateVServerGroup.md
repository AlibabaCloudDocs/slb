# CreateVServerGroup

Creates a VServer group and adds backend servers to the VServer group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateVServerGroup&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateVServerGroup|The operation that you want to perform.

 Set the value to **CreateVServerGroup**. |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahl\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is deployed. |
|VServerGroupName|String|No|Group1|The name of the VServer group.

 It must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). |
|BackendServers|String|No|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \}, \{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \}\]|The list of backend servers to be added.

 The value of this parameter is a JSON string in the JSON List structure. You can specify up to 20 elements in a JSON List for each request.

 -   **ServerId**: the ID of the backend server. You can specify the ID of an Elastic Compute Service \(ECS\) instance or an elastic network interface \(ENI\). This parameter is required and must be set to a string.
-   **Port**: the port that is used by the backend server. This parameter is required and must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: the weight of the backend server. This parameter is required and must be set to an integer. Valid values: 0 to 100.
-   **Description**: the description of the backend server. This parameter is optional and must be set to a string. The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
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
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*|The ID of the VServer group. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|vm-2\*\*\*\*|The ID of the ECS instance or ENI. |
|Port|Integer|70|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Description|String|VServer group|The description of the VServer group. |
|Type|String|Type|The type of backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=CreateVServerGroup
&LoadBalancerId=lb-bp1qjwo61pqz3ahl******
&RegionId=cn-hangzhou
&BackendServers= [{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112"  }, { "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112"  }]
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateVServerGroupResponse>
  <VServerGroupId>rsp-bp1i4c******</VServerGroupId>
  <RequestId>3EBBDBAE-8E8B-438F-A109-95C2FDB2C333</RequestId>
  <BackendServers>
        <BackendServer>
              <Type>ecs</Type>
              <ServerId>i-bp1ds2yjlk66********</ServerId>
              <Description>test-11244</Description>
              <Port>80</Port>
              <Weight>100</Weight>
        </BackendServer>
  </BackendServers>
</CreateVServerGroupResponse>
```

`JSON` format

```
{
  "VServerGroupId": "rsp-bp1i4c3******",
  "RequestId": "3EBBDBAE-8E8B-438F-A109-95C2FDB2C333",
  "BackendServers": {
    "BackendServer": [
      {
        "Type": "ecs",
        "ServerId": "i-bp1ds2yjlk666******",
        "Description": "test-11244",
        "Port": 80,
        "Weight": 100
      }
    ]
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

