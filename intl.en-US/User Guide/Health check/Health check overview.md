# Health check overview {#concept_fph_rzt_vdb .concept}

Server Load Balancer checks the service availability of the backend servers \(ECS instances\) by performing health checks. Health check improves the overall availability of the front-end service, and avoids impact on the entire service caused by exceptions of the backend ECS instances.

After enabling the health check function, SLB stops distributing requests to the instance that is discovered as unhealthy and restarts forwarding requests to the instance only when it is declared healthy.

If your business is highly sensitive to traffic load, frequent health checks may impact normal service. You can reduce this impact by reducing the frequency of health checks, increasing the health check interval, or changing the HTTP health check to TCP health check. To guarantee the service availability, we do not recommend disabling all health checks.

## Health check process {#section_ezz_ld5_vdb .section}

Server Load Balancer is deployed in clusters. Data forwarding and health checks are handled at the same time by the node servers in the LVS cluster and Tengine cluster.

The node servers in the cluster independently perform health checks in parallel, according to the health check configuration. If a node server discovers an ECS instance is unhealthy, the node server will stop distributing requests to the ECS instance. This operation is synchronized through all node servers.

The IP address range used to perform the health check is 100.64.0.0/10. The backend servers cannot block this CIDR block. You do not need to additionally configure a security group rule to allow access from this CIDR block. However, if you have configured security rules such as iptables, allow access from this CIDR block \(100.64.0.0/10 is reserved by Alibaba Cloud, and other users cannot use any IP address in this CIDR block, so there is no security risk\).

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702542_en-US.png)

## Health check of HTTP/HTTPS listeners {#section_e1x_125_vdb .section}

For Layer-7 \(HTTP or HTTPS\) listeners, SLB detects the status of backend servers by sending HTTP HEAD requests, as shown in the following figure.

For HTTPS listeners, certificates are managed in SLB. Data exchange \(including health check data and service interaction data\) between SLB and backend ECS instances is not transmitted over HTTPS to improve the system performance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702543_en-US.png)

The health check process of a Layer-7 listener is as follows:

1.  The Tengine node server sends an HTTP HEAD request to the intranet IP +Health Check Port+Health Check Path of the ECS instance according to the health check settings.
2.  After receiving the request, the backend server returns an HTTP status code based on the running status.
3.  If the Tengine node server does not receive the response from the backend server within the Response Timeout period, the ECS instance is declared unhealthy.
4.  If the Tengine node server receives the response from the backend ECS instance within the Response Timeout period, it compares the returned status code with the status code specified in the listener configuration. If the status code is the same, the backend server is declared healthy. Otherwise, the backend server is declared unhealthy.

## Health check of TCP listeners {#section_oc3_ngw_vdb .section}

For TCP listeners, SLB detects the status of backend servers by sending TCP detections, as the following figure shows.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702549_en-US.png)

The health check process of a TCP listener is as follows:

1.  The LVS node server sends a TCP SYN packet to the intranet IP + Health Check Port of the backend ECS instance.
2.  After receiving the request, the backend server returns a TCP SYN and ACK packet if the corresponding port is listening normally.
3.  If the LVS node server does not receive the required data packet from the backend server within the Response Timeout period, the ECS instance is declared unhealthy. Then, the LVS node server sends an RST data packet to the backend server to terminate the TCP connection.
4.  If the LVS node server receives the data packet from the backend ECS instance within the Response Timeout period, the ECS instance is declared healthy. Then, the LVS node server sends an RST data packet to the backend server to terminate the TCP connection.

**Note:** In general, TCP three-way handshakes are conducted to establish a TCP connection. After the LVS node server receives an SYN + ACK data packet from the backend ECS instance, the LVS node server sends an ACK data packet, and then immediately sends an RST data packet to terminate the TCP connection.

This process may make backend server think an error \(such as an abnormal exit\) occurred in the TCP connection and then throw a corresponding error message, such as `Connection reset by peer`.

Resolution:

-   Use the HTTP health check.
-   If obtaining real IP is enabled, ignore the connection errors caused by access of the SLB IP address.

## Health check of UDP listeners {#section_h12_pgw_vdb .section}

For UDP listeners, Server Load Balancer detects the status of the backend servers through UDP packet detection, as shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702566_en-US.png)

The health check process of a UDP listener is as follows:

1.  The LVS node server sends a UDP packet to the intranet IP + Health Check Port of the ECS instance according to health check configurations.
2.  If the corresponding port of the ECS instance is not listening normally, the system will return an ICMP error message, such as `port XX unreachable`. Otherwise, no message is sent.
3.  If the LVS node server receives the ICMP error message within the Response Timeout period, the ECS instance is declared unhealthy.
4.  If the LVS node server does not receive any messages within the Response Timeout period, the ECS instance is declared healthy.

**Note:** For UDP health checks, the real status of the backend server and the health check result may not be the same in the following situation:

If the ECS instance uses a Linux operating system, the speed of sending ICMP messages in high-concurrency scenarios is limited due to the anti-ICMP attack protection in Linux. In this case, even if an exception occurs in the ECS instance, SLB may declare the backend server healthy because the error message `port XX unreachable` is not returned. As a result, the actual service status is different from the health check result.

Resolution:

Set a pair of custom request and response for the UDP health check. If the custom response is returned, the ECS instance is considered healthy. Otherwise, the ECS instance is considered unhealthy. To achieve this, you must add corresponding configurations for the client.

## Health check time window {#section_ojc_5f5_vdb .section}

The health check function has effectively improved the availability of your business services. However, to reduce impact on the system availability caused by frequent system switches because of health check failure, SLB declares an ECS instance healthy or unhealthy only after successive successes or failures within a specified timeframe. The health check time window is determined by the following three factors:

-   Health check interval \(How often the health check is performed.\)
-   Response timeout \(The amount of time to wait for the response.\)
-   Health check threshold \(The number of consecutive successful or failed health checks.\)

The health check time window is calculated as follows:

-   Health check failure time window = Response Timeout x Unhealthy Threshold + Health Check Interval X \(Unhealthy Threshold\) -1\)

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702568_en-US.png)

-   Health check success time window = \(Response Time of a Successful Health Check X Healthy Threshold\) + Health Check Interval X \(Healthy Threshold-1\)

    **Note:** The success response time of a health check is the duration from the time when the health check request is sent to the time when the response is received. For TCP health check, the time is very short and almost negligible because TCP health check only detects whether the port is alive. For HTTP health check, the time depends on the performance and load of the application server and is generally within seconds.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702570_en-US.png)


The health check result has the following impact on the requests forwarding:

-   If the health check of the target ECS instance fails, new requests will not be distributed to the ECS instance. Therefore, there is no impact on the client access.
-   If the health check of the target ECS instance succeeds, new requests will be distributed to it. The client access is normal.
-   If a request arrives during a health check failure window, the request is still sent to the ECS instance because the ECS instance is being checked and has not been declared unhealthy. As a result, the client access fails.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4137/15580089702571_en-US.png)

