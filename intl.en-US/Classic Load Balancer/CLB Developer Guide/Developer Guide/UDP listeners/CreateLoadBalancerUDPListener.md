# CreateLoadBalancerUDPListener

Creates a UDP listener.

You cannot query the source IP addresses of requests if you create UDP listeners for a Classic Load Balancer \(CLB\) instance that is deployed in a classic network.

**Note:** Newly created listeners are in the **stopped** state. After a listener is created, you must call the StartLoadBalancerListener operation to enable the listener. This way, the listener can forward network traffic.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerUDPListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoadBalancerUDPListener|The operation that you want to perform.

 Set the value to **CreateLoadBalancerUDPListener**. |
|Bandwidth|Integer|Yes|34|The maximum bandwidth of the listener.

 Valid values: **-1 and 1 to 5120**.

 -   **-1**: For a pay-by-data-transfer Internet-facing CLB instance, you can set the value to **-1**. This indicates that the maximum bandwidth is not limited. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the CLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y7\*\*\*\*\*\*|The ID of the CLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the CLB instance is deployed. |
|BackendServerPort|Integer|No|80|The backend port that is used by the CLB instance. Valid values: **1 to 65535**.

 If the VServerGroupId parameter is not set, this parameter is required. |
|Scheduler|String|No|wrr|The scheduling algorithm. Valid values:

 -   **wrr** \(default\): Backend servers that have higher weights receive more requests than those that have lower weights.
-   **wlc**: Requests are distributed based on the combination of the weights and number of connections to backend servers. If two backend servers have the same weight, the backend server that has fewer connections receives more requests.
-   **rr**: Requests are distributed to backend servers in sequence.
-   **sch**: specifies consistent hashing that is based on source IP addresses. Requests from the same source IP address are distributed to the same backend server.
-   **tch**: specifies consistent hashing that is based on four factors: source IP address, destination IP address, source port number, and destination port number. Requests that contain the same preceding information are distributed to the same backend server.
-   **qch**: specifies consistent hashing that is based on QUIC connection IDs. Requests that contain the same QUIC connection ID are distributed to the same backend server.

 Only high-performance CLB instances support the sch, tch, and qch consistent hashing algorithms. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before an unhealthy backend server is declared healthy. In this case, the health check state is changed from **fail** to **success**.

 Valid values: **2 to 10**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive failed health checks that must occur before a healthy backend server is declared unhealthy. In this case, the health check state is changed from **success** to **fail**.

 Valid values: **2 to 10**. |
|HealthCheckConnectTimeout|Integer|No|100|The timeout period of a health check response.

 If a backend server does not respond within the specified time period, the health check fails.

 Valid values: **1 to 300**. Unit: seconds. |
|HealthCheckConnectPort|Integer|No|80|The port that is used for health checks. Valid values: **1 to 65535**.

 If this parameter is not set, the port that is specified in **BackendServerPort** is used for health checks. |
|healthCheckInterval|Integer|No|3|The interval between two consecutive health checks.

 Valid values: **1 to 50**. Unit: seconds. |
|healthCheckReq|String|No|hello|The request string for UDP listener health checks. The string must be 1 to 500 characters in length and can contain only letters and digits. |
|healthCheckExp|String|No|ok|The response string for UDP listener health checks. The string must be 1 to 500 characters in length and can contain only letters and digits. |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*8|The ID of the server group. |
|MasterSlaveServerGroupId|String|No|rsp-0bfucwu\*\*\*\*|The ID of the primary/secondary server group.

 **Note:** You cannot specify both the vServer group ID and primary/secondary server group ID. |
|AclId|String|No|123|The ID of the access control list \(ACL\) to which the listener is bound.

 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|white|The type of ACL. Valid values:

 -   **white**: specifies the ACL as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

However, your business may be adversely affected if the whitelist is not set properly.

After you set a whitelist for a CLB listener, only requests from IP addresses that are added to the whitelist are distributed by the listener.

After a whitelist is enabled for a listener, if no IP address is added to the whitelist, the listener does not distribute requests.

-   **black**: specifies the ACL as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If a blacklist is enabled but the corresponding ACL does not contain an IP address, the CLB listener distributes all requests.


 This parameter takes effect when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable the access control feature.

 Valid values: **on and off**. Default value: off. |
|Description|String|No|test|The description of the listener.

 The description must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample requests

```
http(s)://[Endpoint]/? Action=CreateLoadBalancerUDPListener
&Bandwidth=34
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y7******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoadBalancerUDPListenerResponse>
	  <RequestId>06F00FBB-3D9E-4CCE-9D43-1A6946A75456</RequestId>
</CreateLoadBalancerUDPListenerResponse>
```

`JSON` format

```
{
    "RequestId": "06F00FBB-3D9E-4CCE-9D43-1A6946A75456"
}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|The error message returned because the VServerGroupId parameter or the MasterSlaveServerGroupId parameter does not match.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

