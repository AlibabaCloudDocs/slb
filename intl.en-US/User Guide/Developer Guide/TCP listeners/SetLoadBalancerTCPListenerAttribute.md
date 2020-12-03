# SetLoadBalancerTCPListenerAttribute

Modifies the configurations of a TCP listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerTCPListenerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|SetLoadBalancerTCPListenerAttribute|The operation that you want to perform.

 Set the value to **SetLoadBalancerTCPListenerAttribute**. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the SLB instance.

 Valid values:**1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is deployed.

 You can query the region ID from the [Regions and zones](~~40654~~) list or by calling the [DescribeRegions](~~25609~~) operation. |
|Bandwidth|Integer|No|43|The maximum bandwidth of the listener. Valid values: **1 to 5120 and -1**. Unit: Mbit/s.

 -   **-1**: For a pay-by-data-transfer public-facing SLB instance, you can set the maximum bandwidth to **-1**. This indicates that the maximum bandwidth is not limited.
-   **1 to 5120**: For a pay-by-bandwidth public-facing SLB instance, you can specify the maximum bandwidth of each listener. The sum of maximum bandwidth values of all listeners cannot exceed the maximum bandwidth of the SLB instance. |
|Scheduler|String|No|wrr|The scheduling algorithm. Valid values:

 -   **wrr**: Backend servers that have higher weights receive more requests than those that have lower weights.
-   **wlc**: Requests are distributed based on the combination of weights and connections to backend servers. If two backend servers have the same weight, the backend server that has fewer connections receives more requests.
-   **rr**: Requests are distributed to backend servers in sequence.
-   **sch**: specifies consistent hashing that is based on source IP addresses. Requests from the same source IP address are distributed to the same backend server.
-   **tch**: specifies consistent hashing that is based on four factors: source IP address, destination IP address, source port number, and destination port number. Requests that contain the same preceding information are distributed to the same backend server.

 **Note:** Only guaranteed-performance instances support sch and tch. |
|PersistenceTimeout|Integer|No|0|The timeout period of session persistence. Valid values: **0 to 3600**. Unit: seconds.

 Default value: **0**. By default, session persistence is disabled. |
|EstablishedTimeout|Integer|No|500|The connection timeout period.

 Valid values: **10 to 900**. Unit: seconds. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before a backend server is declared healthy \(from **fail** to **success**\).

 Valid values: **2 to 10**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive failed health checks that must occur before a backend server is declared unhealthy. \(from **success** to **fail**\).

 Valid values: **2 to 10**. |
|HealthCheckConnectTimeout|Integer|No|100|The time period to wait for a health check response.

 If a backend server does not respond within the specified time period, the health check fails.

 Valid values: **1 to 300**.

 **Note:** If the value of the **HealthCheckConnectTimeout** parameter is smaller than that of the **HealthCheckInterval** parameter, the value of the **HCTimeout** parameter is ignored and the value of the **HealthCheckInterval** parameter is regarded the waiting period. |
|HealthCheckConnectPort|Integer|No|8080|The port that is used for health checks.

 Valid values: **1 to 65535**.

 If this parameter is not set, the port specified by **BackendServerPort** is used for health checks. |
|HealthCheckInterval|Integer|No|5|The interval between two consecutive health checks. Valid values: **1 to 50**. Unit: seconds. |
|HealthCheckDomain|String|No|172.16.\*\*. \*\*|The domain name that is used for health checks. You can set this parameter when the TCP listener requires HTTP health checks. If you do not set this parameter, TCP health checks are performed.

 -   **$\_ip**: the private IP address of the backend server.

If you do not set this parameter or set the parameter to $\_ip, the SLB instance uses the private IP address of each backend server as the domain name for health checks.

-   **domain**: The domain name must be 1 to 80 characters in length. It can contain only letters, digits, periods \(.\), and hyphens \(-\). |
|HealthCheckURI|String|No|/test/index.html|The URI that is used for health checks. The URI must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), %? number signs \(\#\), and ampersands \(&\). The URL must start with a forward slash \(/\) and must not contain only a forward slash.

 You can set this parameter when the TCP listener requires HTTP health checks.

 If you do not set this parameter, TCP health checks are performed. |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|The HTTP status code that specifies a successful health check. Separate multiple HTTP status codes with commas \(,\).

 Valid values: **http\_2xx, http\_3xx, http\_4xx, and http\_5xx**. |
|HealthCheckType|String|No|tcp|The type of health check.

 Valid values: **tcp and http**. |
|SynProxy|String|No|enable|Specifies whether to enable SYNPROXY, which protects SLB instances from attacks.

 We recommend that you use the default value for this parameter.

 Valid values:**enable and disable**. |
|VServerGroup|String|No|on|Specifies whether to use a VServer group.

 Valid values: **on and off**.

 The value of **VserverGroup** and the value of **MasterSlaveServerGroup** cannot be **on** at the same time. |
|VServerGroupId|String|No|rsp-cige6j5\*\*\*\*\*|The ID of the VServer group. |
|MasterSlaveServerGroupId|String|No|rsp-cige\*\*\*\*\*\*|The ID of the primary/secondary server group.

 **Note:** You cannot specify the VServer group ID or primary/secondary server group ID at the same time. |
|MasterSlaveServerGroup|String|No|on|Specifies whether to use a primary/secondary server group.

 Valid values: **on and off**.

 The value of **VserverGroup** and the value of **MasterSlaveServerGroup** cannot be set to **on** at the same time. |
|AclId|String|No|12333|The ID of the Access Control List \(ACL\) to which the listener is bound.

 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|white|The type of ACL. Valid values: white and black.

 -   **white**: specifies the ACL as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

Risks may arise if you specify the ACL as a whitelist.

The whitelist allows only network traffic from the IP addresses in the specified ACL to access the SLB listener.

If a whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

-   **black**: specifies the ACL as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If the blacklist is enabled but the corresponding ACL does not contain any IP addresses, the SLB listener forwards all requests.


 This parameter takes effect when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable the access control feature.

 Valid values: **on and off**. |
|Description|String|No|test|The description of the TCP listener. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=SetLoadBalancerTCPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<SetLoadBalancerTCPListenerAttributeResponse>
     <RequestId>59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1</RequestId>
</SetLoadBalancerTCPListenerAttributeResponse>
```

`JSON` format

```
{
    "RequestId": "59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1"
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

