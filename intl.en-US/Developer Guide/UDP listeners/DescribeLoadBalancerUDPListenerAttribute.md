# DescribeLoadBalancerUDPListenerAttribute {#doc_api_Slb_DescribeLoadBalancerUDPListenerAttribute .reference}

Queries the configurations of a UDP listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerUDPListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerUDPListenerAttribute|The name of this action. Value:`DescribeLoadBalancerUDPListenerAttribute`

 |
|ListenerPort|Integer|Yes|80|The frontend port configured in the SLB instance. Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ListenerPort|Integer|53|The frontend port used by the SLB instance.

 |
|BackendServerPort|Integer|53|The backend port used by the SLB instance.

 **Note:** This parameter is not returned when a virtual backend server group is used.

 |
|Bandwidth|Integer|-1|The peak bandwidth of the listener.

 |
|Status|String|stopped|The status of the listener.

 Valid values:**starting | running | configuring | stopping | stopped**

 |
|Scheduler|String|wrr|The algorithm used to distribute traffic.

 -   **wrr** \(default\): Backend servers with higher weights receive more requests than those with smaller weights.
-   **wlc**: A server with a higher weight will receive more requests.

When the weight is the same, the server with a smaller number of connections is more likely to be polled.

-   **rr**: Requests are evenly and sequentially distributed to the backend servers.

 |
|HealthCheck|String|on|Indicates whether to enable health checks.

 Valid values:**on | off**.

 |
|HealthyThreshold|Integer|4|The number of consecutive successes of health checks before a backend server is declared as healthy \(from failure to success\).

 |
|UnhealthyThreshold|Integer|4|The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from success to failure\).

 |
|HealthCheckConnectTimeout|Integer|100|The length of time to wait for the response from a health check.

 |
|HealthCheckConnectPort|Integer|8080|The port used for health checks.

 |
|HealthCheckInterval|Integer|5|The time interval between two consecutive health checks. Unit: seconds.

 |
|VServerGroupId|String|rsp-cige6j5e7p|The ID of the VServer group.

 |
|AclId|String|12394388|The ID of the access control list.

 |
|AclStatus|String|off|Indicates whether to enable access control.

 Valid value: **on | off**. Default value: off.

 |
|AclType|String|white|The access control method:

 -   white:

Indicates a whitelist. Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where an application only allows access from specific IP addresses.

Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable a whitelist without adding any IP addresses in the corresponding access control list, no requests are forwarded.

-   black:

Indicates a blacklist. Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). It applies to scenarios where an application only denies access from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|Description|String|A description of the access control|A description of the access control.

 |
|HealthCheckExp|String|ok|The response string for the health check of the UDP listener.

 |
|HealthCheckReq|String|hello|The request string for the health check of the UDP listener.

 |
|MasterSlaveServerGroupId|String|rsp-0bfucwuotx|The ID of the active/standby server group.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43ecu4sf-cn-east-hangzhou-01 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeLoadBalancerUDPListenerAttributeResponse> 
  <AclStatus>off</AclStatus> 
  <HealthCheck>on</HealthCheck> 
  <HealthCheckConnectTimeout>5</HealthCheckConnectTimeout> 
  <PersistenceTimeout>0</PersistenceTimeout> 
  <ListenerPort>80</ListenerPort> 
  <Status>stopped</Status> 
  <Scheduler>wrr</Scheduler> 
  <HealthyThreshold>3</HealthyThreshold> 
  <HealthCheckInterval>2</HealthCheckInterval> 
  <RequestId>9C103591-2533-432B-9E6B-6DB098C0E65C</RequestId>
  <UnhealthyThreshold>3</UnhealthyThreshold> 
  <BackendServerPort>34</BackendServerPort> 
  <Bandwidth>67</Bandwidth> 
</DescribeLoadBalancerUDPListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"AclStatus":"off",
	"HealthCheck":"on",
	"HealthCheckConnectTimeout":5,
	"PersistenceTimeout":0,
	"ListenerPort":80,
	"Status":"stopped",
	"Scheduler":"wrr",
	"HealthyThreshold":3,
	"HealthCheckInterval":2,
	"RequestId":"9C103591-2533-432B-9E6B-6DB098C0E65C",
	"UnhealthyThreshold":3,
	"BackendServerPort":34,
	"Bandwidth":67
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

