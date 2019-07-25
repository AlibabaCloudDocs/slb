# DescribeLoadBalancerTCPListenerAttribute {#doc_api_Slb_DescribeLoadBalancerTCPListenerAttribute .reference}

Queries the configurations of a TCP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerTCPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerTCPListenerAttribute| The name of this action. Value: **DescribeLoadBalancerTCPListenerAttribute**

 |
|ListenerPort|Integer|Yes|80| The frontend port used by the SLB instance. Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1ygod3yctvg1y7wezms| The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou| The region to which the SLB instance belongs.

 To query the region ID, refer to the list of[regions and zones](~~40654~~)or call the[DescribeRegions](~~25609~~)API.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ListenerPort|Integer|443| The frontend port used by the SLB instance.

 |
|BackendServerPort|Integer|443| The backend port used by the SLB instance.

 **Note:** This parameter is not displayed when the backend server group is a virtual server group.

 |
|Bandwidth|Integer|-1| The peak bandwidth of the listener.

 |
|Status|String|stopped| The status of the listener.

 Valid values:**starting | running | configuring | stopping | stopped**

 |
|SynProxy|String|enable| Indicates whether to enable SynProxy. SynProxy protects SLB from attacks.

 We recommend that you retain the value set by SLB in this parameter.

 -   **enable**: Enable SynProxy.
-   **disable**: Disable SynProxy.

 |
|Scheduler|String|wrr| The algorithm used to distribute traffic.

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight receives more connections. When the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
-   **rr**: Requests are evenly and sequentially distributed to backend servers.

 |
|PersistenceTimeout|Integer|0| Indicates whether to enable session persistence.

 When the value is**0**, session persistence is disabled.

 |
|HealthCheckType|String|tcp| The health check type of the TCP listener.

 Valid values:**tcp | http**

 |
|HealthCheck|String|on| Indicates whether to enable the health check function.

 Valid values:**on | off**

 |
|HealthyThreshold|Integer|4| The number of consecutive successes of health checks before a backend server is declared as healthy \(from failure to success\).

 |
|UnhealthyThreshold|Integer|4| The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from success to failure\).

 |
|HealthCheckConnectPort|Integer|8080| The maximum amount of time to wait for the response from a health check. Unit: seconds

 |
|HealthCheckInterval|Integer|5| The time interval between two consecutive health checks. Unit: seconds.

 |
|HealthCheckDomain|String|$\_ip| The domain name used for health checks.

 |
|HealthCheckURI|String|/test/index.html| The URI used for health checks.

 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx| The HTTP status code indicating that the health check is normal.

 |
|VServerGroupId|String|rsp-cige6j5e7p| The ID of the VServer group.

 |
|AclId|String|12| The ID of the access control list associated with the listener.

 If the value of the**AclStatus** parameter is**on**, this parameter is required.

 |
|AclStatus|String|off| Indicates whether to enable access control.

 Valid values:**on | off**. Default value: off

 |
|AclType|String|white| The access control type:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the list, no requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). It applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is**on**, this parameter is required.

 |
|Description|String|Description| A description of the listener.

 |
|EstablishedTimeout|Integer|500| The timeout value of the TCP connection. Unit: seconds.

 |
|HealthCheckConnectTimeout|Integer|100| The timeout value.

 |
|MasterSlaveServerGroupId|String|rsp-0bfucwuotx| The ID of the active/standby server group.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeLoadBalancerTCPListenerAttribute
&ListenerPort=80 
&LoadBalancerId=lb-bp1ygod3yctvg1y7wezms 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
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
  <HealthCheckDomain/> 
  <HealthCheckInterval>2</HealthCheckInterval> 
  <RequestId>9A113A8C-BB8F-475E-9533-7819ECA2FFC1</RequestId> 
  <BackendServerPort>80</BackendServerPort> 
</DescribeLoadBalancerTCPListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"HealthCheckHttpCode":"http_2xx,http_3xx",
	"Description":"tcp_80",
	"AclStatus":"off",
	"HealthCheckURI":"/",
	"HealthCheck":"on",
	"HealthCheckConnectTimeout":5,
	"PersistenceTimeout":0,
	"ListenerPort":80,
	"Status":"running",
	"EstablishedTimeout":900,
	"HealthCheckType":"tcp",
	"HealthCheckInterval":2,
	"HealthCheckDomain":"",
	"HealthyThreshold":3,
	"Scheduler":"wrr",
	"RequestId":"9A113A8C-BB8F-475E-9533-7819ECA2FFC1",
	"UnhealthyThreshold":3,
	"BackendServerPort":80,
	"Bandwidth":-1
}
```

## Error codes {#section_mgr_ebl_xe5 .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb?spm=a2c69.11428812.home.38.5972hYtYhYtYON)

