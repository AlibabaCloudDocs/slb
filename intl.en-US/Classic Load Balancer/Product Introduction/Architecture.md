# Architecture

This topic describes the CLB architecture. CLB instances are deployed in clusters to synchronize sessions and protect backend servers from SPOFs, improving redundancy and ensuring service stability. CLB supports Layer-4 load balancing of Transmission Control Protocol \(TCP\) and User Datagram Protocol \(UDP\) traffic, and Layer-7 load balancing of HTTP and HTTPS traffic.

CLB forwards client requests to backend servers by using CLB clusters and receives responses from backend servers over internal networks.

## CLB design

CLB provides Layer-4 and Layer-7 load balancing.

-   Layer-4 CLB combines the open-source Linux Virtual Server \(LVS\) with Keepalived to balance loads, and implements customized optimizations to meet cloud computing requirements.
-   Layer-7 CLB uses Tengine to balance loads. Tengine is a web server project launched by Taobao. Based on NGINX, Tengine has a wide range of advanced features optimized for high-traffic websites.

    ![Tengine](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3386229951/p938.png)


Layer-4 CLB runs in a cluster of LVS machines, as shown in the following figure. This cluster deployment model strengthens the availability, stability, and scalability of the load balancing service in abnormal cases.

![LVS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3386229951/p939.png)

In an LVS cluster, each machine uses multicast packets to synchronize sessions with the other machines. As shown in the following figure, Session A established on LVS1 is synchronized to the other LVS machines after the client sends three data packets to the ECS instance. Solid lines indicate the current active connections, while dotted lines indicate that the session requests will be sent to other normally working machines if LVS1 fails or is being maintained. This way, you can perform hot upgrades, machine failure maintenance, and cluster maintenance without affecting the operation of business applications.

**Note:** If a connection is not established \(the three-way handshake is not completed\), or if a connection has been established but session synchronization is not triggered during a hot upgrade, your service may be interrupted. In this case, you must re-initiate the connection from the client.

![LVS](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3386229951/p941.png)

## Inbound network traffic flow

SLB distributes incoming traffic according to the forwarding rules configured in the console or by using APIs. The following figure shows the inbound network traffic flow.

![](../images/p2333.png "Inbound network traffic flow")

1.  For TCP, UDP, HTTP, and HTTPS protocols, the incoming traffic must be forwarded through the LVS cluster first.
2.  Large amounts of access requests are evenly distributed among all servers in the LVS cluster. Servers synchronize sessions to guarantee high availability.
    -   For layer-4 listeners \(the frontend protocol is UDP or TCP\), the node servers in the LVS cluster distribute requests directly to backend ECS instances according to the configured forwarding rules.
    -   For layer-7 listeners that use the frontend protocol HTTP, the node servers in the LVS cluster first distribute requests to the Tengine cluster. Then, the node servers in the Tengine cluster distribute the requests to backend ECS instances according to the configured forwarding rules.
    -   For layer-7 listeners that use the frontend protocol HTTPS, the request distribution is similar to the HTTP protocol. However, before distributing requests to backend ECS instances, the system calls the Key Server to validate certificates and decrypt data packets.

## Outbound network traffic flow

SLB communicates with backend ECS instances through the internal network.

-   If backend ECS instances only need to handle the traffic distributed from SLB, no public bandwidth \(Elastic IP address, NAT Gateway, and public IP address\) is required, and you do not need to purchase any public bandwidth.

    **Note:** Previously created ECS instances are directly allocated with public IP addresses. You can view the public IP addresses by using the ifconfig command. If these ECS instances process requests only through SLB, no traffic fee is incurred for the traffic sent through the Internet even if traffic statistics are read at the public network interface \(NIC\).

-   If you want to provide external services through backend ECS instances, or backend ECS instances need to access the Internet, you must configure at least one of the following: a public IP address, an Elastic IP Address \(EIP\), or a NAT Gateway.

The following figure shows the outbound network traffic flow.

![](../images/p2335.png "Outbound network traffic flow")

In general, the traffic goes out from where it comes in:

1.  For outbound traffic from SLB instances \(that is, traffic transferred through the Internet\), traffic is sent at speeds dependent on the current network capacity, and is charged. However, you are not charged for internal communications, such as traffic transferred between SLB instances and backend ECS instances.
2.  For outbound traffic from an Elastic IP address or from NAT Gateway \(that is, traffic transferred through the Internet\), traffic is sent at speeds dependent on the current network capacity, and is charged. Additionally, if an ECS instance is configured with a public IP address when it is created, the outbound traffic from this instance is also charged.
3.  SLB supports dynamic access to the Internet. Specifically, if a backend ECS instance needs to access the Internet, you must first configure a public IP address for it \(by using an EIP or using NAT Gateway\).
4.  A public IP address \(configured when you create an ECS instance\), Elastic IP address, and NAT Gateway all allow mutual Internet access. That is, ECS instances can access the Internet or be accessed from the Internet through any of these. Note, however, that they cannot forward traffic or balance traffic loads.

