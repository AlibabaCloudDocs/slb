# DescribeLoadBalancerHTTPSListenerAttribute

Queries the configurations of an HTTPS listener.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPSListenerAttribute&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeLoadBalancerHTTPSListenerAttribute|The name of this action.

 Value: **DescribeLoadBalancerHTTPSListenerAttribute** |
|ListenerPort|Integer|Yes|80|The frontend port used by the HTTPS listener.

 Value range: **1 to 65535** |
|LoadBalancerId|String|Yes|lb-bp1mxu5r8lau\*\*\*\*\*\*\*|The ID of the Server Load Balancer \(SLB\) instance to which the HTTPS listener belongs. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to which the SLB instance belongs. |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|The ID of the request. |
|ListenerPort|Integer|80|The frontend port used by the HTTPS listener. |
|BackendServerPort|Integer|80|The backend port used by the HTTPS listener. |
|Bandwidth|Integer|-1|The peak bandwidth of the listener. |
|Status|String|stopped|The status of the listener.

 Valid values: **running \| stopped** |
|SecurityStatus|String|on|The security status of the listener.

 Valid values: **on \| off** |
|XForwardedFor|String|on|Indicates whether the X-Forwarded-For header field is used to retrieve real IP addresses of client requests.

 Valid values: **on \| off** |
|Scheduler|String|wrr|The algorithm used for distributing traffic.

 Valid values: **wrr \| wlc \| rr**

 -   wrr \(default\): A backend server with a higher weight receives more requests.
-   wlc: A backend server with a higher weight receives more requests. If the weight values of two backend servers are the same, the backend server with a smaller number of connections is more likely to be polled.
-   rr: Requests are evenly and sequentially distributed to backend servers. |
|StickySession|String|on|Indicates whether session persistence is enabled.

 Valid values: **on \| off** |
|StickySessionType|String|insert|The method used to handle the cookie. If the value of StickySession is **on**, this parameter is required.

 Valid values: **insert \| server**

 -   insert: Insert the cookie.

SLB adds a cookie to the first response from the backend server \(inserts SERVERID in the HTTP and HTTPS response packet\). The next request will contain the cookie and the listener will distribute the request to the same backend server.

-   server: Rewrite the cookie.

SLB overwrites the original cookie when it discovers that a new cookie is set. The next time the client carries the new cookie to access SLB, the listener will distribute the request to the recorded backend server.


 **Note:** If the value of **StickySession** is **on**, this parameter is required. |
|CookieTimeout|Integer|500|The timeout period of the cookie. |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|The cookie configured on the server. |
|HealthCheck|String|on|Indicates whether the health check function is enabled.

 Valid values: **on \| off** |
