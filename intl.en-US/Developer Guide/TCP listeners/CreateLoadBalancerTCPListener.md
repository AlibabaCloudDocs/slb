# CreateLoadBalancerTCPListener {#doc_api_Slb_CreateLoadBalancerTCPListener .reference}

Creates a TCP listener.

**Note:** The status of a newly created listener is stopped. To start a listener to forward traffic, call[StartLoadBalancerListener](~~27597~~) after the listener is created.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerTCPListener) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateLoadBalancerTCPListener| The name of this action.

 Value: **CreateLoadBalancerTCPListener**

 |
|Bandwidth|Integer|Yes|-1| The peak bandwidth of the listener. Valid values:**-1 | 1 to 5120**

 -   **-1**: You can set the peak bandwidth of an Internet SLB instance that is billed by traffic to **-1**. Then, the peak bandwidth is not restricted.
-   **1 to 5120**: You can set one peak bandwidth for each listener of an Internet SLB instance that is billed by bandwidth. However, the sum of the peak bandwidth values of all listeners cannot exceed the peak bandwidth of the SLB instance.

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance.

 Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08ex\*\*\*\*\*\*| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou-d| The region to which the SLB instance belongs.

 To query the region ID, refer to the list of[regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~).

 |
|AclId|String|No|1323| Optional. The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|No|off| Optional. Indicates whether to enable access control.

 Valid values:**on | off**. Default value: off

 |
|AclType|String|No|black| Optional. The access control type:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a white access control list poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses to the list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is**on**, this parameter is required.

 |
|BackendServerPort|Integer|No|80| Optional. The backend port used by the SLB instance.

 Value range:**1 to 65535**

 If the VServerGroupId parameter is not specified, this parameter is required.

 |
|Description|String|No|Create a listener.| Optional. A description of the listener to be created.

 The description must be 1 to 80 characters in length and can contain letters, numbers, Chinese characters, hyphens \(-\), slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported.

 |
|EstablishedTimeout|Integer|No|500| Optional. The timeout value of the TCP connection.

 Value range:**10 to 900**. Unit: seconds

 |
|HealthCheckConnectPort|Integer|No|80| Optional. The port used for health checks. Value range:**1 to 65535**

 If you do not set this parameter, the backend service port \(BackendServerPort\) is used.

 |
|HealthCheckConnectTimeout|Integer|No|100| Optional. The maximum timeout value for each health check response.

 Value range:**1 to 300**. Unit: seconds

 Default: 5

 |
|HealthCheckDomain|String|No|$\_ip| Optional. The domain name used for health checks. Valid values:

 -   **$\_ip**: the private IP address of the backend server. If the IP address is specified or this parameter is not specified, SLB uses private IP addresses of backend servers as the domain names for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\).

 |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx| Optional. The HTTP status code indicating that the health check is normal. Separate multiple HTTP status codes by commas \(,\).

 Valid values:**http\_2xx | http\_3xx | http\_4xx | http\_5xx**. Default value: http\_2xx

 |
|HealthCheckType|String|No|tcp| Optional. The health check type.

 Valid values:**tcp | http**. Default value: tcp

 |
|HealthCheckURI|String|No|/test/index.html| Optional. The URI used for health checks.

 You can set this parameter when the TCP listener requires HTTP health checks. If you do not set this parameter, TCP health checks are performed.

 |
|HealthyThreshold|Integer|No|4| Optional. The number of consecutive successes of health checks before a backend server is declared as healthy \(from**failure** to**success**\).

 Value range:**2 to 10**

 |
|MasterSlaveServerGroupId|String|No|rsp-0bfucw\*\*\*\*\*| Optional. The ID of the active/standby server group.

 **Note:** You can only choose either VServerGroupId or MasterSlaveServerGroupId.

 |
|PersistenceTimeout|Integer|No|0| Optional. The timeout value of the session persistence.

 Value range:**0 to 3600**. Unit: seconds

 Default value:**0**, which indicates that session persistence is disabled.

 |
|Scheduler|String|No|wrr| Optional. The algorithm used to distribute traffic. Valid values:**wrr | wlc | rr**

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight receives more requests.

When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.

-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 |
|UnhealthyThreshold|Integer|No|4| Optional. The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from**success** to**failure**\).

 Value range:**2 to 10**

 |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*\*| Optional. The ID of the VServer group.

 |
|HealthCheckInterval|Integer|No|3| Optional. The time interval between two consecutive health checks.

 Value range:**1 to 50**. Unit: seconds

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=CreateLoadBalancerTCPListener
&Bandwidth=-1
&ListenerPort=80
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<CreateLoadBalancerTCPListenerResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</CreateLoadBalancerTCPListenerResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#section_8tt_f8k_k28 .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|VServerGroupId and MasterSlaveServerGroupId do not match.|

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

