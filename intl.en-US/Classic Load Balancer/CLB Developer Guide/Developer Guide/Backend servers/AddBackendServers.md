# AddBackendServers

Adds backend servers to a listener.

**Note:** If the backend servers added to a request are identical, only the first backend server added is accepted. The backend servers you want to add cannot be the same as existing backend servers. Otherwise, an error is reported.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=AddBackendServers&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|AddBackendServers|The name of this action.

 Value: **AddBackendServers** |
|LoadBalancerId|String|Yes|lb-2ze7o5h52g02kkzz\*\*\*\*\*\*|The ID of the Server Load Balancer \(SLB\) instance. |
|RegionId|String|Yes|cn-beijing|The ID of the region to which the SLB instance belongs.

 To query the region ID, call [DescribeRegions](~~27584~~). |
|BackendServers|String|Yes|\[\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. \*\*. \*\*", "Port":"80","Description":"test-112" \},\{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. \*\*. \*\*", "Port":"80","Description":"test-113" \}\]|The list of backend servers to be added.

 The list must contain the following parameters:

 -   **ServerId**: the instance ID of the backend server. It can be the instance ID of an Elastic Compute Service \(ECS\) instance or an Elastic Network Interface \(ENI\). It is a required parameter of string type. If the value of **ServerId** is the instance ID of an ENI, the **ServerIp** parameter and the **Type** parameter are required.
-   **Weight**: the weight of the backend server. Value range: 0 to 100. Default value: 100

If the weight value of a backend server is 0, no request is distributed to this server.

-   **Description**: the description of the backend server. This parameter is optional and of string type. The description must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\).
-   **Type**: the type of the backend server. Valid values:
    -   ecs: ECS instance \(default\)
    -   eni: ENI
-   **ServerIp**: the IP address of the ECS instance or ENI.

 Example:

 -   Example of adding an ECS instance: `[{ "ServerId": "i-xxxxxxxxx", "Weight": "100", "Type": "ecs", "Port":"80","Description":"test-112" }]`
-   Example of adding an ENI: `[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" }]`
-   Example of adding multiple ENIs: `[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]`

 **Note:**

-   Only backend servers in the running state can be added. You can add up to 20 backend servers at a time.
-   ENI-type backend servers are supported only by guaranteed-performance instances. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|34B82C81-F13B-4EEB-99F6-A048C67CC830|The ID of the request. |
|LoadBalancerId|String|lb-2ze7o5h52g02kkzz\*\*\*\*|The ID of the SLB instance. |
|BackendServers|Array| |The list of added backend servers. |
|ServerId|String|i-2zej4lxhjoq1icu\*\*\*\*\*|The instance ID of the backend server. |
|Weight|String|100|The weight of the backend server.

 Value range: **0 to 100**

 Default value: **100**. If the value is set to **0**, no requests are forwarded to the backend server. |
|Type|String|ecs|The type of the backend server.

 -   ecs: ECS instance \(default\)
-   eni: ENI |
|Description|String|Backend server|The description of the backend server. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=AddBackendServers
&LoadBalancerId=lb-2ze7o5h52g02kkzz******
&BackendServers=[{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "192.168. **. **", "Port":"80","Description":"test-112" },{ "ServerId": "eni-xxxxxxxxx", "Weight": "100", "Type": "eni", "ServerIp": "172.166. **. **", "Port":"80","Description":"test-113" }]
&<CommonParameters>
```

Response example

`XML` format

```
<AddBackendServersResponse>
    <BackendServers>
        <BackendServer>
            <ServerId>i-2zej4lxhjoq1icu*****</ServerId>
            <Weight>100</Weight>
            <Type>ecs</Type>
        </BackendServer>
        <BackendServer>
            <ServerId>i-2ze1u9ywulp5pbv*****</ServerId>
            <Weight>100</Weight>
            <Type>ecs</Type>
        </BackendServer>
    </BackendServers>
    <RequestId>34B82C81-F13B-4EEB-99F6-A048C67CC830</RequestId>
    <LoadBalancerId>lb-2ze7o5h52g02kkzz*****</LoadBalancerId>
</AddBackendServersResponse>
```

`JSON` format

```
{
    "RequestId": "34B82C81-F13B-4EEB-99F6-A048C67CC830",
    "BackendServers": {
        "BackendServer": [
            {
                "ServerId": "i-2zej4lxhjoq1icue****",
                "Weight": 100,
                "Type": "ecs"
            },
            {
                "ServerId": "i-2ze1u9ywulp5pbvv****",
                "Weight": 100,
                "Type": "ecs"
            }
        ]
    },
    "LoadBalancerId": "lb-2ze7o5h52g02kkzze****"
}
```

## Errors

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter|The specified load balancer does not support the network type of the ECS instance.|The network type of the specified ECS instance is not supported by the specified SLB instance.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

