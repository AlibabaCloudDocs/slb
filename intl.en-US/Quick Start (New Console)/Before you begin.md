# Before you begin {#concept_ug3_rfl_vdb .concept}

Before you use Server Load Balancer \(SLB\), you need to determine the instance type and region, network type, listener protocol, and backend servers according to your business needs.

## Instance region {#section_nby_m4l_vdb .section}

Consider the following scenarios when you select the region to which the SLB instance belongs:

-   To reduce latency and increase the download speed, select a region closest to your customers.
-   To provide more stable and reliable load balancing services, deploy primary and backup zones for zone-level disaster tolerance. To do this, make sure that you select a region in which primary and backup zones are available.
-   SLB does not support cross-region deployment. Therefore, make sure that the region selected for the SLB instance is the same as the region for your backend ECS instances.

## Network type {#section_o3k_44l_vdb .section}

SLB provides Internet and intranet load balancing services. Consider the following scenarios when you select the network type of an SLB instance:

-   If you want to use SLB to distribute requests from the Internet, create an Internet SLB instance.

    An Internet SLB instance is provided with a public IP address to receive requests from the Internet.

-   If you want to use SLB to distribute requests from the intranet, create an intranet SLB instance.

    An intranet SLB instance only has a private IP address and is accessible only from a classic network or VPC.


## Instance type {#section_v4f_bzg_y2b .section}

When you create an SLB instance, you need to choose either a guaranteed-performance or a shared-performance instance type.

The guaranteed-performance instance type provides greater flexibility in resource utilization so to guarantee service availability. For guaranteed-performance instances, Alibaba Cloud SLB provides six specifications for these instances to better meet your specific requirements. We recommend that you select the highest specification, Super I \(slb.s3.large\). This guarantees the running of your services and will not incur extra costs. However, if you do not require the highest specification available, you can choose a lower specification instance such as Higher Ⅱ \(slb.s3.medium\).

## Listener protocol {#section_bhq_r4l_vdb .section}

SLB supports Layer-4 \(TCP and UDP\) and Layer-7 \(HTTP and HTTPS\) load balancing.

-   A Layer-4 listener distributes requests directly to backend servers without modifying HTTP headers. After a request arrives at a Layer-4 listener, SLB uses the backend port configured in the listener to establish a TCP connection with backend ECS instances.
-   A Layer-7 listener is an implementation of reverse proxy. After a request arrives at a Layer-7 listener, SLB uses a TCP connection to transmit the data packets to backend ECS instances instead of transmitting the data packets directly.

    Layer-7 listeners involve one more procedure than Layer-4 listeners for forwarding incoming requests, which can lead to longer performance times. Moreover, scenarios involving insufficient client ports or excessive connections to the backend servers also affect the performance of Layer-7 listeners. Therefore, if you require high performance, we recommend that you use Layer-4 listeners.

    For more information, see [Protocols](../../../../../intl.en-US/User Guide/Listeners/Listener overview.md#table_spy_pp5_vdb).


## Backend servers {#section_f5v_54l_vdb .section}

Before using the SLB service, you must create an ECS instance, deploy applications on it, and add it to an SLB instance.

Note the following when you create and configure an ECS instance:

-   The region and zone of the ECS instance

    Make sure that the region of the ECS instance is the same as that of the SLB instance. Additionally, we recommend that you deploy each ECS instance in different zones to improve availability. For more information, see [Create an instance by using the wizard](../../../../../intl.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

    In this example, two ECS instances are created in the **China \(Hangzhou\)** region. They are named as ECS01 and ECS02 as shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15696/155530972033206_en-US.png)

-   Application configuration

    In this example, a static website is deployed on ECS01 and another on ECS 02 by using Apache, as shown in the following figure.

    -   Enter the EIP address attached to ECS01 in the browser:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15696/155530972038840_en-US.png)

    -   Enter the EIP address attached to ECS02 in the browser:

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15696/155530972038841_en-US.png)

    No additional configuration is required after you deploy applications on the ECS instances. However, if you want to use Layer-4 listeners, and the ECS instances use a Linux operating system, make sure that the values of the following parameters in the net.ipv4.conf file in /etc/sysctl.conf are set to `0`:

    ```
    
    net.ipv4.conf.default.rp_filter = 0
    net.ipv4.conf.all.rp_filter = 0
    net.ipv4.conf.eth0.rp_filter = 0
    ```


