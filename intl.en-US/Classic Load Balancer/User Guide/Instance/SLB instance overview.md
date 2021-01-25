# SLB instance overview

A Server Load Balancer \(SLB\) instance is a running entity of the SLB service. To use the SLB service, you must create an SLB instance and add listeners and backend servers to the instance.

![Instance overview](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6013359951/p2275.png)

## Instance network types

Alibaba Cloud provides Internet and internal SLB instances. If you create an Internet SLB instance, a public IP address is allocated. If you create an internal SLB instance, a private IP address is allocated.

![Instance network types](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6013359951/p2276.png)

-   Internet SLB instances

    An Internet SLB instance distributes client requests to backend Elastic Compute Service \(ECS\) instances over the Internet based on specified listening rules.

    After you create an Internet SLB instance, the system allocates a public IP address to the instance. You can bind a domain name to the public IP address to provide external services.

-   Internal SLB instances

    Internal SLB instances can be used only inside Alibaba Cloud, and can forward requests only from clients that can access SLB instances over the internal network.

    For an internal SLB instance, you can further specify its network type:

    -   Classic network

        If the network type of an internal SLB instance is set to Classic Network, Alibaba Cloud allocates an IP address to the SLB instance and manages the IP address. The internal SLB instance can be accessed only by ECS instances in the classic network.

    -   VPC

        If the network type of an internal SLB instance is set to VPC, the system allocates an IP address to the SLB instance from the CIDR block of the VSwitch to which the SLB instance belongs. The internal SLB instance can be accessed only by the ECS instances that are located within the same VPC.

        ![VPC](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/6013359951/p2283.png)


## Instance types and specifications

SLB provides shared-performance instances and guaranteed-performance instances. Guaranteed-performance instances provide reliable performance.

-   Shared-performance instances

    All shared-performance instances share SLB resources, which means their performance cannot be guaranteed.

-   Guaranteed-performance instances

    The following section describes three key metrics for guaranteed-performance instances:

    -   Max Connection

        The maximum number of connections to an SLB instance. When the number of connections reaches the limit of the specification, new connection requests are dropped.

    -   Connection Per Second \(CPS\)

        The number of new connections that are established per second. When the CPS reaches the limit of the specification, new connection requests are dropped.

    -   Queries Per Second \(QPS\)

        The number of HTTP/HTTPS requests that can be processed per second. This metric is available only for layer-7 SLB listeners. When the QPS reaches the limit of the specification, new connection requests are dropped.


The following table describes the types and specifications of guaranteed-performance instances. For more information, see [Guaranteed-performance instance FAQ](/intl.en-US/Classic Load Balancer/User Guide/Instance/FAQ/Guaranteed-performance instance FAQ.md).

|Type|Specification|Max Connection|CPS|QPS|Purchase method|
|:---|:------------|:-------------|:--|:--|---------------|
|Specification 1|Small I \(slb.s1.small\)|5,000|3,000|1,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 2|Standard I \(slb.s2.small\)|50,000|5,000|5,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 3|Standard II \(slb.s2.medium\)|100,000|10,000|10,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 4|Higher I \(slb.s3.small\)|200,000|20,000|20,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 5|Higher II \(slb.s3.medium\)|500,000|50,000|30,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 6|Super I \(slb.s3.large\)|1,000,000|100,000|50,000|Available for purchase from the official website of Alibaba Cloud.|
|Specification 7|Super II \(slb.s3.xlarge\)|2,000,000|200,000|100,000|Contact your account manager.|
|Specification 8|Super III \(slb.s3.xxlarge\)|5,000,000|500,000|100,000|Contact your account manager.|

The following table describes the differences between shared-performance instances and guaranteed-performance instances.

|Feature|Shared-performance instance|Guaranteed-performance instance|
|-------|---------------------------|-------------------------------|
|Resource allocation|Shared resources|Exclusive resources|
|SLA-guaranteed availability|Not supported|99.95%|
|IPv6|×|√|
|Support for Server Name Indication \(SNI\) certificates|×|√|
|Support for blacklists and whitelists|×|√|
|Support for ENI mounting|×|√|
|Support for elastic network interfaces \(ENIs\)|×|√|
|HTTP-to-HTTPS redirection|×|√|
|Support for consistent hashing|×|√|
|Support for TLS security policies|×|√|
|HTTP2|×|√|
|Websocket\(S\)|×|√|

