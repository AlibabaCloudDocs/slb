# DescribeLoadBalancerUDPListenerAttribute

Queries the configurations of a UDP listener.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerUDPListenerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeLoadBalancerUDPListenerAttribute|The operation that you want to perform.

 Set the value to DescribeLoadBalancerUDPListenerAttribut. |
|ListenerPort|Integer|Yes|80|The frontend port that is used by the SLB instance.

 Valid values: **1 to 65535**. |
|LoadBalancerId|String|Yes|lb-bp1rtfnodmywb43e\*\*\*\*\*|The ID of an SLB instance. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region where the SLB instance is deployed. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ListenerPort|Integer|53|The frontend port that is used by the SLB instance. |
|BackendServerPort|Integer|53|The backend port that is used by the SLB instance.

 **Note:** If the listener is associated with a VServer group, this parameter is not returned. |
|Status|String|stopped|The status of the listener.

 Valid Values: **running and stopped**.

 -   **running**: indicates that the listener is running as expected.
-   **stopped**: indicates that the listener is stopped. |
|Bandwidth|Integer|-1|The maximum bandwidth of the listener. |
|Scheduler|String|wrr|The scheduling algorithm.

 -   **wrr**: Backend servers with higher weights receive more requests than those with lower weights.
-   **wlc**: Requests are forwarded based on the weight and load of each backend server. The load is based on the number of connections to a backend server.

If two backend servers have the same weight, the backend server with fewer connections is expected to receive more requests.

-   **rr**: Requests are sequentially distributed to backend servers. This is the default forwarding algorithm. |
|HealthCheck|String|on|Indicates whether health checks are enabled.

 Valid values: **on and off**. |
|HealthyThreshold|Integer|4|The healthy threshold. |
|UnhealthyThreshold|Integer|4|The unhealthy threshold. |
|HealthCheckConnectTimeout|Integer|100|The health check response timeout. |
|HealthCheckConnectPort|Integer|8080|The port that is used for health checks.

 **Note:** This parameter takes effect only when the **HealthCheck** parameter is set to **on**. |
|HealthCheckInterval|Integer|5|The interval between two consecutive health checks. Unit: seconds. |
|HealthCheckReq|String|hello|A request string for health check of the UDP listener. |
|HealthCheckExp|String|ok|A response string for health check of the UDP listener. |
|VServerGroupId|String|rsp-cige6j\*\*\*\*\*|The ID of the VServer group that is associated with the listener. |
|MasterSlaveServerGroupId|String|rsp-0bfucw\*\*\*\*|The ID of the primary/secondary server group that is associated with the listener. |
|AclId|String|123943\*\*\*\*\*|The ID of the access control list \(ACL\). |
|AclType|String|white|The type of ACL.

 -   white:

the ACL is specified as a whitelist. Only requests from the IP addresses or CIDR blocks in the ACL are forwarded. Whitelists apply to scenarios that require you to allow only specific IP addresses to access an application.

Risks may arise if you specify an ACL as a whitelist. The whitelist allows only network traffic from the IP addresses in the specified ACL to access the SLB listener. If a whitelist is enabled without any IP addresses specified, the SLB listener does not forward any requests.

-   black:

the ACL is specified as a blacklist. All requests from the IP addresses or CIDR blocks in the ACL are rejected. Blacklists apply to scenarios that require you to block access from specific IP addresses to an application.

If the blacklist is enabled but the corresponding ACL does not contain any IP addresses, the SLB listener forwards all requests. |
|AclStatus|String|off|Indicates whether access control is enabled for the listener.

 Valid values: **on and off**. Default value: off. |
|Description|String|The description of access control.|The description of access control. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancerUDPListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1rtfnodmywb43e*****
&<Common request parameters>
```

Sample success responses

`XML` format

```
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

```
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

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

