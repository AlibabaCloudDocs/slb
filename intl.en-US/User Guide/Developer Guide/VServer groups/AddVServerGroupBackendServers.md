# AddVServerGroupBackendServers

Adds backend servers to a specified VServer group.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|AddVServerGroupBackendServers|The operation that you want to perform.

 Set the value to **AddVServerGroupBackendServers**. |
|BackendServers|String|Yes|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. \*\*. \*\*", "Port":"80","Description":"test-113" \}\]|The list of backend servers that you want to add to the VServer group. You can add up to 20 backend servers in each call.

 The following parameters are used to specify a list of backend servers:

 -   **ServerId**: the instance ID of the backend server. You can specify the ID of an Elastic Compute Service \(ECS\) instance or an elastic network interface \(ENI\).
-   **Port**: the port that is used by the backend server. This parameter is required. Valid values: **1 to 65535**.
-   **Weight**: the weight of the backend server. Valid values: 0 to 100. Default value: 100. If the value is set to 0, no requests are forwarded to the backend server.
-   **Type**: the type of backend server. Valid values:
    -   **ecs**: ECS instance. This is the default value.
    -   **eni**: elastic network interface \(ENI\).
-   **Description**: the description of the backend server. This parameter is optional and must be set to a string. The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **ServerIp**: the IP address of the ECS instance or ENI.

 Examples:

 -   ECS instance:`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port": "80", "Description": "test-112" }].`
-   ENI:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   ENI with multiple IP addresses:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]` |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |
|VServerGroupId|String|Yes|rsp-cige6\*\*\*\*\*\*|The ID of the VServer group. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*\*|The ID of the VServer group. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|vm-231|The ID of the ECS instance or ENI. |
|Port|Integer|70|The port that is used by the backend server. |
|Weight|Integer|100|The weight of the backend server. |
|Description|String|The description of the VServer group.|The description of the VServer group. |
|Type|String|ecs|The type of backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI. |
|RequestId|String|9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=AddVServerGroupBackendServers
&BackendServers=[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]
&RegionId=cn-hangzhou
&VServerGroupId=rsp-cige6******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<AddVServerGroupBackendServersResponse>
      <RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
      <VServerGroupId>rsp-cige6*****</VServerGroupId>
      <BackendServers>
            <BackendServer>
                  <ServerId>vm-233</ServerId>
                  <Port>80</Port>
                  <Weight>100</Weight>
            </BackendServer>
            <BackendServer>
                  <ServerId>vm-232</ServerId>
                  <Port>90</Port>
                  <Weight>100</Weight>
            </BackendServer>
            <BackendServer>
                  <ServerId>vm-231</ServerId>
                  <Port>70</Port>
                  <Weight>100</Weight>
            </BackendServer>
      </BackendServers>
</AddVServerGroupBackendServersResponse>
```

`JSON` format

```
{
  "AddVServerGroupBackendServers": {
    "RequestId": "9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C",
    "VServerGroupId": "rsp-cige6j*****",
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
        },
        {
          "ServerId": "vm-231",
          "Port": "70",
          "Weight": "100"
        }
      ]
    }
  }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