|HealthCheckDomain|String|www.test.com|The domain name used for health checks. |
|HealthCheckURI|String|/test/index.html|The URI used for health checks.

 The URI must be 1 to 80 characters in length. It can contain letters, numbers, hyphens \(-\), forward slashes \(/\), periods \(.\), percent signs \(%\), question marks \(?\), number signs \(\#\), and ampersands \(&\). The URL cannot only contain a forward slash \(/\), but must start with a forward slash \(/\). |
|HealthyThreshold|Integer|4|The number of consecutive successful health checks that must occur before a backend server is declared as healthy \(from failure to success\). |
|UnhealthyThreshold|Integer|4|The number of consecutive failed health checks that must occur before a backend server is declared as unhealthy \(from success to failure\). |
|HealthCheckTimeout|Integer|3|The timeout period of a health check. |
|HealthCheckInterval|Integer|5|The interval between two consecutive health checks. |
|HealthCheckConnectPort|Integer|8080|The port used for health checks.

 **Note:** This parameter is valid only when the value of the **HealthCheck** parameter is **on**. |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|The HTTP status code indicating that a health check is successful. |
|ServerCertificateId|String|idkp-123-cn-test-0\*\*|The ID of the server certificate. |
|CACertificateId|String|idkp-234-cn-test-0\*\*|The ID of the CA certificate. |
|VServerGroupId|String|rsp-cige6j5e\*\*\*\*\*\*\*\*|The ID of the VServer group associated with the listener. |
|Gzip|String|on|Indicates whether gzip compression is enabled to compress a specific file type.

 Valid values: **on \| off** |
|XForwardedFor\_SLBIP|String|on|Indicates whether the `SLB-IP` header field is used to retrieve real IP addresses of client requests.

 Valid values: **on \| off** |
|XForwardedFor\_SLBID|String|on|Indicates whether the `SLB-ID` header field is used to retrieve the SLB instance ID.

 Valid values: **on \| off** |
|XForwardedFor\_proto|String|on|Indicates whether the `X-Forwarded-Proto` header field is used to retrieve the listening protocol of the SLB instance.

 Valid values: **on \| off** |
|AclId|String|45|The ID of the access control list associated with the listener.

 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclType|String|white|The access control method. Valid values:

 -   **white**: Indicates a whitelist. Only requests from the IP addresses or CIDR blocks in the selected access control list are forwarded. This method applies to scenarios where an application allows access only from specific IP addresses.

Enabling a whitelist poses some risks to your services.

After a whitelist is configured, only the IP addresses in the list can access the listener.

If you enable a whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

-   **black**: Indicates a blacklist. Requests from the IP addresses or CIDR blocks in the selected access control list are not forwarded \(that is, they are blocked\). This method applies to scenarios where an application denies access only from specific IP addresses.

If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


 If the value of the **AclStatus** parameter is **on**, this parameter is required. |
|AclStatus|String|off|Indicates whether access control is enabled.

 Valid values: **on \| off**. Default value: off |
|RequestTimeout|Integer|43|The timeout period of a request. Value range: 1 to 180. Default value: 60. Unit: seconds

 If no response is received from the backend server during the specified timeout period, SLB stops waiting and sends an HTTP 504 error code to the client. |
|IdleTimeout|Integer|23|The timeout period of an idle connection. Value range: 1 to 60. Default value: 15. Unit: seconds

 If no request is received during the specified timeout period, SLB temporarily terminates the connection and restarts the connection until the next request is received. |
|EnableHttp2|String|off|Indicates whether HTTP/2 is enabled.

 Valid values: **on****\| off**. Default value: on |
|TLSCipherPolicy|String|tls\_cipher\_policy\_1\_0|You can only specify the TLSCipherPolicy parameter for guaranteed-performance instances. Each security policy includes the TLS protocol versions that can be selected by HTTPS and the supported cipher suites.

 Currently, the following four security policies are supported. For more information about their differences, see the description of differences in TLS security policies.

 -   **tls\_cipher\_policy\_1\_0**:

Supported TLS versions: TLSv1.0, TLSv1.1, and TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-   **tls\_cipher\_policy\_1\_1**:

Supported TLS versions: TLSv1.1 and TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-   **tls\_cipher\_policy\_1\_2**

Supported TLS version: TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, AES128-GCM-SHA256, AES256-GCM-SHA384, AES128-SHA256, AES256-SHA256, ECDHE-RSA-AES128-SHA, ECDHE-RSA-AES256-SHA, AES128-SHA, AES256-SHA, and DES-CBC3-SHA.

-   **tls\_cipher\_policy\_1\_2\_strict**

Supported TLS version: TLSv1.2.

Supported cipher suites: ECDHE-RSA-AES128-GCM-SHA256, ECDHE-RSA-AES256-GCM-SHA384, ECDHE-RSA-AES128-SHA256, ECDHE-RSA-AES256-SHA384, ECDHE-RSA-AES128-SHA, and ECDHE-RSA-AES256-SHA. |
|Description|String|Listener description|The description of the listener. |
|XForwardedFor\_SLBPORT|String|off|Indicates whether the `XForwardedFor_SLBPORT` header field is used to retrieve the listening port of the SLB instance.

 Valid values: **on \| off** |
|XForwardedFor\_ClientSrcPort|String|off|Indicates whether the `XForwardedFor_ClientSrcPort` header field is used to retrieve the client port used to access the SLB instance.

 Valid values: **on \| off** |
|XForwardedFor\_ClientCertSubjectDN|String|off|Indicates whether the `XForwardedFor_ClientCertSubjectDN` header field is used to retrieve the owner information of the client certificate used to access the SLB instance.

 Valid values: **on \| off** |
|XForwardedFor\_ClientCertIssuerDN|String|off|Indicates whether the `XForwardedFor_ClientCertIssuerDN` header field is used to retrieve the information of the authority that issues the client certificate.

 Valid values: **on \| off** |
|XForwardedFor\_ClientCertFingerprint|String|off|Indicates whether the `XForwardedFor_ClientCertFingerprint` header field is used to retrieve the fingerprint of the client certificate.

 Valid values: **on \| off** |
|XForwardedFor\_ClientCertClientVerify|String|off|Indicates whether the XForwardedFor\_ClientCertClientVerify header field is used to retrieve the verification result of the client certificate.

 Valid values: **on \| off** |
|Rules|Array| |The list of forwarding rules of the listener. |
|RuleId|String|23|The ID of the forwarding rule. |
|RuleName|String|example|The name of the forwarding rule. |
|Domain|String|www.example.com|The domain name specified in the forwarding rule. |
|Url|String|/example|The URL specified in the forwarding rule. |
|VServerGroupId|String|12|The ID of the target VServer group of the forwarding rule. |
|DomainExtensions|Array| |The list of domain extensions. |
|DomainExtensionId|String|12|The ID of the domain extension. |
|Domain|String|www.example.com|The domain name. |
|ServerCertificateId|String|133444444565|The ID of the certificate used for the domain name. |

## Examples

Request example

```
http(s)://[Endpoint]/? Action=DescribeLoadBalancerHTTPSListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1mxu5r8lau*******
&<CommonParameters>
```

Response example

`XML` format

```
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
      <VServerGroupId>rsp-0xiju72x******</VServerGroupId>
      <HealthCheck>on</HealthCheck>
      <ListenerPort>443</ListenerPort>
      <Status>running</Status>
      <XForwardedFor>on</XForwardedFor>
      <HealthCheckDomain></HealthCheckDomain>
      <HealthCheckInterval>2</HealthCheckInterval>
      <BackendServerPort>443</BackendServerPort>
</DescribeLoadBalancerHTTPSListenerAttributeResponse>
```

`JSON` format

```
{
    "RequestId": "11F52428-64ED-40F7-98C2-DBB6D0BB0AD7",
    "HealthCheckHttpCode": "http_2xx,http_3xx",
    "HealthCheckTimeout": 5,
    "ServerCertificateId": "1231579xxxxxxxx_15dbf6ff26f_1991415478_2054196746",
    "XForwardedFor_SLBID": "off",
    "Gzip": "on",
    "HealthyThreshold": 3,
    "Scheduler": "wrr",
    "StickySession": "off",
    "UnhealthyThreshold": 3,
    "XForwardedFor_SLBIP": "off",
    "XForwardedFor_proto": "off",
    "Bandwidth": -1,
    "HealthCheckURI": "/",
    "VServerGroupId": "rsp-0xiju72x******",
    "HealthCheck": "on",
    "ListenerPort": 443,
    "Status": "running",
    "XForwardedFor": "on",
    "HealthCheckDomain": "",
    "HealthCheckInterval": 2,
    "BackendServerPort": 443
}
```

## Errors

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

