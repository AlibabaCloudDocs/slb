# SetLoadBalancerUDPListenerAttribute

Modifies the configurations of a UDP listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerUDPListenerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetLoadBalancerUDPListenerAttribute|The operation that you want to perform.

 Set the value to **SetLoadBalancerUDPListenerAttribute**. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1rtfnodmywb43ecu4sf-c\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is created. |
|Bandwidth|Integer|No|-1|The maximum bandwidth of the listener. Unit: Mbit/s.

 Valid values: **1 to 5120 and -1**.

 -   **-1**: For a pay-by-data-transfer public-facing SLB instance, you can set the maximum bandwidth to **-1**. This indicates that the maximum bandwidth is not limited.
-   **1-5120**: For a pay-by-bandwidth public-facing SLB instance, you can specify the maximum bandwidth of each listener. The sum of maximum bandwidth values of all listeners cannot exceed the maximum bandwidth of the SLB instance. For more information, see [EIP bandwidth plan](~~85930~~). |
|Scheduler|String|No|wrr|The scheduling algorithm. Valid values:

 -   **wrr**: Backend servers that have higher weights receive more requests than those that have lower weights.
-   **wlc**: Requests are distributed based on the combination of weights and connections to backend servers.

If two backend servers have the same weight, the backend server that has fewer connections receives more requests.

-   **rr**: Requests are distributed to backend servers in sequence.
-   **sch**: specifies consistent hashing that is based on source IP addresses. Requests from the same source IP address are distributed to the same backend server.
-   **tch**: specifies consistent hashing that is based on four factors: source IP address, destination IP address, source port number, and destination port number. Requests that contain the same preceding information are distributed to the same backend server.
-   **qch**: specifies consistent hashing that is based on QUIC connection IDs. Requests that contain the same QUIC connection ID are distributed to the same backend server.

 **Note:** Only guaranteed-performance SLB instances support sch, tch, and qch. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before a backend server is declared healthy \(from **fail** to **success**\).

 Valid values: **2 to 10**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive failed health checks that must occur before a backend server is declared unhealthy. \(from **success** to **fail**\).

 Valid values: **2 to 10**. |
|HealthCheckConnectTimeout|Integer|No|100|The time period to wait for a health check response. If a backend server does not respond within the specified time period, the health check fails.

 Valid values: **1 to 300**. Unit: seconds.

 **Note:** If the value of the **HealthCheckConnectTimeout** parameter is smaller than that of the **HealthCheckInterval** parameter, the value of the **HealthCheckConnectTimeout** parameter is ignored and the value of the **HealthCheckInterval** parameter is regarded as the waiting period. |
|HealthCheckConnectPort|Integer|No|80|The port that is used for health checks.

 Valid values: **1 to 65535**. |
|HealthCheckInterval|Integer|No|5|The interval between two consecutive health checks.

 Valid values: **1 to 50**. Unit: seconds. |
|healthCheckReq|String|No|hello|The request string for UDP listener health checks. The string must be 1 to 500 characters in length and can contain only letters and digits. |
|healthCheckExp|String|No|ok|The response string for UDP listener health checks. The string must be 1 to 500 characters in length and can contain only letters and digits. |
|VServerGroup|String|No|on|Specifies whether to use a VServer group.

 Valid values: **on and off**.

 **Note:** The value of **VserverGroup** and the value of **MasterSlaveServerGroup** cannot be set to **on** at the same time. |
|VServerGroupId|String|No|rsp-cige6\*\*\*\*\*\*|The ID of the VServer group. |
|MasterSlaveServerGroupId|String|No|rsp-0bfuc\*\*\*\*\*|The ID of the primary/secondary server group.

 **Note:** You cannot specify the VServer group ID and primary/secondary server group ID at the same time. |
|MasterSlaveServerGroup|String|No|on|Specifies whether to use a primary/secondary server group.

 Valid values: **on and off**.

 The value of **VserverGroup** and the value of **MasterSlaveServerGroup** cannot be set to **on** at the same time. |
|AclId|String|No|off|The ID of the access control list \(ACL\) to which the listener is bound.

 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|white|The type of ACL. Valid values: white and black.

 -   **white**: specifies the ACL as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

Risks may arise if you specify the ACL as a whitelist.

The whitelist allows only network traffic from the IP addresses in the specified ACL to access the SLB listener.

If a whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

-   **black**: specifies the ACL as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If the blacklist is enabled but the corresponding ACL does not contain any IP addresses, the SLB listener forwards all requests.


 **Note:** This parameter takes effect when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable the access control feature.

 Valid values: **on and off**. |
|Description|String|No|test|The description of the listener. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=SetLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43ecu4sf-c****
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetLoadBalancerUDPListenerAttributeResponse>
     <RequestId>A0F0643E-D653-4F6F-A67F-205B2A92BE18</RequestId>
</SetLoadBalancerUDPListenerAttributeResponse>
```

`JSON` format

```
{
    "RequestId": "A0F0643E-D653-4F6F-A67F-205B2A92BE18"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

