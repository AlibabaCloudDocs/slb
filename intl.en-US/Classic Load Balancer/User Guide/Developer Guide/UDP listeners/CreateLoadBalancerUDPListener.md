# CreateLoadBalancerUDPListener

Creates a UDP listener.

UDP listeners of a Server Load Balancer \(SLB\) instance of the classic network do not support viewing source IP addresses.

**Note:** A newly created listener is in the **stopped** state. After the listener is created, you must call StartLoadBalancerListener to enable the listener to forward traffic.

## Debug

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerUDPListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateLoadBalancerUDPListener|The name of this action.

 Value: **CreateLoadBalancerUDPListener** |
|Bandwidth|Integer|Yes|34|The peak bandwidth of the listener.

 Valid values: **-1 \| 1 to 5120**

 -   **-1**: Setting the peak bandwidth to **-1** for an Internet instance that is billed by traffic results in unlimited bandwidth. |
|ListenerPort|Integer|Yes|80|The frontend port used by the SLB instance.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y7\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs. |
|AclId|String|No|123|The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclStatus|String|No|off|Indicates whether to enable access control.

 Valid values: **on \| off**. Default value: off |
|AclType|String|No|white|The access control type. Valid values:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|BackendServerPort|Integer|No|80|The backend port used by the SLB instance. Value range: **1 to 65535**

 If the VServerGroupId parameter is not specified, this parameter is required. |
|Description|String|No|test|A description of the listener to be created.

 The description must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |
|HealthCheckConnectPort|Integer|No|80|The port used for health checks. Value range: **1 to 65535**

 If you do not set this parameter, the backend service port \(**BackendServerPort**\) is used.

 **Note:** This parameter is valid only when the value of the **HealthCheck** parameter is **on**. |
|HealthCheckConnectTimeout|Integer|No|100|The timeout value for each health check response.

 If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range: **1 to 300**. Unit: seconds |
|HealthyThreshold|Integer|No|4|The number of consecutive successes of health checks before a backend server is declared as healthy \(from **failure** to **success**\).

 Value range: **2 to 10** |
|MasterSlaveServerGroupId|String|No|rsp-0bfucwu\*\*\*\*|The ID of the active/standby server group.

 **Note:** You can only choose either VServerGroupId or MasterSlaveServerGroupId. |
|Scheduler|String|No|wrr|The algorithm used for distributing traffic. Valid values:

 -   **wrr** \(default\): A backend server with a higher weight receives more requests.
-   **wlc**: A backend server with a higher weight receives more requests. If the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.
-   **sch**: the consistent hash algorithm based on source IP addresses. Requests from the same source IP address are scheduled to the same backend server.
-   **tch**: the consistent hash algorithm based on four factors: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.
-   **qch**: the consistent hash algorithm based on QUIC Connection IDs. Requests with the same QUIC Connection ID are forwarded to the same backend server.

 **Note:** Only guaranteed-performance instances support sch, tch, and qch.

 Currently, the Consistent Hash \(CH\) algorithm is only supported in the following regions:

 -   Japan \(Tokyo\)
-   Australia \(Sydney\)
-   Malaysia \(Kuala Lumpur\)
-   Indonesia \(Jakarta\)
-   Germany \(Frankfurt\)
-   US \(Silicon Valley\)
-   US \(Virginia\)
-   UAE \(Dubai\)
-   China \(Hohhot\)
-   UK \(London\)
-   Zone B and Zone C of Singapore
-   China \(Hong Kong\)
-   China \(Qingdao\)
-   China \(Zhangjiakou\)
-   China \(Chengdu\)
-   Zone H and Zone I of China \(Hangzhou\)
-   Zone G and Zone H of China \(Beijing\)
-   Zone D and Zone E of China \(Shenzhen\)
-   Zone F and Zone G of China \(Shanghai\) |
|UnhealthyThreshold|Integer|No|4|The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from **success** to **failure**\).

 Value range: **2 to 10** |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*8|The ID of the VServer group. |
|healthCheckExp|String|No|ok|The response string for UDP listener health checks. The string must be 1 to 500 characters in length and can contain letters and numbers only. |
|healthCheckInterval|Integer|No|3|The interval between two consecutive health checks.

 Value range: **1 to 50**. Unit: seconds |
|healthCheckReq|String|No|hello|The request string for UDP listener health checks. It must be 1 to 500 characters in length and can only contain letters and numbers. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=CreateLoadBalancerUDPListener
&Bandwidth=34
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y7******
&<CommonParameters>

```

Response example

`XML` format

```
<CreateLoadBalancerUDPListenerResponse>
		  <RequestId>06F00FBB-3D9E-4CCE-9D43-1A6946A75456</RequestId>
	</CreateLoadBalancerUDPListenerResponse>
```

`JSON` format

```
{
	"RequestId":"06F00FBB-3D9E-4CCE-9D43-1A6946A75456"
}
```

## Errors

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|The specified VServerGroupId and MasterSlaveServerGroupId do not match.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

