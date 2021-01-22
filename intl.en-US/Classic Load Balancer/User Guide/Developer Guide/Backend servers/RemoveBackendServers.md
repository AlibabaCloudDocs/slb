# RemoveBackendServers

You can call this operation to remove backend servers.

<note\>If the backend servers are not included in the server list of the specified SLB instance, they cannot be deleted and no error is returned. </note\>

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=RemoveBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|RemoveBackendServers|The operation that you want to perform.

 Set the value to **RemoveBackendServers**. |
|BackendServers|String|Yes|\[\{"ServerId":"i-2zej4lxhjoq\*\*\*", "Type": "ecs","Weight":"100"\}\]|The backend servers to be removed. Valid values:

 -   ServerId: The instance ID of a backend server that is an ECS instance ID. This parameter is required and must be set to a string.
-   Weight: The weight of the backend server. This parameter must be set to an integer. Valid values: 0 to 100.
-   Type: The type of the backend server. Valid values:
    -   ecs: ECS instance. This is the default value.
    -   eni: Elastic Network Interface \(ENI\).

 **Note:** You can add up to 20 backend servers in each call.

 Examples:

 -   Remove an ECS instance:`[{"ServerId":"i-2zej4lxhjoq***", "Type": "ecs","Weight":"100"}].`
-   Remove an ENI:`[{"ServerId":"eni-2ze1sdp5***","Type": "eni","Weight":"100"}].` |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ahl\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SLB instance. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|LoadBalancerId|String|lb-bp1vjkb671z53\*\*\*\*\*\*\*|The ID of the SLB instance. |
|BackendServers|Array| |The list of backend servers. |
|BackendServer| | | |
|Description|String|Backend servers|The description of the backend server group. |
|ServerId|String|i-jjgjgjgggd\*\*\*\*\*\*|The instance ID of the backend server. |
|Type|String|ecs|The type of the backend server. Valid values:

 -   **ecs**: ECS instance. This is the default value.
-   **eni**: Elastic Network Interface \(ENI\). |
|Weight|Integer|100|The weight of the backend server. Valid values: **0 to 100**. |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=RemoveBackendServers
&BackendServers=[{"ServerId":"i-2zej4lxhjoq***", "Type": "ecs","Weight":"100"}]
&LoadBalancerId=lb-bp1qjwo61pqz3ahl*****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<RemoveBackendServers>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <LoadBalancerId>lb-bp1vjkb671z53cy******</LoadBalancerId>
  <BackendServers>
        <BackendServer>
              <ServerId>i-jjgjgjg*****</ServerId>
              <Weight>100</Weight>
        </BackendServer>
        <BackendServer>
              <ServerId>i-jjgjgituitu****</ServerId>
              <Weight>100</Weight>
        </BackendServer>
  </BackendServers>
</RemoveBackendServers>
```

`JSON` format

```
{
    "RequestId": "365F4154-92F6-4AE4-92F8-7FF34B540710", 
    "LoadBalancerId": "lb-bp1vjkb671z53cy******", 
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-jjgjgjg*****", 
                "Weight": 100
            }, 
            {
                "ServerId": "i-jjgjgituitu****", 
                "Weight": 100
            }
        ]
    }
}
```

## Error code

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

