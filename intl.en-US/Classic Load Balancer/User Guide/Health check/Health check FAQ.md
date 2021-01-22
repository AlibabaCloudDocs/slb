# Health check FAQ

The following questions about health checks are frequently asked:

-   [How does the health check feature of Server Load Balancer \(SLB\) work?](#section_m43_1qx_wdb)
-   [What are the recommended configurations for health checks in SLB?](#section_jhf_jqx_wdb)
-   [Can I disable the health check feature?](#section_tn3_sqx_wdb)
-   [What is the recommended health check method for TCP listeners?](#section_un3_sqx_wdb)
-   [How are health checks impacted if the weight of an ECS instance is zero?](#section_wn3_sqx_wdb)
-   [What health check method is used for HTTP listeners on backend ECS instances?](#section_xn3_sqx_wdb)
-   [What is the CIDR block that HTTP listeners use to Health Check to backend ECS instances?](#section_yn3_sqx_wdb)
-   [Why do the console and web logs display a different health check frequency?](#section_zn3_sqx_wdb)
-   [Do health checks consume system resources?](#section_b43_sqx_wdb)
-   [How do I handle a health check failure caused by a faulty backend database?](#section_d43_sqx_wdb)
-   [Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful?](#section_11)
-   [Why is the health check result returned as unhealthy even though the service is running normally?](#section_ldb_5sx_wdb)

## How does the health check feature of Server Load Balancer \(SLB\) work?

SLB performs health checks to verify the availability of backend ECS instances. If the health check feature is enabled and the check result shows that a backend ECS instance is unhealthy, the SLB instance does not forward new requests to the ECS instance till the instance becomes healthy.

SLB uses the CIDR block of 100.64.0.0/10 for health checks. Make sure that this CIDR block is permitted to access the backend ECS instances. You do not need to configure a security group rule to allow access from this CIDR block. However, if you have configured security rules such as iptables, you must allow access from this CIDR block. 100.64.0.0/10 is reserved by Alibaba Cloud. Other users cannot use any IP addresses within this CIDR block. Therefore, no relevant security risks exist.

For more information, see [Health check overview](/intl.en-US/Classic Load Balancer/User Guide/Health check/Health check overview.md).

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2726209951/p3226.png)

## What are the recommended configurations for health checks in SLB?

To avoid impacts on system availability caused by frequent switching after failed health checks, the health check status switches only when health checks successively succeed or fail for a specified number of times within a certain time window. For more information, see [Configure health check](/intl.en-US/Classic Load Balancer/User Guide/Health check/Configure health checks.md).

The following table describes the recommended health check configurations for TCP, HTTP, and HTTPS listeners.

|Parameter|Recommended value|
|:--------|:----------------|
|**Response Timeout**|5 seconds|
|**Health Check Interval**|2 seconds|
|**Unhealthy Threshold**|3|

The following table describes the recommended health check configurations for UDP listeners.

|Parameter|Recommended value|
|:--------|:----------------|
|**Response Timeout**|10 seconds|
|**Health Check Interval**|5 seconds|
|**Unhealthy Threshold**|3|
|**Healthy Threshold**|3|

**Note:** The recommended configurations help restore the service in a timely manner if the health check of a backend server fails. If you have higher requirements, you can specify a lower response timeout value. However, you must make sure the response time in the normal status is less than the timeout value that you have specified.

## Can I disable the health check feature?

You can disable health checks only for HTTP and HTTPS listeners. Health check for TCP and UDP listeners cannot be disabled. For more information, see [Disable the health check feature]().

**Note:** If you disable health checks, requests may be distributed to unhealthy ECS instances and cause impacts on your business. We recommend that you enable health checks.

## What is the recommended health check method for TCP listeners?

For TCP listeners, both the HTTP and TCP health check methods are supported:

-   A TCP health check sends SYN handshake packets to an instance to check whether the status of the instance is healthy.
-   An HTTP health check simulates a process that uses a web browser to access resources by sending HEAD or GET requests to an instance and check whether the instance is healthy.

A TCP health check consumes less server resources. If the traffic load on backend servers is high, select TCP health checks. Otherwise, select HTTP health checks.

## How are health checks impacted if the weight of an ECS instance is zero?

If you set the weight of an ECS instance to zero, SLB no longer forwards traffic to this ECS instance, and the ECS instance is determined as healthy in a health check.

After you set the weight of an ECS instance to zero, the ECS instance is removed from SLB. The weight is set to zero only when you restart or manage an ECS instance.

## What health check method is used for HTTP listeners on backend ECS instances?

The HEAD method.

If you do not use the HEAD method for backend ECS instances, the backend ECS instances fail the health checks. We recommend that you access your own IP address on an ECS instance by using the HEAD method for testing. Run the following command on an ECS instance to access your IP address:

```
curl -v -0 -I -H "Host:" -X HEAD http://IP:port
```

## What is the CIDR block that HTTP listeners use to Health Check to backend ECS instances?

The CIDR block used by SLB health checks is 100.64.0.0/10 \(100.64.0.0/10 is reserved by Alibaba Cloud. It is not used by any user and therefore causes no security risks\). If backend ECS instances enable access control such as iptables, you must allow the access of 100.64.0.0/10 \(100.64.0.0/10 is reserved by Alibaba Cloud. It is not used by any user and therefore causes no security risks\) on the internal network interface controller \(NIC\).

## Why do the console and web logs display a different health check frequency?

Health checks are performed in clusters to avoid single points of failure. Proxies of SLB are deployed on multiple nodes. Therefore, the health check frequency recorded in web logs is different from the frequency configured in the console.

## Do health checks consume system resources?

HTTP health checks consume few resources of the backend ECS instances.

## How do I handle a health check failure caused by a faulty backend database?

Problem description:

Two web sites are configured on an ECS instance. The website www.test.com is a static website, and the website app.test.com is a dynamic website. Both websites are configured with SLB services. A 502 error occurs due to a backend database fault when www.test.com is accessed.

Cause:

The domain name app.test.com is set for health checks. ApsaraDB RDS or self-built database failure causes an access error to app.test.com and the health check fails.

Solution:

Set the domain name that is used for health checks to www.test.com.

## Why is a network connection exception recorded in the backend service logs, but the TCP health check is displayed as successful?

Problem description:

After a backend TCP port is configured in an SLB listener, the backend service logs frequently displays a network connection exception. The requests are sent from the SLB instance and the SLB instance also sends RST packets to the backend server at the same time.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2726209951/p3231.jpg)

Cause:

The problem is related to the health check mechanism.

TCP does not interrupt the upper-level services and is used to reduce the cost of health checks and the impacts on backend services. TCP health checks perform only a simple three-way handshake and then directly send RST packets to terminate the TCP connection. The following section describes the data exchange process:

1.  The SLB server sends an SYN request packet to the backend SLB port.
2.  The backend servers reply with an SYN-ACK package if the backend port is normal.
3.  After the SLB instance receives the response from the backend port, the SLB instance determines that the listener and the backend servers are healthy.
4.  The SLB instance sends a RST packet to the backend port to terminate the connection. A health check is complete.

After the health check succeeds, the SLB instance directly sends RST packets to terminate the connection. No data is sent afterwards. As a result, upper-level services such as the Java connection pool determine that the connection is abnormal and errors such as `Connection reset by peer` occur.

Solution:

-   Change the protocol from TCP to HTTP.
-   Filter the logs for requests from the CIDR block of the SLB server and ignore related error messages.

## Why is the health check result returned as unhealthy even though the service is running normally?

Problem description:

The HTTP health check always fails, but the status code is normal. The `curl-I` command obtains the following status code:

```
echo -e 'HEAD /test.html HTTP/1.0\r\n\r\n' | nc -t 192.168.0.1 80
```

Cause:

If the returned status code is different from the healthy status code configured in the console, the backend ECS instances are declared as unhealthy. For example, assume that the configured healthy status code is http\_2xx, the health check fails if the returned status code is not http\_2xx.

No error occurred when a curl test is performed on the Tengine or Nginx cluster, but a 404 error occurred in the test.html test file because the default site is used in the echo test. The following figure shows the error details:

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/2726209951/p3234.jpg)

Solution:

-   Modify the main configuration file and comment out the default site.
-   Add the domain name that is used for health checks in the health check configurations.

