# CreateLoadBalancerTCPListener

Creates a TCP listener.

**Note:** Newly created listeners are in the Stopped state. After a listener is created, you must call the [StartLoadBalancerListener](~~27597~~) operation to enable the listener to forward traffic.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerTCPListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|CreateLoadBalancerTCPListener|The operation that you want to perform.

 Set the value to **CreateLoadBalancerTCPListener**. |
|Bandwidth|Integer|Yes|-1|The maximum bandwidth of the listener. Valid values: **1 to 5120 and -1**. Unit: Mbit/s.

 -   **-1**: For a pay-by-data-transfer public-facing Server Load Balancer \(SLB\) instance, you can set the maximum bandwidth to **-1**. This indicates that the maximum bandwidth is not limited.
-   **1 to 5120**: For a pay-by-bandwidth public-facing SLB instance, you can specify the maximum bandwidth of each listener. The sum of maximum bandwidth values of all listeners cannot exceed the maximum bandwidth of the SLB instance. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08ex\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The region where the SLB instance is created.

 You can query the region ID from the [Regions and zones](~~40654~~) list or by calling the [DescribeRegions](~~25609~~) operation. |
|BackendServerPort|Integer|No|80|The backend port that is used by the SLB instance.

 Valid values: **1 to 65535**.

 If the VServerGroupId parameter is not set, this parameter is required. |
|Scheduler|String|No|wrr|The scheduling algorithm. Valid values:

 -   **wrr**: Backend servers that have higher weights receive more requests than those that have lower weights.
-   **wlc**: Requests are distributed based on the combination of the weights and connections to backend servers. If two backend servers have the same weight, the backend server that has fewer connections receives more requests.
-   **rr**: Requests are distributed to backend servers in sequence.
-   **sch**: specifies consistent hashing that is based on source IP addresses. Requests from the same source IP address are distributed to the same backend server.
-   **tch**: specifies consistent hashing that is based on four factors: source IP address, destination IP address, source port number, and destination port number. Requests that contain the same preceding information are distributed to the same backend server.

 **Note:** Only guaranteed-performance SLB instances support sch and tch.

 The CH algorithm is supported in the following regions:

 -   Japan \(Tokyo\)
-   India \(Mumbai\)
-   Singapore \(Singapore\): zones \(B + C\)
-   Australia \(Sydney\)
-   Malaysia \(Kuala Lumpur\)
-   Indonesia \(Jakarta\)
-   Germany \(Frankfurt\)
-   UK \(London\)
-   UAE \(Dubai\)
-   US \(Silicon Valley\)
-   US \(Virginia\)
-   China \(Hong Kong\): zones \(B + C\)
-   China \(Beijing\): zones \(C + D + E + F + G + H\)
-   China \(Chengdu\): zone A
-   China \(Hangzhou\): zones \(B + C + E + F + I + H\)
-   China \(Hohhot\)
-   China \(Qingdao\): zones \(B + C\)
-   China \(Shanghai\): zones \(B + D + E + F + G + H + J\)
-   China \(Shenzhen\): zones \(B + C + D\)
-   China \(Zhangjiakou\): zones \(A + B\) |
|PersistenceTimeout|Integer|No|0|The timeout period of session persistence.

 Valid values: **0 to 3600**. Unit: seconds.

 Default value: **0**. By default, session persistence is disabled. |
|EstablishedTimeout|Integer|No|500|The timeout period of connections. Unit: seconds.

 Valid values: **10 to 900**. Unit: seconds. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before an unhealthy backend server is declared healthy. In this case, the health check state is changed from **fail** to **success**.

 Valid values: **2 to 10**. |
|UnhealthyThreshold|Integer|No|4|The number of consecutive failed health checks that must occur before a healthy backend server is declared unhealthy. In this case, the health check state is changed from **success** to **fail**.

 Valid values: **2 to 10**. |
|HealthCheckConnectTimeout|Integer|No|100|The maximum amount of time to wait for a health check response.

 Valid values: **1 to 300**. Unit: seconds.

 Default value: **5**. |
|HealthCheckConnectPort|Integer|No|80|The port that is used for health checks.

 Valid values: **1 to 65535**.

 If this parameter is not set, the port specified by BackendServerPort is used for health checks. |
|healthCheckInterval|Integer|No|3|The interval between two consecutive health checks. Unit: seconds.

 Valid values: **1 to 50**. |
|HealthCheckDomain|String|No|172.10.\*\*. \*\*|The domain name that is used for health checks. Valid values:

 -   **$\_ip**: The private IP address of the backend server. If the $\_ip parameter is set or the HealthCheckDomain parameter is not set, SLB uses the private IP addresses of backend servers as the domain names for health check.
-   **domain**: The domain name must be 1 to 80 characters in length. It can contain only letters, digits, periods \(.\), and hyphens \(-\). |
|HealthCheckURI|String|No|/test/index.html|The URI that are used for health checks. The value must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), number signs \(\#\), and ampersands \(&\). The URL must start with a forward slash \(/\) and cannot contain only a forward slash \(/\).

 You can set this parameter when the TCP listener requires HTTP health checks. If you do not set this parameter, TCP health checks are performed. |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|The HTTP status code that specifies a successful health check. Separate multiple HTTP status codes with commas \(,\).

 Valid values: **http\_2xx, http\_3xx, http\_4xx, and http\_5xx**. Default value: http\_2xx. |
|HealthCheckType|String|No|tcp|The type of health check

 Valid values: **tcp and http**. Default value: tcp. |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*\*|The ID of the VServer group. |
|MasterSlaveServerGroupId|String|No|rsp-0bfucw\*\*\*\*\*|The ID of the primary/secondary server group.

 **Note:** You cannot specify the VServer group ID and primary/secondary server group ID at the same time. |
|AclId|String|No|1323|The ID of the Access Control List \(ACL\) to which the listener is bound.

 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclType|String|No|black|The type of ACL. Valid values: white and black.

 -   **white**: specifies the ACL as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

Risks may arise if you specify an ACL as a whitelist.

The whitelist allows only network traffic from the IP addresses in the specified ACL to access the SLB listener.

If a whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

-   **black**: specifies the ACL as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If the blacklist is enabled but the corresponding ACL does not contain any IP addresses, the SLB listener forwards all requests.


 This parameter is required when the **AclStatus** parameter is set to **on**. |
|AclStatus|String|No|off|Specifies whether to enable the access control feature.

 Valid values: **on and off**. |
|Description|String|No|Creates a listener.|The description of the listener.

 It must be 1 to 80 characters in length and can contain letters, digits, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=CreateLoadBalancerTCPListener
&Bandwidth=-1
&ListenerPort=80
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<Common request parameters>
```

Sample success responses

`XML` format

```
<CreateLoadBalancerTCPListenerResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</CreateLoadBalancerTCPListenerResponse>
```

`JSON` format

```
{"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"}
```

## Error codes

|HttpCode|Error code|Error message|Description|
|--------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|The error message returned because the VServerGroupId parameter or the MasterSlaveServerGroupId parameter do not match.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

