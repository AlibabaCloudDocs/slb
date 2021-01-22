# Monitoring and alerting metrics

This topic lists major metrics for Server Load Balancer \(SLB\) Layer 4 and Layer 7 protocols and provides corresponding descriptions. You can set the thresholds of metrics, and create alert rules to trigger alerts.

## Precautions

-   Call the Cloud Monitor API to query monitoring data from the last 31 days.
-   Set Project to acs\_slb\_dashboard, and set the data sampling period to 60 seconds. The Period parameter can be set only to a multiple of 60.
-   Set the Dimensions parameter to a JSON string. Example: `[{"instanceId":"lb-bp1r92vzpemy099f******"}]`.

    In Dimensions, instanceId specifies the ID of the SLB instance, port specifies the port number of the SLB instance, and vip specifies the service address of the SLB instance.


## Layer 4 protocol metrics

|Metric|Description|Unit|Dimension|Statistics|
|:-----|:----------|:---|:--------|:---------|
|HeathyServerCount|The number of healthy ECS instances.|Count|instanceId|Average, Minimum, and Maximum|
|UnhealthyServerCount|The number of unhealthy ECS instances.|Count|instanceId|Average, Minimum, and Maximum|
|PacketTX|The number of outbound packets sent per second on a port.|Count/Second|instanceId, port, and vip|Average, Minimum, and Maximum|
|PacketRX|The number of inbound packets received per second on a port.|Count/Second|instanceId, port, and vip|Average, Minimum, and Maximum|
|TrafficRXNew|The amount of data received per second on a port.|bit/s|instanceId, port, and vip|Average, Minimum, and Maximum|
|TrafficTXNew|The amount of data sent per second on a port.|bit/s|instanceId, port, and vip|Average, Minimum, and Maximum|
|ActiveConnection|The number of active connections to an SLB instance on a port, which indicates the number of connections that clients set up to access the SLB instance. It indicates the number of TCP connections that are in the ESTABLISHED state. If persistent connections are used, a connection can transfer multiple file requests simultaneously.

|Count|instanceId, port, and vip|Average, Minimum, and Maximum|
|InactiveConnection|The number of inactive connections to an SLB instance on a port, which indicates the number of idle connections to the SLB instance. It indicates the number of TCP connections that are not in the ESTABLISHED state. You can run the `netstat -an` command to view the connections for both Windows and Linux instances.

|Count|instanceId, port, and vip|Average, Minimum, and Maximum|
|NewConnection|The number of new TCP connections established between clients and an SLB instance within a statistical period.|Count|instanceId, port, and vip|Average, Minimum, and Maximum|
|MaxConnection|The number of established TCP connections.|Count|instanceId, port, and vip|Average, Minimum, and Maximum|
|DropConnection|The number of connections dropped per second.|Count/Second|instanceId, port, and vip|Average, Minimum, and Maximum|
|DropPacketRX|The number of inbound packets dropped per second.|Count/Second|instanceId, port, and vip|Average, Minimum, and Maximum|
|DropPacketTX|The number of outbound packets dropped per second.|Count/Second|instanceId, port, and vip|Average, Minimum, and Maximum|
|DropTrafficRX|The amount of inbound traffic dropped per second.|bit/s|instanceId, port, and vip|Average, Minimum, and Maximum|
|DropTrafficTX|The amount of outbound traffic dropped per second.|bit/s|instanceId, port, and vip|Average, Minimum, and Maximum|
|InstanceActiveConnection|The number of active connections per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceDropConnection|The number of connections dropped per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceDropPacketRX|The number of inbound packets dropped per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceDropPacketTX|The number of outbound packets dropped per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceDropTrafficRX|The amount of inbound traffic dropped per second on an instance.|bit/s|instanceId|Average, Minimum, and Maximum|
|InstanceDropTrafficTX|The amount of outbound traffic dropped per second on an instance.|bit/s|instanceId|Average, Minimum, and Maximum|
|InstanceInactiveConnection|The number of idle connections per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceMaxConnection|The maximum number of concurrent connections per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceNewConnection|The number of new connections per second on an instance.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstancePacketRX|The number of request packets received by an SLB instance per second.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstancePacketTX|The number of packets sent by an SLB instance per second.|Count/Second|instanceId|Average, Minimum, and Maximum|
|InstanceTrafficRX|The traffic consumed to access an SLB instance from the Internet.|bit/s|instanceId|Average, Minimum, and Maximum|
|InstanceTrafficTX|The traffic consumed by an SLB instance to access the Internet.|bit/s|instanceId|Average, Minimum, and Maximum|
|InstanceMaxConnectionUtilization|The maximum utilization of connections.|%|instanceId|Average, Minimum, and Maximum|
|InstanceNewConnectionUtilization|The utilization of new connections.|%|instanceId|Average, Minimum, and Maximum|

## Layer 7 protocol metrics

|Metric|Description|Unit|Dimensions|Statistics|
|:-----|:----------|:---|:---------|:---------|
|Qps|The queries per second \(QPS\) through a port, which indicates the number of HTTP and HTTPS requests processed per second.|Count/Second|instanceId, port, and vip|Average|
|Rt|The average latency of requests on a port, which indicates the average response time of an SLB instance.|ms|instanceId, port, and vip|Average|
|StatusCode2xx|The number of 2xx status codes returned by an SLB instance to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|StatusCode3xx|The number of 3xx status codes returned by an SLB instance to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|StatusCode4xx|The number of 4xx status codes returned by an SLB instance to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|StatusCode5xx|The number of 5xx status codes returned by an SLB instance to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|StatusCodeOther|The number of other status codes returned by an SLB instance to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|UpstreamCode4xx|The number of 4xx status codes returned by backend servers to an SLB instance through a port.|Count/Second|instanceId, port, and vip|Average|
|UpstreamCode5xx|The number of 5xx status codes returned by backend servers to the client through a port.|Count/Second|instanceId, port, and vip|Average|
|UpstreamRt|The average latency of requests sent by backend servers to the proxy through a port.|ms|instanceId, port, and vip|Average|
|InstanceQps|The queries per second \(QPS\) on an instance, which indicates the number of HTTP and HTTPS requests processed per second.|Count/Second|instanceId|Average|
|InstanceRt|The average response latency of an instance.|ms|instanceId|Average|
|InstanceStatusCode2xx|The number of 2xx status codes returned by an SLB instance to the client.|Count/Second|instanceId|Average|
|InstanceStatusCode3xx|The number of 3xx status codes returned by an SLB instance to the client.|Count/Second|instanceId|Average|
|InstanceStatusCode4xx|The number of 4xx status codes returned by an SLB instance to the client.|Count/Second|instanceId|Average|
|InstanceStatusCode5xx|The number of 5xx status codes returned by an SLB instance to the client.|Count/Second|instanceId|Average|
|InstanceStatusCodeOther|The number of other status codes returned by an SLB instance to the client.|Count/Second|instanceId|Average|
|InstanceUpstreamCode4xx|The number of 4xx status codes returned by backend servers to an SLB instance.|Count/Second|instanceId|Average|
|InstanceUpstreamCode5xx|The number of 5xx status codes returned by backend servers to an SLB instance.|Count/Second|instanceId|Average|
|InstanceUpstreamRt|The average latency of requests sent from backend servers of an SLB instance to a proxy.|ms|instanceId|Average|
|InstanceQpsUtilization|The QPS utilization.|%|instanceId|Average, Minimum, and Maximum|

