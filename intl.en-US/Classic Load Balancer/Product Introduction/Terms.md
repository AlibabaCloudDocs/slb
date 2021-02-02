# Terms

This topic introduces the terms used in CLB.

|Term|Description|
|:---|:----------|
|CLB|CLB distributes traffic across ECS instances. CLB provides Layer-4 and Layer-7 load balancing.|
|CLB instance|A load-balancing instance in CLB. To get started with CLB, you must create a CLB instance.|
|Endpoint|An IP address assigned to a CLB instance. The IP address can be either public or private, depending on the type of the CLB instance. You can resolve a domain name to a public IP address of a CLB instance to provide external services.|
|Listener|A listener distributes requests to backend servers. Each CLB instance must have at least one listener.|
|Backend server|A backend server is an ECS instance that receives client requests distributed by a CLB instance.|
|Default server group|A group of ECS instances that process distributed requests.

If a listener is not configured with any VServer group or primary/secondary server group, the listener distributes traffic to the backend servers in the default server group. |
|VServer group|A group of ECS instances that process distributed requests.

You can create multiple VServer groups for different listeners of a CLB instance to specify traffic distribution with specific listeners. |
|Primary/secondary server group|Each primary/secondary server group contains two ECS instances, where one acts as the primary server and the other acts as the secondary server. If the primary server is detected unhealthy, new requests are automatically distributed to the secondary server.|

