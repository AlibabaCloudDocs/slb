# Architecture {#concept_ivd_np4_tdb .concept}

This topic describes the architecture of Server Load Balancer \(SLB\). SLB is deployed in clusters, which enables session synchronization and mitigates the creation of SPOFs in backend servers. As a traffic forwarding service, SLB forwards requests from clients to backend servers through SLB clusters, and backend servers return the responses to SLB through the intranet.

## Architecture {#section_scm_2f5_xfb .section}

Currently, Alibaba Cloud provides Layer-4 \(TCP protocol and UDP protocol\) and Layer-7 \(HTTP protocol and HTTPS protocol\) load balancing services.

-   Layer-4 SLB uses the open source software Linux Virtual Server \(LVS\) and Keepalived to achieve load balancing. It also customizes the software to adapt to cloud computing requirements.
-   Layer-7 SLB uses Tengine to achieve load balancing. Tengine is a web server project launched by another branch of the Alibaba Cloud Group \(Taobao\). Based on Nginx, Tengine provides a wide range of advanced features to support high-traffic websites.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1566871308938_en-US.png)


As shown in the following figure, Layer-4 SLB in each region actually runs in a cluster of multiple LVS machines. The cluster deployment model strengthens the availability, stability, and scalability of the load balancing services in abnormal circumstances.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1566871308939_en-US.png)

Additionally, each LVS machine in an LVS cluster uses multicast packets to synchronize sessions to other LVS machines. As shown in the following figure, after the client sends three packets to the server, session A is established on LVS1 and this session is synchronized to other LVS machines. In normal situations, the session request is sent to LVS1 as the solid line shows. If LVS1 fails or is being maintained, the session request is sent to other normally working machines, such as LVS2, as the dotted line shows. Therefore, SLB clusters support hot upgrades, and machine failures or system maintenance will not affect your business.

**Note:** If a connection is not established \(that is, a three-way handshake is not completed\), or a connection has been established but the session synchronization is not triggered during a hot upgrade, your service may be interrupted and the client needs to re-initiate the connection.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4092/1566871309941_en-US.png)

## Inbound network traffic flow {#section_gph_4k5_xfb .section}

SLB distributes incoming traffic according to the forwarding rules configured in the console or by using APIs. The following figure shows the inbound network traffic flow.

![](../DNslb1866251/../DNSLB11827830/images/2333_en-US.png "Inbound network traffic flow")

1.  For TCP, UDP, HTTP, and HTTPS protocols, the incoming traffic must be forwarded through the LVS cluster first.
2.  Large amounts of access requests are evenly distributed among all servers in the LVS cluster. Servers synchronize sessions to guarantee high availability.
    -   For Layer-4 listeners \(the frontend protocol is UDP or TCP\), the node servers in the LVS cluster distribute requests directly to backend ECS instances according to the configured forwarding rules.
    -   For Layer-7 listeners that use the frontend protocol HTTP, the node servers in the LVS cluster first distribute requests to the Tengine cluster. Then, the node servers in the Tengine cluster distribute the requests to backend ECS instances according to the configured forwarding rules.
    -   For Layer-7 listeners that use the frontend protocol HTTPS, the request distribution is similar to the HTTP protocol. However, before distributing requests to backend ECS instances, the system calls the Key Server to validate certificates and decrypt data packets.

## Outbound network traffic flow {#section_b1h_sk5_xfb .section}

SLB communicates with backend ECS instances through the intranet.

-   If backend ECS instances only need to handle the traffic distributed from SLB, no public bandwidth \(EIP, NAT Gateway, and public IP address\) is required, and you do not need to purchase any public bandwidth.

    **Note:** Previously created ECS instances are directly allocated with public IP addresses. You can view the public IP addresses by using the ifconfig command. If these ECS instances process requests only through SLB, no traffic fee is incurred for the traffic sent through the Internet even if traffic statistics are read at the public network interface \(NIC\).

-   If you want to provide external services through backend ECS instances, or backend ECS instances need to access the Internet, you must configure at least one of the following: a public IP address, an Elastic IP Address \(EIP\), or a NAT Gateway.

The following figure shows the outbound network traffic flow.

![](../DNslb1866251/../DNSLB11827830/images/2335_en-US.png "Outbound network traffic flow")

1.  For outbound traffic from SLB instances \(that is, traffic transferred through the Internet\), traffic is sent at speeds dependent on the current network capacity, and is charged. However, you are not charged for intranet communications, such as traffic transferred between SLB instances and backend ECS instances.
2.  For outbound traffic from an EIP or from NAT Gateway \(that is, traffic transferred through the Internet\), traffic is sent at speeds dependent on the current network capacity, and is charged. Additionally, if an ECS instance is configured with a public IP address when it is created, the outbound traffic from this instance is also charged.
3.  SLB supports dynamic access to the Internet. Specifically, if a backend ECS instance needs to access the Internet, you must first configure a public IP address for it \(by using an EIP or using NAT Gateway\).
4.  A public IP address \(configured when you create an ECS instance\), EIP, and NAT gateway all allow mutual Internet access. That is, ECS instances can access the Internet or be accessed from the Internet through any of these. Note, however, that they cannot forward traffic or balance traffic loads.

