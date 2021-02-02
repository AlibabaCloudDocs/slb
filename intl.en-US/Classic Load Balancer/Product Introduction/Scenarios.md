# Scenarios

Classic Load Balancer \(CLB\) can be used to improve the availability and reliability of applications with high access traffic.

## Balance the loads of your applications

You can configure listening rules to distribute heavy traffic among ECS instances that are attached as backend servers to CLB instances. You can also use the session persistence feature to forward all of the requests from the same client to the same backend ECS instance to enhance access efficiency.

## Scale your applications

You can extend the service capability of your applications by adding or removing backend ECS instances to suit your business needs. CLB can be used for both web servers and application servers.

## Eliminate single points of failure \(SPOFs\)

You can attach multiple ECS instances to a CLB instance. When an ECS instance malfunctions, CLB automatically isolates this ECS instance and distributes inbound requests to other healthy ECS instances, ensuring that your applications continue to run properly.

## Implement zone-disaster recovery \(multi-zone disaster recovery\)

To provide more stable and reliable load balancing services, Alibaba Cloud allows you to deploy CLB instances across multiple zones in most regions for disaster recovery. Specifically, you can deploy a CLB instance in two zones within the same region. One zone is the primary zone, while the other zone is the secondary zone. If the primary zone fails or becomes unavailable, the CLB instance will fail over to the secondary zone in about 30 seconds. When the primary zone recovers, the CLB instance will automatically switch back to the primary zone.

We recommend that you create a CLB instance in a region that has multiple zones for zone-disaster recovery. We recommend that you plan the deployment of backend servers based on your business needs. In addition, we recommend that you add at least one backend server in each zone to achieve the highest load balancing efficiency.

As shown in the following figure, ECS instances in different zones are attached to a single CLB instance. In normal cases, the CLB instance distributes inbound traffic to ECS instances both in the primary zone \(Zone A\) and in the secondary zone \(Zone B\). If Zone A fails, the CLB instance distributes inbound traffic only to Zone B. This deployment mode helps avoid service interruptions caused by zone-level failure and reduce latency.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8384522161/p947.png)

Assume that you deploy all ECS instances in the primary zone \(Zone A\) and no ECS instances in the secondary zone \(Zone B\) as shown in the following figure. If Zone A fails, your services will be interrupted because no ECS instances are available in Zone B. This deployment mode achieves low latency at the cost of high availability.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8384522161/p948.png)

## Geo-disaster recovery

You can deploy CLB instances in different regions and attach ECS instances of different zones within the same region to a CLB instance. You can use DNS to resolve domain names to service addresses of CLB instances in different regions for global load balancing purposes. When a region becomes unavailable, you can temporarily stop DNS resolution within that region without affecting user access.

![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8384522161/p949.png)

