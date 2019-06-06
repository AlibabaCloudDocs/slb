# CreateLoadBalancerUDPListener {#doc_api_Slb_CreateLoadBalancerUDPListener .reference}

Creates a UDP listener.

Obtaining real IP addresses is not supported by classic network SLB instances when you use the UDP protocol.

**Note:** A newly created listener is in the**Stopped** state. After a listener is created, you need to call StartLoadBalancerListener to start the listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerUDPListener) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateLoadBalancerUDPListener|The name of this action. Value:**CreateLoadBalancerUDPListener**

 |
|Bandwidth|Integer|Yes|34|The peak bandwidth of the listener to be created. Valid values:**-1 | 1 to 5120**.

 -   **-1**: Setting the peak bandwidth to **-1** for an Internet instance that is billed by traffic results in unlimited bandwidth.

 |
|ListenerPort|Integer|Yes|80|The frontend port configured in the SLB instance. Value range: **1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y7wezms|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The region ID of the SLB instance.

 |
|AclId|String|No|123|Optional. The ID of the access control list associated with the listener to be created.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off|Optional. Indicates whether to enable access control.

 Valid values: **on | off**. Default value: off

 |
|AclType|String|No|white|Optional. The access control type:

 -   **white**: Indicates a whitelist. Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. This applies to scenarios in which an application only allows access from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is enabled, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the list, no requests are forwarded.

-   **black**: Indicates a blacklist. Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). This applies to scenarios in which an application only denies access from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|BackendServerPort|Integer|No|80|Optional. The backend port used by the SLB instance. Value range:**1 to 65535**. If the VServerGroupId parameter is not specified, this parameter is required.

 |
|Description|String|No|test|Optional. The description of the listener to be created.

 The description must be 1 to 80 characters in length. It can contain letters, numbers, hyphens \(-\), slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported.

 |
|HealthCheckConnectPort|Integer|No|80|Optional. The port used for health checks. Value range: **1 to 65535**

 If you do not set this parameter, the backend service port \(**BackendServerPort**\) is used.

 |
|HealthCheckConnectTimeout|Integer|No|100|Optional. The length of time to wait for the response from the health check.

 If the backend ECS instance does not send a correct response within the specified time, the health check fails.

 Value range:**1 to 300**. Unit: seconds

 |
|HealthyThreshold|Integer|No|4|Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(that is, changes from**failure** to **success** state\).

 Value range:**2 to 10**

 |
|MasterSlaveServerGroupId|String|No|rsp-0bfucwuotx|The ID of the active/standby server group.

 **Note:** You cannot set both the VServerGroupId parameter and the MasterSlaveServerGroupId parameter at the same time.

 |
|Scheduler|String|No|wrr|Optional. The algorithm used to distribute traffic. Valid values:

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight will receive more requests. When the weight value is the same, the backend server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.
-   **sch**: A consistent hash based on the source IP address. Requests with the same source IP addresses are scheduled to the same backend server.
-   **tch**: A consistent hash based on the following four factors: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.
-   **qch**: A consistent hash based on the QUIC Connection ID. The same QUIC Connection IDs are scheduled to the same backend servers.

 **Note:** Only guaranteed-performance instances support sch, tch, and qch.

 Currently, the consistent hash algorithm is supported in the following regions:

 -   Japan \(Tokyo\)
-   Australia \(Sydney\)
-   Malaysia \(Kuala Lumpur\)
-   Indonesia \(Jakarta\)
-   Germany \(Frankfurt\)
-   US \(Silicon Valley\)
-   US \(Virginia\)
-   UAE \(Dubai\)
-   China \(Hohhot\)

 |
|UnhealthyThreshold|Integer|No|4|Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(that is, changes from**success** to **failure** state\).

 Value range: **2 to 10**

 |
|VServerGroupId|String|No|rsp-cige6j5e7p|Optional. The ID of the VServer group.

 |
|healthCheckExp|String|No|ok|Optional. The health check response string of the UDP listener. The string must be 1 to 500 characters in length and can contain letters and numbers only.

 |
|healthCheckInterval|Integer|No|3|Optional. The time interval between two consecutive health checks.

 Value range: **1 to 50**. Unit: seconds.

 |
|healthCheckReq|String|No|hello|Optional. The request string for UDP listener health checks. It must be 1 to 500 characters in length and can only contain letters and numbers.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateLoadBalancerUDPListener
&Bandwidth=34
&ListenerPort=80 
&LoadBalancerId=lb-bp1ygod3yctvg1y7wezms
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateLoadBalancerUDPListenerResponse> 
  <RequestId>06F00FBB-3D9E-4CCE-9D43-1A6946A75456</RequestId> 
</CreateLoadBalancerUDPListenerResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"06F00FBB-3D9E-4CCE-9D43-1A6946A75456"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|VServerGroupId and MasterSlaveServerGroupId do not match.|

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

