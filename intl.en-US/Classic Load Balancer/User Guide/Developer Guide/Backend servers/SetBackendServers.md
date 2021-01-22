# SetBackendServers

You can call this operation to specify weights of backend servers.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetBackendServers|The operation that you want to perform.

 Set the value to **SetBackendServers**. |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3a\*\*\*\*\*\*|The ID of the SLB instance that you want to query. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SLB instance. |
|BackendServers|String|Yes|\[\{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" \}\]|The backend servers that you want to add to the SLB instance.

 The value of this parameter is a JSON string with a JSON List structure. You can specify up to 20 elements in a list at a request.

 -   **ServerId**: The instance ID of a backend server. This parameter is required and must be set to a string.
-   **Port**: The port number that is used by the backend server. This parameter must be set to an integer. Valid values: 1 to 65535.
-   **Weight**: The weight of the backend server. This parameter is required and must be set to an integer. Valid values: 0 to 100.
-   **Description**: The description of a backend server. This parameter is optional and must be set to a string. The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: The instance type of the backend server. This parameter must be set to a string. Valid values:
    -   ecs: ECS instance. This is the default value.
    -   eni: Elastic Network Interface \(ENI\).
-   **ServerIp**: the IP address of an ECS instance or ENI instance.

 Examples:

 -   ECS instance:`[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }].`
-   ENI:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   ENI with multiple IP addresses:`[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]`

 **Note:**

-   Only backend servers that are in the running state can be added to the SLB instance. You can add up to 20 backend servers in each call.
-   You can specify ENIs as the backend servers of only guaranteed-performance instances. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoadBalancerId|String|lb-bp1qjwo61pqz3a\*\*\*\*\*\*|The ID of the SLB instance that you want to query. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|i-xxxxxxxxx|The ID of the ECS instance. |
|Weight|String|100|The weight of the backend server. |
|Description|String|The backend server.|The description of the backend server. |
|Type|String|ecs|The type of the backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: ENI instance. |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=SetBackendServers
&LoadBalancerId=lb-bp1qjwo61pqz3a******
&BackendServers=[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs",  "Port":"80","Description":"test-112" }]
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetBackendServersResponse>
      <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
      <LoadBalancerId>lb-dhf13*******</LoadBalancerId>
      <BackendServers>
            <BackendServer>
                  <ServerId>eni-hg231**</ServerId>
                  <Weight>100</Weight>
                              <Type>eni</Type>
            </BackendServer>
            <BackendServer>
                  <ServerId>eni-hfhf***</ServerId>
                  <Weight>100</Weight>
                              <Type>eni</Type>
            </BackendServer>
      </BackendServers>
</SetBackendServersResponse>
```

`JSON` format

```
{
    "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710",
    "LoadBalancerId": "139a00604ad-cn-ea******",
    "BackendServers": {
      "BackendServer": [
        {
          "ServerId": "eni-hg231**",
          "Weight": "100",
          "Type": "eni"
        },
        {
          "ServerId": "eni-hhshhs****",
          "Weight": "100",
          "Type": "eni"
        }
      ]
    }
  }
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

