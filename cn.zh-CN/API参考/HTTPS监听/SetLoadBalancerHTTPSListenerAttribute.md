# SetLoadBalancerHTTPSListenerAttribute {#doc_api_Slb_SetLoadBalancerHTTPSListenerAttribute .reference}

调用SetLoadBalancerHTTPSListenerAttribute修改HTTPS监听的配置。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerHTTPSListenerAttribute)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetLoadBalancerHTTPSListenerAttribute|要执行的操作。

 取值：**SetLoadBalancerHTTPSListenerAttribute**。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|139a00604ad-cn-east-hangzhou-01|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|AclId|String|否|56565|监听绑定的访问策略组ID。

 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|AclStatus|String|否|off|是否开启访问控制功能。

 取值：**on|off**。

 |
|AclType|String|否|white|访问控制类型：

 -   **white**： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   **black**： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


 当**AclStatus**参数的值为**on**时，该参数必选。

 |
|Bandwidth|Integer|否|-1|监听的带宽峰值。

 取值：**1|1-5120**。

 -   **-1**：不限制带宽峰值。
-   **1-5120**：监听的带宽峰值，所有监听的带宽峰值之和不能超过实例的带宽峰值。

 |
|CACertificateId|String|否|139a00604ad-cn-east-hangzhou-01|CA证书ID。

 若既上传CA证书又上传服务器证书，即采用双向认证；若用户只上传服务器证书，即为单向认证。

 |
|Cookie|String|否|B490B5EBF6F3CD402E515D22BCDA1598|服务器上配置的Cookie。

 长度为1-200个字符，只能包含ASCII英文字母和数字字符，不能包含逗号、分号或空格，也不能以$开头。

 当**StickySession**为**on**且**StickySessionType**为**server**时，该参数必选。

 |
|CookieTimeout|Integer|否|500|Cookie超时时间。

 取值：**1-86400**（秒）。

 **说明：** 当**StickySession**为**on**且**StickySessionType**为**insert**时，该参数必选。

 |
|Description|String|否|监听描述|监听描述。

 |
|EnableHttp2|String|否|off|是否开启HTTP/2特性。

 取值：**on|off**。

 |
|Gzip|String|否|on|是否开启Gzip压缩，对特定文件类型进行压缩。

 取值：**on|off**（默认值）。

 |
|HealthCheck|String|否|on|是否开启健康检查。

 取值：**on|off**。

 |
|HealthCheckConnectPort|Integer|否|8080|健康检查使用的端口。

 取值：**1-65535**。

 |
|HealthCheckDomain|String|否|$\_ip|用于健康检查的域名，取值：

 -   **$\_ip**： 后端服务器的私网IP。当指定了IP或该参数未指定时，负载均衡会使用各后端服务器的私网IP当做健康检查使用的域名。
-   **domain**：域名长度为1-80字符，只能包含字母、数字、点号（.）和连字符（-）。

 |
|HealthCheckHttpCode|String|否|http\_2xx,http\_3xx|健康检查正常的HTTP状态码，多个状态码用逗号（,）分割。

 取值：**http\_2xx|http\_3xx|http\_4xx|http\_5xx**。

 |
|HealthCheckInterval|Integer|否|5|健康检查的时间间隔。

 取值：**1-50**（秒）。

 |
|HealthCheckTimeout|Integer|否|3|接收来自运行状况检查的响应需要等待的时间。如果后端ECS在指定的时间内没有正确响应，则判定为健康检查失败。

 取值：**1-300**（秒）。

 **说明：** 如果**HealthCHeckTimeout**的值小于**HealthCheckInterval**的值，则**HealthCHeckTimeout**无效，超时时间为**HealthCheckInterval**的值。

 |
|HealthCheckURI|String|否|/test/index.html|用于健康检查的URI。

 |
|HealthyThreshold|Integer|否|4|健康检查连续成功多少次后，将后端服务器的健康检查状态由**fail**判定为**success**。

 取值：**2-10**。

 |
|IdleTimeout|Integer|否|23|指定连接空闲超时时间，取值范围为1-60秒，默认值为15秒。

 在超时时间内一直没有访问请求，负载均衡会暂时中断当前连接，直到一下次请求来临时重新建立新的连接。

 |
