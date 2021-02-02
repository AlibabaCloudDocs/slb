# Network traffic flow

Classic Load Balancer \(CLB\) uses CLB clusters to forward client requests to backend servers and receives responses from backend servers over the internal network.

## Inbound network traffic flow

CLB distributes incoming traffic according to forwarding rules configured in the console or by using API operations. The following figure shows the inbound network traffic flow.

![](../images/p2333.png "Inbound network traffic flow")

1.  For TCP, UDP, HTTP, and HTTPS protocols, the incoming traffic must be forwarded through the LVS cluster first.
2.  The large amounts of inbound traffic is distributed evenly among all node servers in the LVS cluster, and the node servers synchronize sessions to ensure high availability.
    -   For Layer 4 listeners \(either UDP or TCP\), the node servers in the LVS cluster distribute requests directly to backend ECS instances according to the configured forwarding rules.
    -   For Layer 7 listeners that use the HTTP frontend protocol, the node servers in the LVS cluster first distribute requests to the Tengine cluster. Then, the node servers in the Tengine cluster distribute the requests to backend ECS instances according to the configured forwarding rules.
    -   For Layer 7 listeners that use the HTTPS frontend protocol, the request distribution is similar to the HTTP protocol except that the system calls the Key Server to validate certificates and decrypt data packets before requests are distributed to backend ECS instances.

## Outbound network traffic flow

CLB communicates with backend ECS instances by using the internal network.

-   If backend ECS instances handle the traffic distributed only from CLB, no public bandwidth \(ECS instances, EIPs, NAT gateways, and public IP addresses\) is required, and you do not need to purchase public bandwidth.

    **Note:** Previously created ECS instances are directly allocated with public IP addresses. You can view the public IP addresses by using the ipconfig command. If these ECS instances process requests only through CLB, no traffic fees are incurred for Internet traffic even if traffic statistics are read at the public network interface \(NIC\).

-   If you want to provide external services through backend ECS instances, or backend ECS instances need to access the Internet, you must configure at least one of the following services: an ECS instance, a public IP address, an Elastic IP Address \(EIP\), or a NAT gateway.

The following figure shows the outbound network traffic flow.

![](../images/p2335.png "Outbound network traffic flow")

General principle: The traffic goes out from where it comes in.

-   Outbound traffic from CLB instances is charged, and the speeds at which it is sent depend on the current network capacity. However, you are not charged for inbound traffic and internal communications between CLB instances and backend ECS instances.
-   Traffic from an EIP or from a NAT gateway incurs charges. The speed at which EIP or NAT gateway traffic is sent depends on the current network capacity. If you configure public bandwidth when you purchase an ECS instance, traffic is sent at speeds dependent on the current network capacity, and is charged.
-   CLB supports dynamic access to the Internet. Specifically, if a backend ECS instance needs to access the Internet, you must first configure public bandwidth for it, and purchase an EIP or a NAT gateway.
-   The public bandwidth that you configured when you create ECS instances, EIPs, and NAT gateways allow ECS instances to access the Internet or be accessed from the Internet, but they cannot forward traffic or balance traffic loads.

