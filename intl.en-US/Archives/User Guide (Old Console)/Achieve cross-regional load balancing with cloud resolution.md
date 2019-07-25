# Achieve cross-regional load balancing with cloud resolution {#concept_hqf_4k5_vdb .concept}

## Global load balancing {#section_nyz_jlc_wdb .section}

Load balancing is divided into local load balancing and global load balancing. Local load balancing balances loads of server groups in the same region. Global load balancing balances server groups that are in different regions and have different network structures.

Combined with cloud resolution \(global load balancing edition \), you can deploy cloud resolution \(global load balancing edition\) on the local load balancing upper layer \), achieve cross-regional disaster recovery and intelligent resolution.

-   Multi-line intelligent analytical service

    Multi-line intelligent resolution is supported by cloud resolution \(global load balancing, that is, based on the type of network that the site visitor is located in, the intelligent judgment provides the best access resolution address, enables access to the user for the fastest and most smooth experience.

    As shown in the figure below, when judging the source of the visitor as an overseas user, the domain name is resolved to a load balancing instance located in the united states; when judging the source of the visitor as a domestic user, the domain name is resolved to the domestic load balancing instance.

-   Cross-regional disaster recovery

    Cloud resolution provides monitoring services that monitor the ip address that the host logs. According to the monitoring and detection results of the website, the fault cluster is isolated in real time and the flow rate is switched dynamically, achieve cross-regional disaster recovery.


## Deploy global load balancing {#section_zkj_hmc_wdb .section}

This operation takes a domain name as aliyuntest. club's website \(for example, the majority of its users are located in singapore and in the country \), guides you through cloud resolution and load balancing for global load balancing.

Step 1 purchase and configure the cloud server

Depending on the geographic distribution of the users of your application service, purchase and configure at least two ecs under the appropriate geographic area.

In this operation, in beijing, shenzhen and singapore, two ecs were purchased separately, and set up a simple static web page on ecs.

-   Beijing regional ecs example
-   Shenzhen regional ecs example
-   Example of regional ecs in singapore

## Step 2: purchase and configure load balancing instances {#section_u35_ypc_wdb .section}

1.  Refer to creating load balancing instances in beijing, shenzhen and singapore to create three public load balancing instances.
2.  Refer to configuring load balancing instances to add listening and adding the ecs configured under each zone to the back-end server pool.

-   Example of load balancing in beijing
-   Example of load balancing in shenzhen
-   Example of regional load balancing in singapore

## Step 3 configure global load balancing {#section_fkw_drc_wdb .section}

1.  Configure cloud resolution for global load balancing.
    1.  On the global load balancing page, click buy now.
    2.  Configure cloud resolution for global load balancing.

        In this operation, other configurations use the default options in addition to the following:

        -   Configuration type, select global load balancing edition.
        -   Global load balancing type, select inter-line load balancing.
        -   Bind your site domain name. You can also bind domain names after creation.
    3.  Click buy now.
    4.  The vip product page of the dns management console is resolved on the cloud, view the global load balancing cloud resolution instance created.
2.  Sets intelligent resolution.
    1.  Log in to the domain name service management console.
    2.  Locate the domain name that the cloud resolution instance is bound to, and then click the resolution setting that is listed in its actions.
    3.  Sets the domain name resolution. Add three a records to point to the public network ip of the load balancing instance that was created, respectively, it also sets the-record analytical line of the singapore area to overseas.
3.  Add a web site monitor.
    1.  On the parse settings page, click web site monitoring.
    2.  Click Add monitor to add the IP address of the three A records to the monitor list.
    3.  Modify the monitoring configuration by clicking the settings option for each monitor record.

        Set the switchover rule when the domain name record cannot be accessed to force a pause of the record resolution.

4.  Turn on global load balancing.
    1.  On the parse settings page, click global load balancing.
    2.  Click the inter-line load balancing tab, select the target domain name, and then click open.
    3.  In the pop-up dialog box, click OK.

## Step 4 test {#section_sxj_ntc_wdb .section}

Remove the back-end server for the beijing regional load balancing instance so that the service for the load balancing instance is unavailable.

Visit the website to see if the access is normal.

**Note:** Cloud-resolved dns monitoring takes 1-2 minutes to aggregate judgment after your ip downtime, suppose your monitoring frequency is set to 1 minute, then the line abnormal switching effective time in 2-3 minutes; if your monitoring frequency is set to 10 minutes, then the line abnormal switching effective time in 12-13 minutes.

