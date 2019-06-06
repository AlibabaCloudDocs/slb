# DescribeLoadBalancerHTTPSListenerAttribute {#doc_api_Slb_DescribeLoadBalancerHTTPSListenerAttribute .reference}

Queries the configurations of an HTTPS listener.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPSListenerAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerHTTPSListenerAttribute|The name of this action. Value:**DescribeLoadBalancerHTTPSListenerAttribute**

 |
|ListenerPort|Integer|Yes|80|The frontend port used by the SLB instance. Value range:**1 to 65535**

 |
|LoadBalancerId|String|Yes|lb-bp1mxu5r8laukr35n1k5r|The ID of the SLB instance.

 |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|ListenerPort|Integer|80|The frontend port used by the SLB instance.

 |
|BackendServerPort|Integer|80|The backend port used by the SLB instance.

 |
|Bandwidth|Integer  |-1|The peak bandwidth of the listener.

 |
|Status|String|stopped|The status of the listener.

 Valid values: **starting | running | configuring | stopping | stopped**

 |
|XForwardedFor|String|on|Indicates whether to use the X-Forwarded-For record to obtain the real IP address of a visitor.

 Valid values: **on | off**

 |
|Scheduler|String|wrr|The algorithm used to distribute traffic. 

 Valid values: **wrr | wlc | rr**

 |
|StickySession|String|on|Indicates whether to enable session persistence.

 Valid values: **on | off**

 |
|StickySessionType|String|on|The method used to handle the cookie. When the value of StickySession is **on**, this parameter is required.

 Valid values: **insert | server**

 |
|CookieTimeout|Integer|500|Timeout period of the cookie.

 |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|The cookie configured on the backend server.

 |
|HealthCheck|String|on|Indicates whether to enable the health check function.

 Valid values: **on | off**

 |
|HealthCheckDomain|String|$\_ip|The domain name used for health checks.

 |
|HealthCheckURI|String|/test/index.html|The URI used for health checks.

 |
|HealthyThreshold|Integer|4|The number of consecutive successes of health checks before a backend server is declared as healthy \(from failure to success\).

 |
|UnhealthyThreshold|Integer|4|The number of consecutive failures of health checks before a backend server is declared as unhealthy \(from success to failure\).

 |
|HealthCheckTimeout|Integer|3|The maximum amount of time to wait for the response from a health check. Unit: seconds

 |
|HealthCheckInterval|Integer|5|The time interval between two consecutive health checks. Unit: seconds

 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|The HTTP status code indicating that the health check is normal.

 |
|HealthCheckConnectPort|Integer|8080|The port used for health checks.

 |
|ServerCertificateId|String|idkp-123-cn-test-01|The ID of the server certificate.

 |
|CACertificateId|String|idkp-234-cn-test-02|The ID of the CA certificate.

 |
|VServerGroupId|String|rsp-cige6j5e7p|The ID of the VServer group.

 |
|Gzip|String|on|Indicates whether to enable Gzip compression.

 Valid values: **on | off**

 |
|AclId|String|45|The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|AclStatus|String|off|Indicates whether to enable access control.

 Valid values:**on | off**. Default value: off

 |
|AclType|String|white|The access control type:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is enabled, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the list, no requests are forwarded.

-   **black**: Indicates a blacklist. Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded \(that is, they are blocked\). It applies to scenarios where an application only denies access from specific IP addresses.

If you enable a blacklist without adding any IP addresses to the list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required.

 |
|Description|String|A description of the listener|A description of the listener.

 |
|DomainExtensions| | |Domain name extension list.

 |
|└Domain|String|www.example.com|The domain name.

 |
|└DomainExtensionId|String|12|The ID of the domain name extension.

 |
|└ServerCertificateId|String|133444444565|The ID of the certificate corresponding to the domain name.

 |
|EnableHttp2|String|off|Indicates whether to enable the HTTP/2 feature.

 Valid values:**on** | **off**. Default value: on

 |
|IdleTimeout|Integer|23|Specify the idle connection timeout. Value range: 1 to 60. Default value: 15. Unit: seconds

 If no request is received during the specified timeout period, SLB will temporarily terminate the connection and restart the connection when the next request is received.

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|Request ID.

 |
|RequestTimeout|Integer|43|Specify the request timeout. Value range: 1 to 180. Default value: 60. Unit: seconds

 If no response is received from the backend server during the specified timeout period, SLB will stop waiting and send an HTTP 504 error code to the client.

 |
|Rules| | |A list of forwarding rules of the listener.

 |
