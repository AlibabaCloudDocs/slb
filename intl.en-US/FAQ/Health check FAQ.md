# Health check FAQ {#concept_zx3_fh5_vdb .concept}

The following are frequently asked questions about health checks:

-   [How does the health check function of Server Load Balancer \(SLB\) work?](#section_m43_1qx_wdb)
-   [What are the recommended configurations for health checks in SLB?](#section_jhf_jqx_wdb)
-   [Can I disable the health check function?](#section_tn3_sqx_wdb)
-   [What is the recommended health check method for TCP listeners?](#section_un3_sqx_wdb)
-   [Is there any impact to health checks if the weight of an ECS instance is zero?](#section_wn3_sqx_wdb)
-   [What health check method is used for HTTP listeners on backend ECS instances?](#section_xn3_sqx_wdb)
-   [What are the ranges of IP addresses that HTTP listeners use to perform health checks on backend ECS instances?](#section_yn3_sqx_wdb)
-   [Why is the health check frequency that is displayed on the console different from that recorded in the web logs?](#section_zn3_sqx_wdb)
-   [Do health checks use system resources?](#section_b43_sqx_wdb)
-   [How do I handle a health check failure caused by a faulty backend database?](#section_d43_sqx_wdb)
-   [Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful?](#section_11)
-   [Why is the health check result returned as abnormal when the service is running normally?](#section_ldb_5sx_wdb)

## How does the health check function of Server Load Balancer \(SLB\) work? {#section_m43_1qx_wdb .section}

SLB checks the service availability of backend servers \(ECS instances\) by performing health checks on backend servers. When SLB detects that an ECS instance is unhealthy, SLB stops distributing requests to the ECS instance until it becomes healthy again.

The IP address range used for health checks is 100.64.0.0/10. Make sure that backend ECS instances do not block this CIDR block. You do not need to configure a security group rule to allow access from this CIDR block. However, if you have configured security rules such as iptables, you need to allow access from this CIDR block. \(100.64.0.0/10 is reserved by Alibaba Cloud. Other users cannot use any IP address in this CIDR block and therefore there is no security risk.\)

For more information, see [Health check overview](../intl.en-US/Archives/User Guide (Old Console)/Listener/Health check/Health check overview.md#).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15679955643226_en-US.png)

## What are the recommended configurations for health checks in SLB? {#section_jhf_jqx_wdb .section}

To avoid the impact of backend server switching caused by frequent health check failures on system availability, health check failures or successes must reach a certain threshold before the health check status of a backend server is switched.

The following are recommended health check configurations for TCP, HTTP, and HTTPS listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|5 seconds|
|**Health check interval**|2 seconds|
|**Unhealthy threshold**|3 times|

The following are recommended health check configurations for UDP listeners.

|Configuration|Recommended value|
|:------------|:----------------|
|**Response timeout**|10 seconds|
|**Health check interval**|5 seconds|
|**Unhealthy threshold**|3 times|
|**Healthy threshold**|3 times|

**Note:** These configurations are conducive to restoring the service when the health check of a backend server fails. If you have higher requirements, you can specify a lower response timeout value. However, you must make sure the response time in the normal status is less than the timeout value that you have specified.

## Can I disable the health check function? {#section_tn3_sqx_wdb .section}

You can only disable health checks for HTTP and HTTPS listeners. Health checks for UDP and TCP listeners cannot be disabled.

**Note:** If the health check function is disabled, requests may be distributed to unhealthy ECS instances, which can lead to service interruptions. Therefore, we recommend that you enable health checks.

## What is the recommended health check method for TCP listeners? {#section_un3_sqx_wdb .section}

For TCP listeners, both the TCP health check and HTTP health check are supported:

-   TCP health checks send SYN handshake packets to backend servers to check whether the ports of backend servers are normal.
-   HTTP health checks detect the health status of applications on backend servers by sending HEAD and GET requests to simulate visits from the browser of a user.

The TCP health check minimally impacts the performance of backend servers and consumes less server resources. Select TCP health check if the traffic load on backend servers is high, and select HTTP health check if not.

## Is there any impact to health checks if the weight of an ECS instance is zero? {#section_wn3_sqx_wdb .section}

If you set the weight of an ECS instance to zero, SLB will no longer forward traffic to this ECS instance and health checks for Layer-4 listeners will indicate abnormal of backend ECS instances \(the health check is normal for Layer-7 listeners\).

Setting the weight value to zero is equal to manually removing the ECS instance from SLB. Generally, the weight is set to zero only when you restart, adjust, or maintain the ECS instance.

## What health check method is used for HTTP listeners on backend ECS instances? {#section_xn3_sqx_wdb .section}

HEAD request method.

If you disable the HEAD request method for backend ECS instances, health checks on the backend ECS instances will fail. We recommend that you access your own IP address on the ECS instance by using the HEAD method for testing:

``` {#codeblock_ebg_qer_fp9}
curl -v -0 -I -H "Host:" -X HEAD http://IP:port
```

## What are the ranges of IP addresses that HTTP listeners use to perform health checks on backend ECS instances? {#section_yn3_sqx_wdb .section}

The IP address range used by SLB health checks is 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \). If the backend ECS instance enables access control such as iptables, you need to allow the access of 100.64.0.0/10（100.64.0.0/10 is reserved by Alibaba Cloud, and will not be used by any user, there is no security risk \) on the intranet NIC.

## Why is the health check frequency that is displayed on the console different from that recorded in the web logs? {#section_zn3_sqx_wdb .section}

Health checks are performed in the cluster to avoid single points of failure. Therefore, the health check frequency recorded in the logs is different from the frequency configured in the console.

## Do health checks use system resources? {#section_b43_sqx_wdb .section}

HTTP health checks consume few resources of the backend ECS instances.

## How do I handle a health check failure caused by a faulty backend database? {#section_d43_sqx_wdb .section}

Symptoms:

Two web sites are configured on an ECS instance. The website www.test.com is a static website, and the website app.test.com is a dynamic website. A 502 error occurs due to a backend database fault when accessing www.test.com.

Cause:

The domain name app.test.com is configured for health checks. RDS or self-built database failure causes the access error to app.test.com. Therefore, the health check fails.

Solution:

Configure the domain name used for health checks to www.test.com.

## Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful? {#section_11 .section}

Symptoms:

After configuring the backend TCP port in an SLB listener, a network connection exception is frequently shown in the backend service logs. The requests are sent from the SLB instance and the SLB instance also sends RST packets to the backend server at the same time.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15679955643231_en-US.jpg)

Cause:

The problem is related to the health check mechanism.

TCP is transparent to the upper-Layer applications and is utilized to reduce the cost of health checks and the impact on backend service. TCP health checks only perform a simple three-way handshake and then directly send RST packets to terminate the TCP connection. The data exchange process is as follows:

1.  The SLB instance sends a SYN packet to the backend port.
2.  The backend server replies with a SYN-ACK if the backend port is normal.
3.  After successfully receiving the response from the backend port, the SLB instance considers that the port is in normal status and the status of the backend server is normal.
4.  The SLB instance sends a RST packet to the backend port to actively terminate the connection. For now, a health check is completed.

After the health check succeeds, the SLB instance directly sends RST packets to terminate the connection and no data is sent afterwards. Therefore, upper-Layer services \(such as Java connection pool\) deem that the connection is abnormal and errors such as `Connection reset by pee` occur.

Solution:

-   Use the HTTP protocol.
-   In terms of the service, filter the logs from the SLB IP address range and ignore related error messages.

## Why is the health check result returned as abnormal when the service is running normally? {#section_ldb_5sx_wdb .section}

Symptoms:

The HTTP health check always fails, but the status code obtained by performing the `curl -l` test is normal as follows:

``` {#codeblock_kgy_aas_0df}
echo -e ‘HEAD /test.html HTTP/1.0\r\n\r\n’ | nc -t 192.168.0.1 80
```

Cause:

If the returned status code is different from the normal status code configured in the console, the backend ECS instance is declared as unhealthy. For example, if the configured normal status code is http\_2xx, all other status codes returned not matching this status code will be considered as health check failure.

No error occurred when a curl test is performed on the Tengine/Nginx cluster, but a 404 error occurred in the test.html test file because the default site is used in the echo test.

Solution:

-   Modify the main configuration file and annotate the default site.
-   Add the domain name used for health checks in the health check configurations.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4288/15679955643234_en-US.jpg)

