# View monitoring data in the console

You can use Cloud Monitor to view the monitoring data of a Server Load Balancer \(SLB\) instance, such as the number of connections, number of packets, and traffic.

1.  Log on to the [SLB console](https://slb.console.aliyun.com).

2.  On the Instances page, select the region in which the SLB instance that you want to view resides.

3.  Find the SLB instance and click the monitoring icon ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1113359951/p7338.png).

4.  Select the monitoring metrics that you want to view.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1113359951/p7337.png)

    The following table lists the monitoring metrics of SLB instances.

    |Monitoring metric|Description|
    |:----------------|:----------|
    |**Traffic**|    -   Inbound Traffic: the amount of traffic consumed to access an SLB instance from the Internet.
    -   Outbound Traffic: the amount of traffic consumed by an SLB instance to access the Internet. |
    |**Packets**|    -   Inbound Packets: the number of request packets received per second.
    -   Outbound Packets: the number of response packets sent per second. |
    |**Concurrent Connections**|    -   Active Connections Count: the number of TCP connections that are in the ESTABLISHED state. If persistent connections are used, a connection may transfer multiple file requests simultaneously.
    -   Inactive Connections Count: the number of TCP connections that are not in the ESTABLISHED state. You can run the `netstat -an` command to view the connections for both Windows and Linux instances.
    -   Maximum Concurrent Connections Count: the total number of TCP connections. |
    |**New Connections**|The average number of new TCP connections established between clients and SLB instances in a statistical period.|
    |**Dropped Traffic**|    -   Dropped Inbound Traffic: the amount of inbound traffic dropped per second.
    -   Dropped Outbound Traffic: the amount of outbound traffic dropped per second. |
    |**Dropped Packets**|    -   Dropped Inbound Packets: the number of inbound packets dropped per second.
    -   Dropped Outbound Packets: the number of outbound packets dropped per second. |
    |**Dropped Connections**|The number of connections dropped per second.|
    |Metrics specific to Layer 7 \(HTTP or HTTPS\) listeners|
    |**Layer-7 QPS**|The number of HTTP or HTTPS requests that can be processed per second.|
    |**Response Time \(Listener\)**|The average response time of an SLB instance.|
    |**HTTP Status Code 2XX/3XX/4XX/5XX/Other HTTP Status Codes \(Listener\)**|The number of HTTP response codes returned by listeners.|
    |**HTTP Status Code 4XX/5XX \(Server\)**|The number of HTTP response codes returned by backend servers.|
    |**Response Time \(Server\)**|The average response time of backend servers.|


