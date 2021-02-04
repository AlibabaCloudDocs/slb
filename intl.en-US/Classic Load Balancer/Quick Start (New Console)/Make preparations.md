# Make preparations

This topic describes the considerations for configuring a Server Load Balancer \(SLB\) instance. Before you create an SLB instance, you must determine the listener type and network type of the SLB instance.

## Select the region of the SLB instance

When you select a region, take note of the following issues:

-   To reduce latency and increase the download speed, we recommend that you select a region that is closest to your customers.
-   To provide more stable and reliable load balancing services, SLB supports primary/secondary zone deployment in most regions. This implements disaster recovery across data centers in the same region. We recommend that you select a region that supports primary/secondary zone deployment.
-   SLB does not support cross-region deployment. Therefore, you must deploy the SLB instance and backend Elastic Compute Service \(ECS\) instances in the same region.

## Select the network type of the SLB instance \(Internet-facing or internal-facing\)

SLB provides load balancing services for the public network and internal network:

-   If you want to use SLB to distribute requests from the Internet, create an Internet-facing SLB instance.

    An Internet-facing SLB instance is assigned a public IP address to receive requests from the Internet.

-   If you want to use SLB to distribute requests from the internal network, create an internal-facing SLB instance.

    An internal-facing SLB instance is assigned a private IP address and is only accessible from the internal network.


## Select an instance type

Apsara Stack released guaranteed-performance SLB instances on April 1, 2018. When you create an SLB instance, you can choose a guaranteed-performance instance that provides exclusive resources and higher service availability. SLB provides six types of instances:

-   For a pay-as-you-go instance, we recommend that you select the instance type that provides the highest specifications. This guarantees flexible load balancing services at no extra costs. However, if the capacity of Super I \(slb.s3.large\), the highest-performance instance type, far exceeds the demand of your business, you can select a more appropriate type such as Higher II \(slb.s3.medium\).

## Select a listener protocol

SLB supports Layer 4 \(TCP and UDP\) and Layer 7 \(HTTP and HTTPS\) load balancing:

-   A Layer 4 listener directly distributes requests to backend servers without modifying packet headers. After a client request reaches a Layer 4 listener, SLB uses the backend port that is configured for the listener to establish a TCP connection with a backend ECS instance.
-   A Layer 7 listener functions as a reverse proxy. After a client request reaches a Layer 7 listener, SLB establishes a new TCP connection over HTTP with a backend server, instead of directly forwarding the request to the backend server \(ECS instance\).

    Compared with Layer 4 listeners, Layer 7 listeners require an additional step of Tengine processing. Therefore, Layer 4 listeners provide better performance than Layer 7 listeners. In addition, the performance of Layer 7 listeners may be affected by factors such as insufficient client ports or excessive backend server connections. We recommend that you use Layer 4 listeners for high performance purposes.

    For more information, see [Protocols](/intl.en-US/Classic Load Balancer/User Guide/Listeners/Listener overview.md).


## Create backend servers

Before you use the SLB service, you must create ECS instances, deploy applications on the ECS instances, and then add the ECS instances to your SLB instance to process client requests.

When you create and configure an ECS instance, take note of the following issues:

-   Region and zones of the ECS instance

    Make sure that the ECS instance is deployed in the same region as the SLB instance. We recommend that you deploy ECS instances in different zones to improve availability. For more information about how to create an ECS instance, see [Create an instance by using the wizard](/intl.en-US/Instance/Create an instance/Create an instance by using the wizard.md).

    In this example, two ECS instances named ECS01 and ECS02 are created in the **China \(Hangzhou\)** region. The following figure shows their basic configurations.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/4275298951/p33206.png)

-   Configurations

    In this example, two static web pages are hosted on ECS01 and ECS02 by using Apache.

    -   Enter the elastic IP address \(EIP\) that is associated with ECS01 in the address bar of your browser.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3013359951/p2224.png)

    -   Enter the EIP that is associated with ECS02 in the address bar of your browser.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3013359951/p2231.png)

    No additional configurations are required after you deploy applications on the ECS instances. However, if you want to use a Layer 4 \(TCP or UDP\) listener and the ECS instances run Linux, make sure that the following parameters in the net.ipv4.conf file under /etc/sysctl.conf are set to 0:

    ```
    
    net.ipv4.conf.default.rp_filter = 0
    net.ipv4.conf.all.rp_filter = 0
    net.ipv4.conf.eth0.rp_filter = 0
    ```