|RequestTimeout|Integer|否|223|指定请求超时时间，取值范围为1-180秒，默认值为60秒。

 在超时时间内后端服务器一直没有响应，负载均衡将放弃等待，给客户端返回HTTP 504错误码。

 |
|Scheduler|String|否|wrr|调度算法。取值：

 -   **wrr**（默认值）：权重值越高的后端服务器，被轮询到的次数（概率）也越高。
-   **wlc**：除了根据每台后端服务器设定的权重值来进行轮询，同时还考虑后端服务器的实际负载（即连接数）。当权重值相同时，当前连接数越小的后端服务器被轮询到的次数（概率）也越高。
-   **rr**：按照访问顺序依次将外部请求依序分发到后端服务器。

 |
|ServerCertificateId|String|否|idkp-123-cn-test-01|服务器证书的ID。

 |
|StickySession|String|否|on|是否开启会话保持。

 取值：**on|off**。

 |
|StickySessionType|String|否|on|cookie的处理方式。取值：

 -   **insert**：植入Cookie。

客户端第一次访问时，负载均衡会在返回请求中植入Cookie（即在HTTP/HTTPS响应报文中插入SERVERID），下次客户端携带此Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器上。

-   **server**：重写Cookie。

负载均衡发现用户自定义了Cookie，将会对原来的Cookie进行重写，下次客户端携带新的Cookie访问，负载均衡服务会将请求定向转发给之前记录到的后端服务器。


 **说明：** 当**StickySession**的值为**on**时，必须指定该参数。

 |
|TLSCipherPolicy|String|否|tls\_cipher\_policy\_1\_2|只有性能保障型实例才可以指定TLSCipherPolicy参数，每种policy定义了一种安全策略，安全策略包含HTTPS可选的TLS协议版本和配套的加密算法套件。

 目前支持以下四种安全策略，请根据实际情况选择对应的policy。

 -   **tls\_cipher\_policy\_1\_0**：
    -   支持TLS版本： TLSv1.0、TLSv1.1和TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   **tls\_cipher\_policy\_1\_1**：
    -   支持TLS版本： TLSv1.1和TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   **tls\_cipher\_policy\_1\_2** 
    -   支持TLS版本：TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、AES128-GCM-SHA256、AES256-GCM-SHA384、AES128-SHA256、AES256-SHA256、ECDHE-RSA-AES128-SHA、ECDHE-RSA-AES256-SHA、AES128-SHA、AES256-SHA和DES-CBC3-SHA。
-   **tls\_cipher\_policy\_1\_2\_strict** 
    -   支持TLS版本：TLSv1.2。
    -   支持加密算法套件：ECDHE-RSA-AES128-GCM-SHA256、ECDHE-RSA-AES256-GCM-SHA384、ECDHE-RSA-AES128-SHA256、ECDHE-RSA-AES256-SHA384、ECDHE-RSA-AES128-SHA和ECDHE-RSA-AES256-SHA。

 |
|UnhealthyThreshold|Integer|否|4|健康检查连续失败多少次后，将后端服务器的健康检查状态由**success**判定为**fail**。

 取值：**2-10**。

 |
|VServerGroup|String|否|on|是否使用服务器组。

 取值：**on|off**。

 |
|VServerGroupId|String|否|rsp-cige6j5e7p|虚拟服务器组ID。

 |
|XForwardedFor|String|否|on|是否开启通过X-Forwarded-For头字段获取来访者真实IP。

 取值：**on|off**。

 |
|XForwardedFor\_SLBID|String|否|on|是否通过`SLB-ID`头字段获取负载均衡实例ID。

 取值：**on|off**（默认值）。

 |
|XForwardedFor\_SLBIP|String|否|on|是否通过`SLB-IP`头字段获取客户端请求的真实IP。

 取值：**on|off**（默认值）。

 |
|XForwardedFor\_proto|String|否|on|是否通过`X-Forwarded-Proto`头字段获取负载均衡实例的监听协议。

 取值：**on | off**（默认值）。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetLoadBalancerHTTPSListenerAttribute
&ListenerPort=80
&LoadBalancerId=139a00604ad-cn-east-hangzhou-01
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetLoadBalancerHTTPSListenerAttributeResponse>
  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</SetLoadBalancerHTTPSListenerAttributeResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

