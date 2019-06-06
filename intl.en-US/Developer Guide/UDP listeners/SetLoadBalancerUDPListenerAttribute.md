# SetLoadBalancerUDPListenerAttribute {#doc_api_Slb_SetLoadBalancerUDPListenerAttribute .reference}

Modifies the configurations of a UDP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerUDPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|SetLoadBalancerUDPListenerAttribute|The name of this action. Value:**SetLoadBalancerUDPListenerAttribute**

 |
|ListenerPort|Integer|Yes|80|The frontend port configured in the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 |
|AclId|String|No|off|Optional. The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off|Optional. Indicates whether to enable access control.

 Valid values:**on | off**

 |
|AclType|String|No|white|Optional. The access control method:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses to the list, no requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|Bandwidth|Integer|No|-1|Optional. The peak bandwidth of the listener. Valid values:**-1 | 1 to 5120**

 -   **-1**: The peak bandwidth is not limited.
-   **1 to 5120**: the peak bandwidth of the listener. Unit: Mbit/s. The sum of the peak bandwidth values of all listeners cannot surpass the peak bandwidth of the instance.

 |
|Description|String|No|test|Optional. A description of the listener.

 |
|HealthCheckConnectPort|Integer|No|80|Optional. The port used for health checks.

 Valid values:**1 to 65535**

 |
|HealthCheckConnectTimeout|Integer|No|100|Optional. The length of time to wait for the response from the health check. If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 **Note:** If the value of **HealthCheckInterval** is greater than the value of **HealthCheckConnectTimeout**, the **HealthCheckConnectTimeout** parameter is invalid, and the timeout is set to the value of **HealthCheckInterval**.

 |
|HealthCheckInterval|Integer|No|5|Optional. The time interval between two consecutive health checks.

 Value range:**1 to 50**. Unit: seconds

 |
|HealthyThreshold|Integer|No|4|The number of consecutive successes of health checks before the backend server is declared as healthy \(from**failure** to**success**\).

 Value range: **2 to 10**

 |
|MasterSlaveServerGroup|String|No|on|Optional. Indicates whether to use an active/standby server group. Valid values: **on | off**

 The value of **VServerGroup** and the value of **MasterSlaveServerGroup** cannot be **on** at the same time.

 |
|MasterSlaveServerGroupId|String|No|rsp-0bfucwuotx|Optional. The ID of the active/standby server group.

 **Note:** You can only choose either VServerGroupId or MasterSlaveServerGroupId.

 |
|Scheduler|String|No|wrr|Optional. The algorithm used to distribute traffic. Valid values:

 -   **wrr**: A backend server with a higher weight is more likely to be polled.
-   **wlc**: A server with a higher weight receives more requests.

When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.

-   **rr**: Requests are evenly and sequentially distributed to backend servers.
-   **sch**: A consistent hash based on the source IP address. Requests with the same source IP addresses are scheduled to the same backend server.
-   **tch**: A consistent hash based on the following four parameters: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.
-   **qch**: A consistent hash based on the QUIC Connection ID. The same QUIC Connection IDs are scheduled to the same backend servers.

 **Note:** Only guaranteed-performance instances support sch, tch, and qch.

 |
|UnhealthyThreshold|Integer|No|4|Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success** to**failure**\).

 Value range: **2 to 10**

 |
|VServerGroup|String|No|on|Optional. Indicates whether to use a VServer group.

 Valid values:**on | off**

 **Note:** The value of **VServerGroup** and the value of **MasterSlaveServerGroup** cannot be **on** at the same time.

 |
|VServerGroupId|String|No|rsp-cige6j5e7p|Optional. The ID of the VServer group.

 |
|healthCheckExp|String|No|ok|Optional. The response string for health checks of UDP listeners. It must be 1 to 500 characters in length and can only contain letters and numbers.

 |
|healthCheckReq|String|No|hello|Optional. The request string for health checks of UDP listeners. It must be 1 to 500 characters in length and can only contain letters and numbers.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=SetLoadBalancerUDPListenerAttribute
&ListenerPort=80 
&LoadBalancerId=lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<SetLoadBalancerUDPListenerAttributeResponse> 
  <RequestId>A0F0643E-D653-4F6F-A67F-205B2A92BE18</RequestId> 
</SetLoadBalancerUDPListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"A0F0643E-D653-4F6F-A67F-205B2A92BE18"
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

