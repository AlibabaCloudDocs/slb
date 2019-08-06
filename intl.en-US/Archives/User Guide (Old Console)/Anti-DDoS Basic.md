# Anti-DDoS Basic {#concept_qtj_cqn_vdb .concept}

You can view Alibaba Cloud Security thresholds of an Internet SLB instance on the SLB console.

## Introduction to Anti-DDoS Basic {#section_cnq_p3c_wdb .section}

Alibaba Cloud provides up to 5 Gbps basic anti-DDoS protection for SLB. As shown in the following figure, all traffic from the Internet must first go through Alibaba Cloud Security before arriving at SLB. Anti-DDoS Basic cleans and filters common DDoS attacks and protects your services against attacks such as SYN flood, UDP flood, ACK flood, ICMP flood, and DNS Query flood.

![](images/2870_en-US.jpeg)

Anti-DDoS Basic sets the cleaning threshold and blackhole threshold according to the bandwidth of the Internet SLB instance. When the inbound traffic reaches the threshold, the cleaning or blackhole is triggered:

-   Cleaning: When the attack traffic from the Internet exceeds the cleaning threshold or matches certain attack traffic model, Alibaba Cloud Security starts cleaning the attack traffic. The cleaning operation includes packet filtration, traffic speed limitation, packet speed limitation and so on.
-   Blackhole: When the attack traffic from the Internet exceeds the blackhole threshold, blackhole is triggered and all inbound traffic is dropped.

## View thresholds {#section_f35_ljc_wdb .section}

You can view the thresholds of an instance on the SLB console. If you cannot view the thresholds using a RAM account, ask your system administrator to grant the permission for you. For more information, see [Allow read-only access to Anti-DDoS Basic](#section_c4n_wjc_wdb).

To view thresholds, complete these steps:

1.  Log on to the [SLB console](https://slbnew.console.aliyun.com/?spm=a2c4g.11186623.2.6.XSuumL#/list/cn-hangzhou).
2.  Select a region.
3.  Hover the mouse pointer to the DDoS icon next to the target instance. You can click the link to go to the DDoS console to view more information.
    -   BPS threshold: When the inbound traffic exceeds the BPS cleaning threshold, cleaning is triggered.
    -   PPS threshold: When the inbound packets exceed the PPS cleaning threshold, cleaning is triggered.
    -   Blackhole threshold: When the inbound traffic exceeds the blackhole threshold, blackhole is triggered.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2871_en-US.png)


## Allow read-only access to Anti-DDoS Basic {#section_c4n_wjc_wdb .section}

To allow read-only access to Anti-DDoS Basic, complete these steps:

**Note:** You have to use the primary account to complete the authorization.

1.  Use the primary account to log on to the RAM console.
2.  In the left-side navigation pane, click **Users**, find the target RAM account and click **Manage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2872_en-US.png)

3.  Click **User Authorization Policies**, and then click **Edit Authorization Policy**.
4.  In the displayed dialog box, search **AliyunYundunDDosReadOnlyAccess**, and then add it to the Selected Authorization Policy Names list. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/2873_en-US.png)