|└Domain|String|www.example.com|The domain name.

 |
|└RuleId|String|23|The ID of the forwarding rule.

 |
|└RuleName|String|example|The name of the forwarding rule.

 |
|└Url|String|/example|The access path.

 |
|└VServerGroupId|String|12|The ID of the target VServer group of the forwarding rule.

 |
|SecurityStatus|String|on|The security status.

 |
|TLSCipherPolicy|String|tls\_cipher\_policy\_1\_0|You can only specify the TLSCipherPolicy parameter for guaranteed-performance instances. Each security policy includes the TLS protocol versions that can be selected by HTTPS and the supported cipher suites.

 Currently, the following four security policies are supported. For more information about their differences, see the introduction to the differences of TLS security policies.

 -   **tls\_cipher\_policy\_1\_0**:

Supported TLS versions: TLSv1.0, TLSv1.1, and TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-   **tls\_cipher\_policy\_1\_1**:

Supported TLS versions: TLSv1.1 and TLSv1.2.

Supported encryption algorithm suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-    **tls\_cipher\_policy\_1\_2** 

Supported TLS version: TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-    **tls\_cipher\_policy\_1\_2\_strict** 

Supported TLS version: TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA.


 |
|XForwardedFor\_SLBID|String|on|Indicates whether to use the `SLB-ID` header field to obtain the SLB instance ID.

 Valid values: **on | off**

 |
|XForwardedFor\_SLBIP|String|on|Indicates whether to use the `SLB-IP` header field to obtain the real IP address of a client.

 Valid values: **on | off**

 |
|XForwardedFor\_proto|String|on|Indicates whether to use the `X-Forwarded-Proto` header field to obtain the listening protocol of the SLB instance.

 Valid values: **on | off**

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=DescribeLoadBalancerHTTPSListenerAttribute
&ListenerPort=80 
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01 
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeLoadBalancerHTTPSListenerAttributeResponse> 
  <RequestId>11F52428-64ED-40F7-98C2-DBB6D0BB0AD7</RequestId> 
  <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode> 
  <HealthCheckTimeout>5</HealthCheckTimeout> 
  <ServerCertificateId>1231579xxxxxxxx_15dbf6ff26f_1991415478_2054196746</ServerCertificateId>
  <XForwardedFor_SLBID>off</XForwardedFor_SLBID> 
  <Gzip>on</Gzip> 
  <HealthyThreshold>3</HealthyThreshold> 
  <Scheduler>wrr</Scheduler> 
  <StickySession>off</StickySession> 
  <UnhealthyThreshold>3</UnhealthyThreshold> 
  <XForwardedFor_SLBIP>off</XForwardedFor_SLBIP> 
  <XForwardedFor_proto>off</XForwardedFor_proto> 
  <Bandwidth>-1</Bandwidth>
  <HealthCheckURI>/</HealthCheckURI>
  <VServerGroupId>rsp-0xiju72xwnr93</VServerGroupId>
  <HealthCheck>on</HealthCheck> 
  <ListenerPort>443</ListenerPort> 
  <Status>running</Status>
  <XForwardedFor>on</XForwardedFor> 
  <HealthCheckDomain/> 
  <HealthCheckInterval>2</HealthCheckInterval> 
  <BackendServerPort>443</BackendServerPort> 
</DescribeLoadBalancerHTTPSListenerAttributeResponse> 

```

`JSON` format

``` {#json_return_success_demo}
{
	"HealthCheckHttpCode":"http_2xx,http_3xx",
	"HealthCheckURI":"/",
	"VServerGroupId":"rsp-0xiju72xwnr93",
	"HealthCheckTimeout":5,
	"HealthCheck":"on",
	"ListenerPort":443,
	"ServerCertificateId":"1231579xxxxxxxx_15dbf6ff26f_1991415478_2054196746",
	"Status":"running",
	"XForwardedFor_SLBID":"off",
	"Gzip":"on",
	"XForwardedFor":"on",
	"HealthCheckInterval":2,
	"HealthCheckDomain":"",
	"HealthyThreshold":3,
	"Scheduler":"wrr",
	"RequestId":"11F52428-64ED-40F7-98C2-DBB6D0BB0AD7",
	"StickySession":"off",
	"UnhealthyThreshold":3,
	"XForwardedFor_SLBIP":"off",
	"XForwardedFor_proto":"off",
	"BackendServerPort":443,
	"Bandwidth":-1
}
```

## Error codes { .section}

[See common error codes.](https://error-center.aliyun.com/status/product/Slb)

