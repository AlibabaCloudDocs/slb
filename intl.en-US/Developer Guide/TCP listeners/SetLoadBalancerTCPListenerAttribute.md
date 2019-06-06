# SetLoadBalancerTCPListenerAttribute {#doc_api_Slb_SetLoadBalancerTCPListenerAttribute .reference}

Modifies the configurations of a TCP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerTCPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerTCPListenerAttribute|The name of this action. Value:**SetLoadBalancerTCPListenerAttribute**

 |
|ListenerPort|Integer|Yes|80|The frontend port used by the SLB instance. Value range: **1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y7wezms|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call the [DescribeRegions](~~25609~~) API.

 |
|AclId|String|No|12333|Optional. The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off|Optional. Indicates whether to enable access control.

 Valid values: **on | off**

 |
|AclType|String|No|white|Optional. The access control method:

 -   **white**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the list, no requests are forwarded.

-   **black**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|Bandwidth|Integer|No|43|Optional. The peak bandwidth of the listener. Unit: Mbit/s Valid values:**-1 | 1 to 5120**

 -   **-1**: You can set the peak bandwidth of an Internet SLB instance that is billed by traffic to **-1**. Then, the peak bandwidth is not restricted.
-   **1 to 5120**: You can set one peak bandwidth for each listener of an Internet SLB instance that is billed by bandwidth. However, the sum of the peak bandwidth values of all listeners cannot exceed the peak bandwidth of the instance. For more information, see [Share bandwidth](~~57846~~).

 |
|Description|String|No|test|Optional. A description of the TCP listener.

 |
|EstablishedTimeout|Integer|No|500|Optional. The timeout value of the TCP connection.

 Value range:**10 to 900**. Unit: seconds

 |
|HealthCheckConnectPort|Integer|No|8080|Optional. The port used for health checks. Value range: 1 to 65535

 If you do not set this parameter, the backend server port \(**BackendServerPort**\) is used.

 |
|HealthCheckConnectTimeout|Integer|No|100|Optional. The length of time to wait for the response from the health check.

 If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckInterval** is greater than the value of **HealthCheckConnectTimeout**, the **HealthCheckConnectTimeout** parameter is invalid, and the timeout is set to the value of **HealthCheckInterval**.

 |
|HealthCheckDomain|String|No|$\_ip|Optional. The domain name used for health checks. You can set this parameter when the TCP listener requires HTTP health checks. If you do not set this parameter, TCP health checks are performed.

 -   **$\_ip**: the private IP address of the backend server.

When the IP address is specified or this parameter is not specified, SLB uses private IP addresses of backend servers as the domain names for health checks.

-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|Optional. The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by commas \(,\).

 Valid values: **http\_2xx | http\_3xx | http\_4xx | http\_5xx**

 |
|HealthCheckInterval|Integer|No|5|Optional. The time interval between two consecutive health checks. Value range:**1 to 50**. Unit: seconds

 |
|HealthCheckType|String|No|tcp|Optional. The health check type.

 Valid values: **tcp | http**

 |
|HealthCheckURI|String|No|/test/index.html|Optional. The URI used for health checks.

 You can set this parameter when the TCP listener requires HTTP health checks.

 If you do not set this parameter, TCP health checks are performed.

 |
|HealthyThreshold|Integer|No|4|Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to**success**\).

 Value range:**2 to 10**

 |
|MasterSlaveServerGroup|String|No|on|Optional. Indicates whether to use an active/standby server group. Valid values: **on | off**

 The value of **VServerGroup** and the value of **MasterSlaveServerGroup** cannot be **on** at the same time.

 |
|MasterSlaveServerGroupId|String|No|rsp-cige6j5e7p|Optional. The ID of the active/standby server group.

 **Note:** You can only choose either VServerGroupId or MasterSlaveServerGroupId.

 |
|PersistenceTimeout|Integer|No|0|Optional. The timeout value of the session persistence. Value range: **0 to 3600**. Unit: seconds

 Default value: **0**, which indicates that session persistence is disabled.

 |
|Scheduler|String|No|wrr|Optional. The algorithm used to distribute traffic. Valid values:

 -   **wrr**: A backend server with a higher weight is more likely to be polled.
-   **wlc**: A server with a higher weight receives more requests. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.
-   **sch**: A consistent hash based on source IP addresses. Requests with the same source IP addresses are scheduled to the same backend server.
-   **tch**: A consistent hash based on the following four variables: source IP + destination IP + source port + destination port. The same streams are scheduled to the same backend server.

 **Note:** Only guaranteed-performance instances support sch and tch.

 |
|SynProxy|String|No|enable|Optional. Indicates whether to enable SynProxy. SynProxy protects SLB from attacks.

 We recommend that you retain the value set by SLB in this parameter.

 Valid values:**enable | disable**

 |
|UnhealthyThreshold|Integer|No|4|Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success** to**failure**\).

 Value range:**2 to 10**

 |
|VServerGroup|String|No|on|Optional. Indicates whether to use a VServer group. Valid values: **on | off**

 The value of **VServerGroup** and the value of **MasterSlaveServerGroup** cannot be **on** at the same time.

 |
|VServerGroupId|String|No|rsp-cige6j5e7p|Optional. The ID of the VServer group.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerTCPListenerAttribute
&ListenerPort=80 
&LoadBalancerId=lb-bp1ygod3yctvg1y7wezms 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerTCPListenerAttributeResponse> 
  <RequestId>59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1</RequestId> 
</SetLoadBalancerTCPListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"59B41B53-BC4B-481A-9D8D-2A0D20B3FCD1"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

