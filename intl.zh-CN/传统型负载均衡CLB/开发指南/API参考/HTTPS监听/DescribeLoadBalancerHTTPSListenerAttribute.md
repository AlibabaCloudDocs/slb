# DescribeLoadBalancerHTTPSListenerAttribute

调用DescribeLoadBalancerHTTPSListenerAttribute查询HTTPS监听配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPSListenerAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerHTTPSListenerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerHTTPSListenerAttribute**。 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。 |
|LoadBalancerId|String|是|lb-bp1mxu5r8lau\*\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。 |
|BackendServerPort|Integer|80|负载均衡实例后端使用的端口。 |
|Bandwidth|Integer|-1|监听的带宽峰值。 |
|Status|String|stopped|当前监听的状态。

 取值：**running\|stopped**。 |
|SecurityStatus|String|on|安全状态。

 取值：**on\|off**。 |
|XForwardedFor|String|on|是否开启通过X-Forwarded-For的方式获取来访者真实IP。

 取值：**on \| off**。 |
|Scheduler|String|wrr|调度算法。

 取值：**wrr \| wlc \| rr**。

 -   wrr（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   wlc：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   rr：按照访问顺序依次将外部请求依序分发到后端服务器。 |
|StickySession|String|on|是否开启会话保持。

 取值：**on \| off**。 |
|StickySessionType|String|insert|cookie的处理方式。当StickySession的值为**on**时，必须指定该参数。

 取值：**insert \| server**。

 -   insert：植入Cookie。

客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP/HTTPS响应报文中插入SERVERID），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。

-   server：重写Cookie。

负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。


 **说明：** 当**StickySession**的值为**on**时，必须指定该参数。 |
|CookieTimeout|Integer|500|cookie超时时间。 |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|服务器上配置的cookie。 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on \| off**。 |
|HealthCheckDomain|String|www.test.com|用于健康检查的域名。 |
|HealthCheckURI|String|/test/index.html|用于健康检查的URI。

 长度限制为1~80，只能使用字母、数字和-/.%?\#&这些字符。 URL不能只为/，但必须以/开头。 |
|HealthyThreshold|Integer|4|健康检查阈值。 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。 |
|HealthCheckTimeout|Integer|3|每次健康检查响应的最大超时间，单位为秒。 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，单位为秒。 |
|HealthCheckConnectPort|Integer|8080|健康检查的端口。

 **说明：** 当**HealthCheck**值为**on**时才会有效。 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|健康检查正常的HTTP状态码。 |
|ServerCertificateId|String|idkp-123-cn-test-0\*\*|服务器证书的ID。 |
|CACertificateId|String|idkp-234-cn-test-0\*\*|CA证书ID。 |
|VServerGroupId|String|rsp-cige6j5e\*\*\*\*\*\*\*\*|绑定的服务器组ID。 |
|Gzip|String|on|是否开启Gzip压缩。

 取值：**on \| off**。 |
|XForwardedFor\_SLBIP|String|on|是否通过`SLB-IP`头字段获取客户端请求的真实IP。

 取值：**on \| off**。 |
|XForwardedFor\_SLBID|String|on|是否通过`SLB-ID`头字段获取负载均衡实例ID。

 取值：**on \| off**。 |
|XForwardedFor\_proto|String|on|是否通过`X-Forwarded-Proto`头字段获取负载均衡实例的监听协议。

 取值：**on \| off**。 |
|AclId|String|45|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclType|String|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发任何请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。 |
|AclStatus|String|off|是否开启访问控制功能。

 取值：**on \| off**（默认值）。 |
|RequestTimeout|Integer|43|指定请求超时时间，取值范围为1-180秒，默认值为60秒。

 在超时时间内后端服务器一直没有响应，负载均衡将放弃等待，给客户端返回HTTP 504错误码。 |
|IdleTimeout|Integer|23|指定连接空闲超时时间，取值范围为1-60秒，默认值为15秒。

 在超时时间内一直没有访问请求，负载均衡会暂时中断当前连接，直到一下次请求来临时重新建立新的连接。 |
|EnableHttp2|String|off|是否开启HTTP/2特性。

 取值：**on**（默认值）**\| off**。 |
|TLSCipherPolicy|String|tls\_cipher\_policy\_1\_0|只有性能保障型实例才可以指定TLSCipherPolicy参数，每种policy定义了一种安全策略，安全策略包含HTTPS可选的TLS协议版本和配套的加密算法套件。

 目前支持以下四种安全策略，详细区别请参见TLS安全策略差异说明，请根据实际情况选择对应的policy。

 -   **tls\_cipher\_policy\_1\_0**：

支持TLS版本： TLSv1.0、TLSv1.1和TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-   **tls\_cipher\_policy\_1\_1**：

支持TLS版本： TLSv1.1和TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-   **tls\_cipher\_policy\_1\_2**

支持TLS版本：TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-   **tls\_cipher\_policy\_1\_2\_strict**

支持TLS版本：TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、ECDHE-RSA-AES128-SHA和ECDHE-RSA-AES256-SHA。 |
|Description|String|监听描述|监听描述。 |
|XForwardedFor\_SLBPORT|String|off|通过`XForwardedFor_SLBPORT`头字段获取负载均衡实例的监听端口。

 取值：**on \| off**。 |
|XForwardedFor\_ClientSrcPort|String|off|通过`XForwardedFor_ClientSrcPort`头字段获取访问负载均衡实例客户端的端口。

 取值：**on \| off**。 |
|XForwardedFor\_ClientCertSubjectDN|String|off|通过`XForwardedFor_ClientCertSubjectDN`头字段获取访问负载均衡实例客户端证书的所有者信息。

 取值：**on \| off**。 |
|XForwardedFor\_ClientCertIssuerDN|String|off|通过`XForwardedFor_ClientCertIssuerDN`头字段获取访问负载均衡实例客户端证书的发行者信息。

 取值：**on \| off**。 |
|XForwardedFor\_ClientCertFingerprint|String|off|通过`XForwardedFor_ClientCertFingerprint`头字段获取访问负载均衡实例客户端证书的指纹。

 取值：**on \| off**。 |
|XForwardedFor\_ClientCertClientVerify|String|off|通过XForwardedFor\_ClientCertClientVerify头字段获取对访问负载均衡实例客户端证书的校验结果。

 取值：**on \| off**。 |
|Rules|Array| |监听下的转发规则列表。 |
|RuleId|String|23|转发规则ID。 |
|RuleName|String|example|转发规则名称。 |
|Domain|String|www.example.com|域名。 |
|Url|String|/example|访问路径。 |
|VServerGroupId|String|12|转发规则的目标服务器组ID。 |
|DomainExtensions|Array| |域名扩展列表。 |
|DomainExtensionId|String|12|域名扩展ID。 |
|Domain|String|www.example.com|域名。 |
|ServerCertificateId|String|133444444565|与域名对应的证书ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancerHTTPSListenerAttribute
&ListenerPort=80
&LoadBalancerId=lb-bp1mxu5r8lau*******
&<公共请求参数>
```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

