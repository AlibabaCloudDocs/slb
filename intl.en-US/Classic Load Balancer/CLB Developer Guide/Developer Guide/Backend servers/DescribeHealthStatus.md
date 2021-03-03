# DescribeHealthStatus

Queries the health status of backend servers.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeHealthStatus&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeHealthStatus|The operation that you want to perform.

 Set the value to **DescribeHealthStatus**. |
|LoadBalancerId|String|Yes|lb-bp1qjwo61pqz3ah\*\*\*\*\*\*|The ID of the Classic Load Balancer \(CLB\) instance. |
|ListenerPort|Integer|No|80|The frontend port that is used by the CLB instance.

 Valid values: **1 to 65535**.

 **Note:** If you do not specify this parameter, the health status of all ports is returned. |
|ListenerProtocol|String|No|https|The frontend protocol that is used by the CLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the CLB instance is deployed. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|BackendServers|Array of BackendServer| |The list of backend servers. |
|BackendServer| | | |
|ServerId|String|i-bp1h5u3fv54ytf\*\*\*\*\*|The ID of the Elastic Compute Service \(ECS\) instance or elastic network interface \(ENI\). |
|ServerHealthStatus|String|abnormal|The health status of the backend server:

 -   **normal**: The backend server is healthy.
-   **abnormal**: The backend server is unhealthy.
-   **unavailable**: The health check is not completed. |
|EniHost|String|192.168.\*\*. \*\*|The IP address of the ENI. |
|ListenerPort|Integer|80|The frontend port that is used by the CLB instance. |
|Port|Integer|70|The backend port that is used by the CLB instance. |
|Protocol|String|https|The frontend protocol that is used by the CLB instance. |
|ServerIp|String|192.168.\*\*. \*\*|The IP address of the ECS instance. |
|Type|String|ecs|The type of backend server. Valid values:

 -   **ecs** \(default\): an ECS instance.
-   **eni**: an ENI. |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=DescribeHealthStatus
&LoadBalancerId=lb-bp1qjwo61pqz3ah******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeHealthStatusResponse>
  <RequestId>E69BA4CE-2B55-45EC-94CA-E47B16759459</RequestId>
  <BackendServers>
        <BackendServer>
              <ListenerPort>80</ListenerPort>
              <ServerId>i-bp1h5u3fv54ytf0******</ServerId>
              <Port>80</Port>
              <ServerIp>192.168.0. **</ServerIp>
              <ServerHealthStatus>abnormal</ServerHealthStatus>
              <Protocol>http</Protocol>
        </BackendServer>
        <BackendServer>
              <ListenerPort>8080</ListenerPort>
              <ServerId>i-bp1h5u3fv54ytf0******</ServerId>
              <Port>80</Port>
              <ServerIp>192.168.0. **</ServerIp>
              <ServerHealthStatus>abnormal</ServerHealthStatus>
              <Protocol>tcp</Protocol>
        </BackendServer>
  </BackendServers>
</DescribeHealthStatusResponse>
```

`JSON` format

```
{
    "RequestId": "E69BA4CE-2B55-45EC-94CA-E47B16759459", 
    "BackendServers": {
        "BackendServer": [
            {
                "ListenerPort": 80, 
                "ServerId": "i-bp1h5u3fv54ytf*****", 
                "Port": 80, 
                "ServerIp": "192.168. **. **", 
                "ServerHealthStatus": "abnormal", 
                "Protocol": "http"
            }, 
            {
                "ListenerPort": 8080, 
                "ServerId": "i-bp1h5u3fv54ytf0******", 
                "Port": 80, 
                "ServerIp": "192.168. **. **", 
                "ServerHealthStatus": "abnormal", 
                "Protocol": "tcp"
            }
        ]
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

