# CreateLoadBalancerTCPListener

Creates a TCP listener.

**Note:** A newly created listener is in the stopped state. After the listener is created, you must call [StartLoadBalancerListener](~~27597~~) to enable the listener to forward traffic.

## Debug

[Use OpenAPI Explorer to perform debug operations and generate SDK code examples.](https://api.aliyun.com/#product=Slb&api=CreateLoadBalancerTCPListener&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|CreateLoadBalancerTCPListener|The name of this action.

 Value: **CreateLoadBalancerTCPListener** |
|Bandwidth|Integer|Yes|-1|The peak bandwidth of the listener. Valid values: **-1 \| 1 to 5120**

 -   **-1**: If you set the peak bandwidth of a pay-by-data-transfer Internet Server Load Balancer \(SLB\) instance to **-1**, the peak bandwidth is not limited.
-   **1-5120**: Unit: Mbps. You can set one peak bandwidth for each listener of a pay-by-bandwidth Internet SLB instance. However, the sum of the peak bandwidth values of all listeners cannot exceed the peak bandwidth of the SLB instance. For more information, see [Share instance bandwidth](~~57846~~). |
|ListenerPort|Integer|Yes|80|The frontend port used by the SLB instance.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp1b6c719dfa08ex\*\*\*\*\*\*|The ID of the SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |
|AclId|String|No|1323|The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclStatus|String|No|off|Indicates whether to enable access control.

 Valid values: **on \| off**. Default value: off |
|AclType|String|No|black|The access control type. Valid values:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. The use of a whitelist applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). The use of a blacklist applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|BackendServerPort|Integer|No|80|The backend port used by the SLB instance.

 Value range: **1 to 65535**

 If the VServerGroupId parameter is not specified, this parameter is required. |
|Description|String|No|Create a listener.|The description of the listener to be created.

 The description must be 1 to 80 characters in length and can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), and underscores \(\_\). Chinese characters are supported. |
|EstablishedTimeout|Integer|No|500|The timeout value of the TCP connection.

 Value range: **10 to 900**. Unit: seconds |
|HealthCheckConnectPort|Integer|No|80|The port used for health checks. Value range: **1 to 65535**

 If you do not set this parameter, the backend service port \(BackendServerPort\) is used.

 **Note:** This parameter is valid only when the value of the **HealthCheck** parameter is **on**. |
|HealthCheckConnectTimeout|Integer|No|100|The maximum timeout value for each health check response.

 Value range: **1 to 300**. Unit: seconds.

 Default value: 5 |
|HealthCheckDomain|String|No|$\_ip|The domain name used for health checks. Valid values:

 -   **$\_ip**: the private IP address of the backend server. If the IP address is specified or this parameter is not specified, SLB uses the private IP address of the backend server as the domain name for health checks.
-   **domain**: The domain name must be 1 to 80 characters in length, and can only contain letters, numbers, periods \(.\), and hyphens \(-\). |
|HealthCheckHttpCode|String|No|http\_2xx,http\_3xx|The HTTP status code indicating that the health check succeeds. Separate multiple HTTP status codes by commas \(,\).

 Valid values: **http\_2xx \| http\_3xx \| http\_4xx \| http\_5xx**. Default value: http\_2xx |
|HealthCheckType|String|No|tcp|The health check type.

 Valid values: **tcp \| http**. Default value: tcp |
|HealthCheckURI|String|No|/test/index.html|The URI used for health checks. The URI must be 1 to 80 characters in length and can only contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\). It must start with a forward slash \(/\), but cannot only contain a forward slash \(/\).

 You can set this parameter when the TCP listener requires HTTP health checks. If you do not set this parameter, TCP health checks are performed. |
|HealthyThreshold|Integer|No|4|The number of consecutive successful health checks that must occur before a backend server is declared as healthy \(from **failure** to **success**\).

 Value range: **2 to 10** |
|MasterSlaveServerGroupId|String|No|rsp-0bfucw\*\*\*\*\*|The ID of the active/standby server group.

 **Note:** You must specify either the VServerGroupId or MasterSlaveServerGroupId parameter. |
|PersistenceTimeout|Integer|No|0|The timeout value of the session persistence.

 Value range: **0 to 3600**. Unit: seconds

 Default value: **0**, which indicates that session persistence is disabled. |
|Scheduler|String|No|wrr|The algorithm used for distributing traffic. Valid values:

 -   **wrr** \(default\): A backend server with a higher weight receives more requests.
-   **wlc**: A server with a higher weight receives more requests. When the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.
-   **sch**: the consistent hash algorithm based on source IP addresses. Requests from the same source IP address are scheduled to the same backend server.
-   **tch**: the consistent hash algorithm based on four factors: source IP address + destination IP address + source port + destination port. The same streams are scheduled to the same backend server.

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
|UnhealthyThreshold|Integer|No|4|The number of consecutive failed health checks that must occur before a backend server is declared as unhealthy \(from **success** to **failure**\).

 Value range: **2 to 10** |
|VServerGroupId|String|No|rsp-cige6j\*\*\*\*\*|The ID of the VServer group. |
|healthCheckInterval|Integer|No|3|The interval between two consecutive health checks. Unit: seconds

 Value range: **1 to 50**. Unit: seconds. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|The ID of the request. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=CreateLoadBalancerTCPListener
&Bandwidth=-1
&ListenerPort=80
&LoadBalancerId=lb-bp1b6c719dfa08ex******
&<CommonParameters>

```

Response example

`XML` format

```
<CreateLoadBalancerTCPListenerResponse>
			  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
		</CreateLoadBalancerTCPListenerResponse>
```

`JSON` format

```
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Errors

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|Abs.VServerGroupIdAndMasterSlaveServerGroupId.MissMatch|The parameters VServerGroupId or MasterSlaveServerGroupId miss match.|VServerGroupId and MasterSlaveServerGroupId do not match.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

