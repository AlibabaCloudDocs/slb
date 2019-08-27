# Terms {#concept_fz5_np4_tdb .concept}

This topic describes the terms commonly used in Alibaba Cloud Server Load Balancer.

|Term|Description|
|:---|:----------|
|Server Load Balancer|Alibaba Cloud Server Load Balancer \(SLB\) is a traffic distribution and control service that distributes the incoming traffic among multiple Elastic Compute Service \(ECS\) instances according to configured forwarding rules.|
|SLB instance|An SLB instance is a running entity of the SLB service. To use SLB, you must first create an SLB instance.|
|endpoint|An IP address allocated to an SLB instance. According to the instance type, the IP address is either a public IP address or a private IP address. You can resolve a domain name to a public IP address to provide external services.|
|listener|A listener defines how incoming requests are distributed. An SLB instance must contain at least one listener.|
|backend server|The ECS instances that are added to an SLB instance to process distributed requests.|
|default server group| A group of ECS instances that process the distributed requests.

 If a listener does not configure a VServer group or an active/standby server group, the default server group is used. Incoming traffic is distributed to ECS instances in the default server group.

 |
|VServer group| A group of ECS instances that process the distributed requests.

 Different listeners can be associated with different VServer groups to distribute different requests to different backend servers.

 |
|active/standby server group|An active/standby server group contains only two ECS instances. One is the active server and the other is the standby server. When the health check of the active server fails, SLB automatically forwards traffic to the standby server.|

