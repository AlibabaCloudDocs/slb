# Implement cross-region load balancing by using Global Traffic Manager

This topic describes how to manage global traffic over local load balancing services by using Global Traffic Manager \(GTM\) to accelerate access across regions and enable cross-region disaster recovery and intelligent resolution.

## Global Traffic Manager

Server Load Balancer \(SLB\) provides the local and global load balancing features according to the geographical positioning of its application. The local load balancing feature balances server groups in the same region, whereas the global load balancing feature balances server groups that are in different regions and have different network architectures.

-   Multi-line intelligent DNS resolution

    GTM uses intelligent DNS resolution to resolve domain names and uses health checks to check the running status of application services. This way, GTM directs access requests to the most appropriate IP addresses and provides fast and smooth access for users.

-   Cross-region disaster recovery

    GTM allows you to add IP addresses of different regions to different address pools and perform health checks. You can set the default address pool to **Address Pool A** and the failover IP address pool to **Address Pool B** in the access policy configurations. This enables the failover of application services between primary and secondary instances.

-   Accelerated access across regions

    You can use GTM to direct user access from different regions to different IP address pools, which enables group-based user management and group-based access to improve user experience of application services.


## Deployment of Global Traffic Manager

This section shows how to perform global load balancing by using GTM and SLB. A website with the aliyuntest.club domain name is used in the example. Most users of this website are located in Singapore and mainland China.

## Step 1: Purchase and configure ECS instances

Purchase and configure at least two ECS instances for each region in which the users of the application service reside.

In this example, two ECS instances are purchased in each of the China \(Beijing\), China \(Shenzhen\), and Singapore regions. A static web page is built on each ECS instance.

-   Example of the ECS instance in the China \(Beijing\) region
-   Example of the ECS instance in the China \(Shenzhen\) region
-   Example of the ECS instance in the Singapore region

## Step 2: Purchase and configure SLB instances

1.  Create an Internet-facing SLB instance in each of the China \(Beijing\), China \(Shenzhen\), and Singapore regions. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).
2.  Add listeners for the created SLB instances, and add the configured ECS instances to backend server groups. For more information, see [Configure an SLB instance](/intl.en-US/Classic Load Balancer/Quick Start (New Console)/Configure an SLB instance.md).

-   Example of the SLB instance in the China \(Beijing\) region
-   Example of the SLB instance in the China \(Shenzhen\) region
-   Example of the SLB instance in the Singapore region

## Step 3: Configure GTM

1.  Purchase a GTM instance.
    1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/#/dns/domainList).
    2.  In the left-side navigation pane, click **Global Traffic Manager**.
    3.  On the Global Traffic Manager page, click **Create Instance**.
    4.  Set Edition, Quantity, and Duration.
    5.  Click **Buy Now**.

        After the instance is purchased, the system allocates a CNAME record.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1273498951/p10621.png)

2.  Configure the GTM instance.
    1.  On the Global Traffic Manager page, click the ID of the instance or click **Configure** in the **Actions** column.
    2.  In the left-side navigation pane, click **Global Traffic Manager**.
    3.  On the Global Settings tab, click **Edit** to configure the instance.

        Set the following parameters and use the default values for the remaining parameters.

        -   Instance Name: The instance name is used to identify the application service for which the instance is used.
        -   Primary Domain: The primary domain name is used to access the application service. In this example, aliyuntest.club is used.
        -   Alert Group: When an exception occurs in GTM, the system notifies contacts in an alert contact group that you configured in Cloud Monitor.
    4.  Click **Confirm**.
3.  Create address pools.
    1.  On the Address Pool Configurations tab, click **Create Address Pool**.
    2.  In the Create Address Pool panel, configure the address pool.

        In this example, three address pools are created. Each address pool accommodates the addresses of one of the three SLB instances.

        -   Address Pool Name: Enter a name of the address pool. Example: China North\_Beijing, China East\_Shenzhen, or Singapore.
        -   Address: Enter the public IP address of the SLB instance that belongs to the specified region.
        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1273498951/p10664.png)

    3.  Click **Confirm**.
4.  Configure health checks.

    In this example, health checks are configured for the three created address pools.

    1.  On the Address Pool Configurations tab, click **Edit** to the right of the Health Check switch.
    2.  Configure health check parameters.

        The locations of monitoring nodes are displayed in the **Monitoring Node** section. Select a monitoring node based on the region of the address pool.

5.  Configure access policies.

    In this example, different access policies are added for the three regions.

    1.  On the Access Policy tab, click **Add Access Policy**.
    2.  In the Add Access Policy panel, configure the access policy.
        -   Configure corresponding default address pools for different access regions, and set an address pool of another region as the failover address pool.
        -   Select an access region. When users in this region access the application service, the address pool configured for the access policy is matched.

            The DNS Request Sources parameter of at least one access policy must be set to **Global**. Otherwise, the application service is inaccessible in some regions.

6.  Configure CNAME access.
    1.  Log on to the Alibaba Cloud DNS console.
    2.  Find the domain name aliyuntest.club and click **Configure** in the **Actions** column.
    3.  On the DNS Settings page, click **Add Record**.
    4.  On the Add Record page, direct the aliyuntest.club domain name that is accessed by end users to the CNAME record of the GTM instance.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1273498951/p10688.png)

    5.  Click **Confirm**.

## Step 4: Perform a test

Remove the backend servers that are attached to the SLB instance in the China \(Beijing\) region so that the SLB service becomes unavailable.

Visit the website to determine whether it can be accessed normally.

**Note:** It can take up to two minutes for GTM to make a judgment after it detects that your server is down. For example, if you set the monitoring frequency to one minute, it can take up to three minutes for failover to take effect.

