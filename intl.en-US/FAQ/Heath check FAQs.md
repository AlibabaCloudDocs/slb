# Heath check FAQs {#concept_zx3_fh5_vdb .concept}

-   [How does the health check function of Server Load Balancer \(SLB\) work?](#section_m43_1qx_wdb)
-   [What are the recommended configurations for health checks in SLB?](#section_jhf_jqx_wdb)
-   [Can I disable the health checks?](#section_tn3_sqx_wdb)
-   [What is the recommended health check method for TCP listeners?](#section_un3_sqx_wdb)
-   [Is there any impact to health checks if the weight of an ECS instance is zero?](#section_wn3_sqx_wdb)
-   [What health check method is used for HTTP listeners on backend ECS instances?](#section_xn3_sqx_wdb)
-   [7. What are the ranges of IP address that HTTP listeners use to perform health checks on backend ECS instances?](#section_yn3_sqx_wdb)
-   [Why is the health check frequency that is displayed on the console different from that recorded in the web logs?](#section_zn3_sqx_wdb)
-   [Do health checks use system resources?](#section_b43_sqx_wdb)
-   [How can I handle a health check failure caused by a faulty backend database?](#section_d43_sqx_wdb)
-   [Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful?](reseller.en-US/FAQ/Heath check FAQs.md#section_11)
-   [Why is the health check result returned as abnormal when the service is running normally?](#section_ldb_5sx_wdb)

## How does the health check function of Server Load Balancer \(SLB\) work? {#section_m43_1qx_wdb .section}

SLB checks the service availability of backend servers \(ECS instances\) by performing health checks on backend servers. When SLB determines that an instance is unhealthy, it stops distributing requests to that instance. Distributions to that instance will resume when it becomes healthy again.

The IP address range used to perform the health check is 100.64.0.0/10. The backend servers cannot block this CIDR block. You do not need to additionally configure a security group rule to allow access from this CIDR block. However, if you have configured security rules such as iptables, allow access from this CIDR block \(100.64.0.0/10 is reserved by Alibaba Cloud, and other users cannot use any IP address in this CIDR block, so there is no security risk\).

For more information, see [Health check overview](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Health check overview.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15561997593226_en-US.png)

## What are the recommended configurations for health checks in SLB? {#section_jhf_jqx_wdb .section}

However, to avoid the impact of switching caused by frequent health check failures on the system availability, status is switched \(health check succeeded or failed\) only when the health check continuously succeeds or fails for multiple times in the time window. For more information, see [Health check configurations](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Health check configurations.md#).

The following are recommended health check configurations for TCP/HTTP/HTTPS listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|5 seconds|
|**Health check Interval**|2 seconds|
|**Unhealthy threshold**|3 times|

The following are recommended health check configurations for UDP listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|10 seconds|
|**Health check Interval**|5 seconds|
|**Unhealthy threshold**|3 times|
|**Healthy threshold**|3 times|

**Note:** These configurations are conducive to restoring the service when the health check of a backend server fails. If you have higher requirements, you can specify a smaller response timeout value, but you need to make sure that the processing time in the normal status is less than the specified timeout value.

## Can I disable the health checks? {#section_tn3_sqx_wdb .section}

You can only disable health check for HTTP and HTTPS listeners. The health check of UDP and TCP listeners cannot be disabled. For more information, see [Close health check](../reseller.en-US/Archives/User Guide (Old Console)/Listener/Health check/Close health check.md#).

**Note:** When the health check function is disabled, requests may be distributed to unhealthy ECS instances, which can lead to service interruption. We do not recommend disabling health checks.

## What is the recommended health check method for TCP listeners? {#section_un3_sqx_wdb .section}

For TCP listeners, both TCP health checks and HTTP health checks are supported:

-   TCP health checks send SYN handshake packets to backend servers to check whether the ports of backend servers are normal.
-   HTTP health checks detect the health status of applications on backend servers by sending HEAD and GET requests to simulate visits from the browser of a user.

The TCP health check minimally impacts performance and consumes less resources on the backend ECS instances. Choose TCP health checks if the traffic load on the backend ECS instance is large, and choose HTTP health checks if not.

## Is there any impact to health checks if the weight of an ECS instance is zero? {#section_wn3_sqx_wdb .section}

In this situation, SLB will no longer forward traffic to this ECS instance and the health check will indicate abnormal for the Layer-4 listeners, while the health check is normal for Layer-7 listeners.

Setting the weight value to zero is equal to manually removing the ECS instance from Server Load Balancer. The weight is set to zero only when restarting, adjusting, or maintaining the ECS instance.

## What health check method is used for HTTP listeners on backend ECS instances? {#section_xn3_sqx_wdb .section}

HEAD method

If the backend ECS instances disable the HEAD method access, health checks on the backend ECS instances will fail. We recommend you access your own IP address using the HEAD method on the ECS instance for testing:

```
curl -v -0 -I -H "Host:" -X HEAD http://IP:port
```

## 7. What are the ranges of IP address that HTTP listeners use to perform health checks on backend ECS instances? {#section_yn3_sqx_wdb .section}

The IP address range used by the health check of SLB is 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \). If the backend ECS instance enables access control such as iptables, you need to allow the access of 100.64.0.0/10 on the intranet NIC.

## Why is the health check frequency that is displayed on the console different from that recorded in the web logs? {#section_zn3_sqx_wdb .section}

Health checks are performed in the cluster to avoid single points of failure. Therefore, the health check frequency recorded in the logs is different from the frequency configured in the console.

## Do health checks use system resources? {#section_b43_sqx_wdb .section}

HTTP health checks consume few resources of the backend ECS instances.

## How can I handle a health check failure caused by a faulty backend database? {#section_d43_sqx_wdb .section}

Symptoms:

Two web sites are configured on an ECS instance. The website www.test.com is a static website, and the website app.test.com is a dynamic website. A 502 error occurred when accessing www.test.com due to a backend database fault.

Cause:

Domain name app.test.com is configured for health check. RDS or self-built database failure causes the access error to app.test.com, so the health check fails.

Resolution:

Configure the domain name used for health checks to www.test.com.

## Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful? {#section_11 .section}

Symptoms:

After configuring the backend TCP port in a SLB listener, a network connection exception is frequently shown in the backend service logs. The requests are sent from the SLB instance and the SLB instance also sends RST packets to the backend server at the same time.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15561997603231_en-US.jpg)

Cause:

The problem is related to the health check mechanism.

TCP is transparent to the upper-Layer applications and is utilized to reduce the cost of health checks and the impact on backend service. TCP health checks only perform a simple three-way handshake and then directly send RST packets to terminate the TCP connection. The data exchange process is as follows:

1.  The SLB instance sends a SYN packet to the backend port.
2.  The backend server replies with a SYN-ACK if the backend port is in normal status.
3.  After successfully receiving the response from the backend port, the SLB instance considers that the port is in normal status and the status of the backend server is normal.
4.  The SLB instance sends a RST packet to the backend port to actively terminate the connection. For now, health check is completed.

After the health check succeeds, the SLB instance directly sends RST packets to terminate the connection and no data is sent afterwards. Therefore, upper-Layer services \(such as Java connection pool\) deem that the connection is abnormal and errors such as `Connection reset by peer` are displayed.

Resolution:

-   Use HTTP protocol instead.
-   In the service layer, filter the logs from the SLB IP address range and ignore related error messages.

## Why is the health check result returned as abnormal when the service is running normally? {#section_ldb_5sx_wdb .section}

Symptoms:

The HTTP health check always fails, but the status code obtained by performing the `curl -I` test is normal as follows:

```
echo -e ‘HEAD /test.html HTTP/1.0\r\n\r\n’ | nc -t 192.168.0.1 80
```

Cause:

If the returned status code is different from the normal status code configured on the console, the backend ECS instance is declared as unhealthy. For example, if the configured normal status code is http\_2xx, all other status codes returned not matching this status code will be considered as health check failure.

No error occurred when a curl test is performed on the Tengine/Nginx cluster, but a 404 error occurred in the test.html test file because the default site is used in the echo test.

Resolution:

-   Modify the main configuration file and annotate the default site.
-   Add the domain name used for health check in the health check configurations.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15561997603234_en-US.jpg)

