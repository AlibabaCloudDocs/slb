# SLB instance overview {#concept_fsy_ssm_vdb .concept}

An SLB instance is a running entity of the Server Load Balancer service. To use the load balancing service, you must create an SLB instance first, and then add listeners and backend servers to it.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4112/15645483042275_en-US.png)

Alibaba Cloud provides Internet SLB service and intranet SLB service. A public or a private IP address is allocated to the SLB instance according to the instance type you select.

## Internet SLB instances {#section_vjt_kwm_vdb .section}

An Internet SLB instance distributes client requests over the Internet to backend ECS servers according to configured forwarding rules.

After you create an Internet Server Load Balancer instance, the system will allocate a public IP to the instance. You can resolve a domain name to the public IP to provide public services.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4112/15645483042276_en-US.png)

## Intranet SLB instances {#section_n5n_zwm_vdb .section}

Intranet SLB instances can only be used inside Alibaba Cloud and can only forward requests from clients that can access the intranet of SLB.

For an intranet SLB instance, you can further select the network type:

-   Classic network

    If you choose classic network for the intranet SLB instance, the IP of the SLB instance is allocated and maintained by Alibaba Cloud. The classic SLB instance can only be accessed by the classic ECS instances.

-   VPC network

    If you choose VPC network for the intranet SLB instance, the IP of the SLB instance is allocated from the CIDR of the VSwitch that the instance belongs to. SLB instances of the VPC network can only be accessed by ECS instances in the same VPC.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4112/15645483042283_en-US.png)


