# Scenarios {#concept_evl_4p4_tdb .concept}

Server Load Balancer \(SLB\) is suitable for applications with high access traffic to improve availability and reliability.

## Balance the loads of your applications {#section_gft_1x4_tdb .section}

If your applications experience high access traffic, SLB can help you distribute inbound traffic among multiple backend servers \(ECS instances\) according to the listening rules you set. Additionally, you can configure session persistence to distribute the requests from the same client to the same backend server.

## **Scale your applications** {#section_l45_dx4_tdb .section}

You can add or remove backend servers at any time to scale the serving capacity of your applications. SLB supports various web servers and application servers.

## Protect your applications from single points of failure {#section_gkp_3x4_tdb .section}

You can add multiple ECS instances to an SLB instance. If some ECS instances are faulty, SLB automatically shields faulty ECS instances and distributes requests to healthy ECS instances, guaranteeing that your applications can still work normally.

## Realize disaster tolerance across zones {#section_kc4_kx4_tdb .section}

To provide more stable and reliable services, SLB provides multiple zones in most regions to achieve same-region disaster tolerance. If the primary zone becomes unavailable, SLB switches to the secondary zone in about 30 seconds and the load balancing service will hardly be affected. Once the primary zone becomes available, SLB automatically switches back to the primary zone.

We recommend that you create an SLB instance in a region that has deployed multiple zones. You also need to consider the deployment of backend servers. We recommend that you add at least one backend server in each zone to achieve the highest efficiency.

As shown in the following figure, ECS instances in different zones are added to an SLB instance. In normal situation, SLB will distribute traffic to ECS instances both in the primary zone \(Zone A\) and in the secondary zone \(Zone B\). Once the primary zone is unavailable, the traffic will be distributed to the ECS instances in the secondary zone. This avoids service interruption caused by the failure of a single zone, and also reduces latency.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1559012052947_en-US.png)

However, if you deploy all ECS instances in the primary zone and have no ECS instances deployed in the secondary zone, your service will be interrupted when the primary zone is unavailable, because no ECS instances are available in the secondary zone to handle the distributed requests. This deployment mode achieves low latency at the expense of high availability.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1559012053948_en-US.png)

## Achieve disaster tolerance across regions {#section_x5d_5x4_tdb .section}

You can deploy SLB instances in different regions, and add ECS instances of different zones in the same region to an instance. Then, you can use Alibaba Cloud DNS to resolve domain names to service addresses of SLB instances in different regions, thus implementing global load balancing. When a region becomes unavailable, you can temporarily stop DNS in that region, and no user access will be affected.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4094/1559012053949_en-US.png)

