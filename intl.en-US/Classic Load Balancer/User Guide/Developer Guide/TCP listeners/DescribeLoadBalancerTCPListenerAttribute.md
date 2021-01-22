# DescribeLoadBalancerTCPListenerAttribute

Queries the configurations of a TCP listener.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerTCPListenerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerTCPListenerAttribute|The name of this action.

 Value: **DescribeLoadBalancerTCPListenerAttribute** |
|ListenerPort|Integer|Yes|80|The frontend port used by the TCP listener.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y\*\*\*\*\*\*|The ID of the Server Load Balancer \(SLB\) instance to which the TCP listener belongs. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 To query the region ID, refer to the list of [regions and zones](~~40654~~) or call [DescribeRegions](~~25609~~). |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ListenerPort|Integer|443|The frontend port used by the TCP listener. |
|BackendServerPort|Integer|443|The backend port used by the TCP listener.

 **Note:** This parameter is not displayed when the backend server group is a VServer group. |
|Status|String|stopped|The status of the TCP listener.

 Valid values: **running \| stopped**

 -   **running**: The listener is running.
-   **stopped**: The listener is stopped. |
|Bandwidth|Integer|-1|The peak bandwidth of the listener. |
|Scheduler|String|wrr|The algorithm used for distributing traffic.

 -   **wrr** \(default\): A backend server with a higher weight receives more requests.
-   **wlc**: A backend server with a higher weight receives more requests. If the weight values of two backend servers are the same, the server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers. |
|SynProxy|String|enable|Indicates whether SynProxy is enabled. SynProxy protects SLB from attacks.

 We recommend that you retain the value set by SLB for this parameter.

 -   **enable**: SynProxy is enabled.
-   **disable**: SynProxy is disabled. |
|PersistenceTimeout|Integer|0|Indicates whether session persistence is enabled.

 The value **0** indicates that session persistence is disabled. |
|EstablishedTimeout|Integer|500|The timeout value of the TCP connection. |
|HealthCheck|String|on|Indicates whether the health check function is enabled.

 Valid values: **on \| off** |
|HealthyThreshold|Integer|4|The number of consecutive successful health checks that must occur before a backend server is declared as healthy \(from failure to success\). |
|UnhealthyThreshold|Integer|4|The number of consecutive failed health checks that must occur before a backend server is declared as unhealthy \(from success to failure\). |
|HealthCheckConnectTimeout|Integer|100|The timeout value of a health check. |
|HealthCheckConnectPort|Integer|8080|The port used for health checks. |
|HealthCheckInterval|Integer|5|The interval between two consecutive health checks. |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|The HTTP status code indicating that a health check is successful. |
|HealthCheckDomain|String|www.domain.com|The domain name used for health checks. |
|HealthCheckURI|String|/test/index.html|The URI used for health checks.

 The URI must be 1 to 80 characters in length. It can only contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\). The URL cannot only contain a forward slash \(/\), but must start with a forward slash \(/\). |
|HealthCheckType|String|tcp|The health check type of the TCP listener.

 Valid values: **tcp \| http** |
|HealthCheckMethod|String|tcp|The health check method. |
|VServerGroupId|String|rsp-cige6\*\*\*\*\*\*8|The ID of the VServer group associated with the TCP listener. |
|MasterSlaveServerGroupId|String|rsp-0bfucw\*\*\*\*\*|The ID of the active/standby server group associated with the TCP listener. |
|AclId|String|12|The ID of the access control list associated with the TCP listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclType|String|white|The access control method. Valid values:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. This method applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). This method applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclStatus|String|off|Indicates whether to enable access control.

 Valid values: **on \| off**. Default value: off |
|Description|String|The description of the TCP listener.|The description of the TCP listener. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancerTCPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1ygod3yctvg1y******
&<CommonParameters>
```

Response example

`XML` format

```
<DescribeLoadBalancerTCPListenerAttributeResponse>
			  <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode>
	  <PersistenceTimeout>0</PersistenceTimeout>
	  <HealthCheckType>tcp</HealthCheckType>
	  <HealthyThreshold>3</HealthyThreshold>
	  <Scheduler>wrr</Scheduler>
	  <UnhealthyThreshold>3</UnhealthyThreshold>
	  <Bandwidth>-1</Bandwidth>
	  <Description>tcp_80</Description>
	  <AclStatus>off</AclStatus>
	  <HealthCheckURI>/</HealthCheckURI>
	  <HealthCheck>on</HealthCheck>
	  <HealthCheckConnectTimeout>5</HealthCheckConnectTimeout>
	  <ListenerPort>80</ListenerPort>
	  <Status>running</Status>
	  <EstablishedTimeout>900</EstablishedTimeout>
	  <HealthCheckDomain></HealthCheckDomain>
	  <HealthCheckInterval>2</HealthCheckInterval>
	  <RequestId>9A113A8C-BB8F-475E-9533-7819ECA2FFC1</RequestId>
	  <BackendServerPort>80</BackendServerPort>
    </DescribeLoadBalancerTCPListenerAttributeResponse>
```

`JSON` format

```
{
    "HealthCheckHttpCode": "http_2xx,http_3xx", 
    "PersistenceTimeout": 0, 
    "HealthCheckType": "tcp", 
    "HealthyThreshold": 3, 
    "Scheduler": "wrr", 
    "UnhealthyThreshold": 3, 
    "Bandwidth": -1, 
    "Description": "tcp_80", 
    "AclStatus": "off", 
    "HealthCheckURI": "/", 
    "HealthCheck": "on", 
    "HealthCheckConnectTimeout": 5, 
    "ListenerPort": 80, 
    "Status": "running", 
    "EstablishedTimeout": 900, 
    "HealthCheckDomain": "", 
    "HealthCheckInterval": 2, 
    "RequestId": "9A113A8C-BB8F-475E-9533-7819ECA2FFC1", 
    "BackendServerPort": 80
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

