# DescribeLoadBalancerHTTPListenerAttribute {#slb_api_DescribeLoadBalancerHTTPListenerAttribute .reference}

查询HTTP监听配置。

## 请求参数 {#section_ow5_23c_ndb .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：DescribeLoadBalancerHTTPListenerAttribute

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口。取值：1-65535

|

## 返回参数 {#section_qw5_23c_ndb .section}

|名称|类型|描述|
|:-|:-|:-|
|RequestId|String|请求ID。|
|ListenerPort|Integer|负载均衡实例前端使用的端口。|
|BackendServerPort|Integer|负载均衡实例后端使用的端口。|
|Bandwidth|Integer|监听的带宽峰值。|
|Status|String|当前监听的状态。取值：starting | running | configuring | stopping | stopped

|
|XForwardedFor|String|是否开启通过X-Forwarded-For头字段获取访者真实IP。|
|XForwardedFor\_SLBIP|String|是否通过SLB-IP头字段获取客户端请求的真实IP。|
|XForwardedFor\_SLBID|String|是否通过SLB-ID头字段获取负载均衡实例ID。|
|XForwardedFor\_proto|String|是否通过X-Forwarded-Proto头字段获取负载均衡实例的监听协议。|
|Scheduler|String|调度算法。|
|StickySession|String|是否开启会话保持。|
|StickySessionType|String|cookie的处理方式。|
|CookieTimeout|Integer|Cookie超时时间。|
|Cookie|String|服务器上配置的cookie。|
|AclStatus|String|是否开启访问控制功能。取值：on | off（默认值）

|
|AclType|String|访问控制类型：-   white： 仅转发来自所选访问控制策略组中设置的IP地址或地址段的请求，白名单适用于应用只允许特定IP访问的场景。

设置白名单存在一定业务风险。一旦设置白名单，就只有白名单中的IP可以访问负载均衡监听。如果开启了白名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。

-   black： 来自所选访问控制策略组中设置的IP地址或地址段的所有请求都不会转发，黑名单适用于应用只限制某些特定IP访问的场景。

如果开启了黑名单访问，但访问策略组中没有添加任何IP，则负载均衡监听会转发全部请求。


当AclStatus参数的值为on时，该参数必选。

|
|AclId|String|监听绑定的访问策略组ID。当AclStatus参数的值为on时，该参数必选。

|
|HealthCheck|String|是否开启健康检查。|
|HealthCheckDomain|String|用于健康检查的域名。|
|HealthCheckURI|String|用于健康检查的URI。|
|HealthyThreshold|Integer|健康检查阈值。|
|UnhealthyThreshold|Integer|不健康检查阈值。|
|HealthCheckTimeout|Integer|每次健康检查响应的最大超时间，单位为秒。|
|HealthCheckInterval|Integer|健康检查的时间间隔，单位为秒。|
|HealthCheckHttpCode|String|健康检查正常的HTTP状态码。|
|HealthCheckConnectPort|Integer|健康检查的端口。|
|Gzip|String|是否开启Gzip压缩。|

## 示例 {#section_sw5_23c_ndb .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancerHTTPListenerAttribute
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <DescribeLoadBalancerHTTPListenerAttributeResponse>  
        <RequestId>8D8A6319-F05A-4577-B50D-388B4B30E103</RequestId>
        <HealthCheckHttpCode>http_2xx,http_3xx</HealthCheckHttpCode>
        <CookieTimeout>1000</CookieTimeout>
        <HealthCheckTimeout>5</HealthCheckTimeout>
        <XForwardedFor_SLBID>off</XForwardedFor_SLBID>
        <Gzip>on</Gzip>
        <Scheduler>wrr</Scheduler>
        <HealthyThreshold>3</HealthyThreshold>
        <StickySession>on</StickySession>
        <UnhealthyThreshold>3</UnhealthyThreshold>
        <XForwardedFor_SLBIP>off</XForwardedFor_SLBIP>
        <XForwardedFor_proto>off</XForwardedFor_proto>
        <Bandwidth>-1</Bandwidth>
        <HealthCheckURI>/</HealthCheckURI>
        <VServerGroupId>rsp-bp1kfa2u3y5yw</VServerGroupId>
        <HealthCheck>on</HealthCheck>
        <ListenerPort>8080</ListenerPort>
        <Status>running</Status> 
        <XForwardedFor>on</XForwardedFor>
        <HealthCheckInterval>2</HealthCheckInterval>
        <StickySessionType>insert</StickySessionType>
    </DescribeLoadBalancerHTTPListenerAttributeResponse>
    ```

-   JSON格式

    ```
    {
       "RequestId":"8D8A6319-F05A-4577-B50D-388B4B30E103",
       "HealthCheckHttpCode":"http_2xx,http_3xx",
       "CookieTimeout":1000,
       "HealthCheckTimeout":5,
       "XForwardedFor_SLBID":"off",
       "Gzip":"on",
       "Scheduler":"wrr",
       "HealthyThreshold":3,
       "StickySession":"on",
       "UnhealthyThreshold":3,
       "XForwardedFor_SLBIP":"off",
       "XForwardedFor_proto":"off",
       "Bandwidth":-1,
       "HealthCheckURI":"/",
       "VServerGroupId":"rsp-bp1kfa2u3y5yw",
       "HealthCheck":"on",
       "ListenerPort":8080,
       "Status":"running",
       "XForwardedFor":"on",
       "HealthCheckInterval":2,
       "StickySessionType":"insert"
    }
    ```


