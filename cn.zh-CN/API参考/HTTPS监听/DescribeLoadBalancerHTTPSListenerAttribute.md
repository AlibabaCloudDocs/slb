# DescribeLoadBalancerHTTPSListenerAttribute {#doc_api_Slb_DescribeLoadBalancerHTTPSListenerAttribute .reference}

使用DescribeLoadBalancerHTTPSListenerAttribute查询HTTPS监听配置。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerHTTPSListenerAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerHTTPSListenerAttribute|要执行的操作。取值：**DescribeLoadBalancerHTTPSListenerAttribute**

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。取值：**1-65535**

 |
|LoadBalancerId|String|是|lb-bp1mxu5r8laukr35n1k5r|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|ListenerPort|Integer|80|负载均衡实例前端使用的端口。

 |
|BackendServerPort|Integer|80|负载均衡实例后端使用的端口。

 |
|Bandwidth|Integer|-1|监听的带宽峰值。

 |
|Status|String|stopped|当前监听的状态。

 取值：**starting | running | configuring | stopping | stopped**

 |
|XForwardedFor|String|on|是否开启通过X-Forwarded-For的方式获取来访者真实IP。

 取值：**on | off**

 |
|Scheduler|String|wrr|调度算法。

 取值：**wrr | wlc | rr**

 |
|StickySession|String|on|是否开启会话保持。

 取值：**on | off**

 |
|StickySessionType|String|on|cookie的处理方式。当StickySession的值为**on**时，必须指定该参数。

 取值：**insert | server**

 |
|CookieTimeout|Integer|500|cookie超时时间。

 |
|Cookie|String|B490B5EBF6F3CD402E515D22BCDA1598|服务器上配置的cookie。

 |
|HealthCheck|String|on|是否开启健康检查。

 取值：**on | off**

 |
|HealthCheckDomain|String|$\_ip|用于健康检查的域名。

 |
|HealthCheckURI|String|/test/index.html|用于健康检查的URI。

 |
|HealthyThreshold|Integer|4|健康检查阈值。

 |
|UnhealthyThreshold|Integer|4|不健康检查阈值。

 |
|HealthCheckTimeout|Integer|3|每次健康检查响应的最大超时间，单位为秒。

 |
|HealthCheckInterval|Integer|5|健康检查的时间间隔，单位为秒。

 |
|HealthCheckHttpCode|String|http\_2xx,http\_3xx|健康检查正常的HTTP状态码。

 |
|HealthCheckConnectPort|Integer|8080|健康检查的端口。

 |
|ServerCertificateId|String|idkp-123-cn-test-01|服务器证书的ID。

 |
|CACertificateId|String|idkp-234-cn-test-02|CA证书ID。

 |
|VServerGroupId|String|rsp-cige6j5e7p|绑定的服务器组ID。

 |
|Gzip|String|on|是否开启Gzip压缩。

 取值：**on | off**

 |
|AclId|String|45|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|AclStatus|String|off|是否开启访问控制功能。

 取值：**on | off**（默认值）

 |
|AclType|String|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。

一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。

如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听不会转发任何请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|Description|String|监听描述|监听描述。

 |
|DomainExtensions| | |域名扩展列表。

 |
|└Domain|String|www.example.com|域名。

 |
|└DomainExtensionId|String|12|域名扩展ID。

 |
|└ServerCertificateId|String|133444444565|与域名对应的证书ID。

 |
|EnableHttp2|String|off|是否开启HTTP/2特性。

 取值：**on**（默认值）**| off**

 |
|IdleTimeout|Integer|23|指定连接空闲超时时间，取值范围为1-60秒，默认值为15秒。

 在超时时间内一直没有访问请求，负载均衡会暂时中断当前连接，直到一下次请求来临时重新建立新的连接。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |
|RequestTimeout|Integer|43|指定请求超时时间，取值范围为1-180秒，默认值为60秒。

 在超时时间内后端服务器一直没有响应，负载均衡将放弃等待，给客户端返回HTTP 504错误码。

 |
|Rules| | |监听下的转发规则列表。

 |
|└Domain|String|www.example.com|域名。

 |
|└RuleId|String|23|转发规则ID。

 |
|└RuleName|String|example|转发规则名称。

 |
|└Url|String|/example|访问路径。

 |
|└VServerGroupId|String|12|转发规则的目标服务器组ID。

 |
|SecurityStatus|String|on|安全状态。

 |
|TLSCipherPolicy|String|tls\_cipher\_policy\_1\_0|只有性能保障型实例才可以指定TLSCipherPolicy参数，每种policy定义了一种安全策略，安全策略包含HTTPS可选的TLS协议版本和配套的加密算法套件。

 目前支持以下四种安全策略，详细区别请参见TLS安全策略差异说明，请根据实际情况选择对应的policy。

 -   **tls\_cipher\_policy\_1\_0**：

支持TLS版本： TLSv1.0、TLSv1.1和TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-   **tls\_cipher\_policy\_1\_1**：

支持TLS版本： TLSv1.1和TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-    **tls\_cipher\_policy\_1\_2** 

支持TLS版本：TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。

-    **tls\_cipher\_policy\_1\_2\_strict** 

支持TLS版本：TLSv1.2。

支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、ECDHE-RSA-AES128-SHA和ECDHE-RSA-AES256-SHA。


 |
|XForwardedFor\_SLBID|String|on|是否通过`SLB-ID`头字段获取负载均衡实例ID。

 取值：**on | off**

 |
|XForwardedFor\_SLBIP|String|on|是否通过`SLB-IP`头字段获取客户端请求的真实IP。

 取值：**on | off**

 |
|XForwardedFor\_proto|String|on|是否通过`X-Forwarded-Proto`头字段获取负载均衡实例的监听协议。

 取值：**on | off**

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=DescribeLoadBalancerHTTPSListenerAttribute
&ListenerPort=80
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<公共请求参数>

```

正常返回示例

`XML` 格式

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

`JSON` 格式

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

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

