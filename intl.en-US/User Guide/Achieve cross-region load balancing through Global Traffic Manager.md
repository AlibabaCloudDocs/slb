# Achieve cross-region load balancing through Global Traffic Manager {#concept_hqf_4k5_vdb .concept}

By using Global Traffic Manager, you can apply global traffic balancing management on a higher plane than the level of local traffic balancing to achieve cross-region disaster tolerance, accelerate access across different regions, and achieve intelligent DNS resolution.

## Global traffic management {#section_nyz_jlc_wdb .section}

Server Load Balancer \(SLB\) provides local load balancing and global load balancing functions according to the geographical positioning of its application. Specifically, the local load balancing function balances a number of server groups in the same region, whereas the global load balancing function balances server groups that are in different regions and have different network requirements.

-   Multi-line intelligent resolution

    Global Traffic Manager \(GTM\) uses DNS intelligent resolution to resolve domain names and health checks to check the running status of application servers so that it can direct access requests to the most appropriate IP addresses, helping users experience the fastest and smoothest access.

-   Cross-region disaster tolerance

    With GTM, you can add IP addresses of different regions to different address pools and perform health checks. In access policy configurations, by setting the **address pool A** as the default IP address pool and **address pool B** as the failover IP address pool, you can realize disaster tolerance of IP addresses.

-   Accelerate access across different regions

    By using GTM, you can direct user access requests from different regions to different IP address pools, thus achieving grouped user and access management, and improving user experience.


## Deploy global traffic management {#section_zkj_hmc_wdb .section}

This topic takes the website aliyuntest.club as an example \(most users of the website are from Singapore and China\) to show you how to achieve global load balancing through GTM and SLB.

## Step 1 Purchase and configure ECS instances {#section_kcf_wcv_y2b .section}

Purchase and configure at least two ECS instances in each region where the users of the application service are located.

In this example, two ECS instances are purchased in Beijing, Shenzhen, and Singapore separately, and a simple static web page is built on each ECS instance.

## Step 2 Purchase and configure SLB instances {#section_u35_ypc_wdb .section}

1.  Create one Internet SLB instance in each of the region Beijing, Shenzhen, and Singapore. For more information about how to create an Internet SLB instance, see [Create an SLB instance](intl.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).
2.  Add listeners for the created SLB instances, and add the configured ECS instances to backend server groups. For more information, see [Configure an SLB instance](../../../../intl.en-US/Quick Start (New Console)/Configure an SLB instance.md#).

## Step 3 Configure GTM {#section_fkw_drc_wdb .section}

1.  Purchase a GTM instance.
    1.  Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/#/dns/domainList).
    2.  In the left-side navigation pane, click **Global Traffic Manager**.
    3.  On the Global Traffic Manager page, click **Create Instance**.
    4.  Select the **Version**, **Quantity**, and **Service Time**.
    5.  Click **Buy Now**.

        After the instance is successfully purchased, the system automatically allocates a CNAME record.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/155806041710621_en-US.png)

2.  Configure the GTM instance.
    1.  On the Global Traffic Manager page, click the target GTM instance ID or click **Configure** in the **Actions** column.
    2.  In the left-side navigation pane, click **Configurations**.
    3.  On the Global Settings tab page, click **Edit** to set the parameters of the GTM instance.

        Configure the following parameters and use the default values for the remaining parameters.

        -   **Instance Name**: It is used to help you identify which application this instance is created for. Enter a customized name.
        -   **Primary Domain**: It is the domain name you use to access the application. In this example, enter aliyuntest.club.
        -   **Alert Group**: Select an alarm contact group you configured in CloudMonitor. When an exception occurs, the contact group is notified.
    4.  Click **Confirm**.
3.  Configure address pool.
    1.  On the Address Pool Configurations tab page, click **Create Address Pool**.
    2.  On the Create Address Pool page, configure the address pool.

        In this example, create three address pools and each address pool accommodates the addresses of one of the three SLB instances.

        -   **Address Pool Name**: Enter a name, for example, China North\_Beijing, China East\_Shenzhen, and Singapore.
        -   **Address**: Enter the public IP address of the Internet SLB instance that belongs to the region in the address pool name.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/155806041710664_en-US.png)

    3.  Click **Confirm**.
4.  Configure health check.

    In this example, configure health checks for the three address pools separately.

    1.  On the Address Pool tab page, click the target address pool.
    2.  In the **Settings** area, click **Add** next to **Health Check**.
    3.  Set health check parameters.

        **Monitoring Node** shows the locations of monitoring nodes. Select the monitoring node according to the region of the address pool.

5.  Configure access policy.

    In this example, add different access policies for the three different regions.

    1.  On the Access Policy tab page, click **Add Access Policy**.
    2.  On the Add Access Policy page, configure the access policy.
        -   Configure corresponding default address pools for different access regions, and set an address pool of another region as the failover address pool.
        -   Select the access region. When users in this region access the application, the address pool configured in the access policy is matched.

            There must be an access policy with **Global** selected as the access region. Otherwise some regions cannot access the application.

6.  Configure CNAME access.
    1.  Log on to the Alibaba Cloud DNS console.
    2.  Find the domain name aliyuntest.club and click **Configure** in the **Actions** column.
    3.  On the DNS Settings page, click **Add Record**.
    4.  On the Add Record page, direct the domain name that is accessed by end users, aliyuntest.club in this example, to the CNAME record of the GTM instance.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15689/155806041710688_en-US.png)

    5.  Click **OK**.

## Step 4 Test {#section_sxj_ntc_wdb .section}

Remove the ECS instances of the SLB instance in Beijing so that the SLB service becomes unavailable.

Visit the website to see if the access is normal.

**Note:** It takes one to two minutes for GTM to make judgment after it detects that your IP address is down. If you set the monitoring frequency to 1 minute, it takes two to three minutes for the failover to take effect.

