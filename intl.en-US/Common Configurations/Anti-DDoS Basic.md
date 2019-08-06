# Anti-DDoS Basic {#concept_qtj_cqn_vdb .concept}

You can view Alibaba Cloud Security thresholds of an Internet Server Load Balancer \(SLB\) instance through the SLB console.

## Introduction to Anti-DDoS Basic {#section_cnq_p3c_wdb .section}

Alibaba Cloud provides up to 5 Gbit/s Anti-DDoS Basic for SLB. As shown in the following figure, all traffic from the Internet must first go through Alibaba Cloud Security before arriving at SLB. Anti-DDoS Basic scrubs and filters common DDoS attacks and protects your services against attacks such as SYN flood, UDP flood, ACK flood, ICMP flood, and DNS Query flood.

![](../DNSLB11827830/images/2870_en-US.jpeg)

Anti-DDoS Basic sets the scrubbing threshold and blackholing threshold according to the bandwidth of the Internet SLB instance. When the inbound traffic reaches the threshold, scrubbing or blackholing is triggered:

-   Scrubbing: When the attack traffic from the Internet exceeds the scrubbing threshold or matches certain attack traffic model, Alibaba Cloud Security starts scrubbing the attack traffic. The scrubbing includes packet filtration, traffic speed limitation, packet speed limitation and more.
-   Blackholing: When the attack traffic from the Internet exceeds the blackholing threshold, blackholing is triggered and all inbound traffic is dropped.

The thresholds are calculated based on the following principles:

-   The thresholds are determined by the bandwidth of the SLB instance, that is, the outbound bandwidth of the SLB instance. The thresholds are high when the bandwidth of the instance is high and vise versa.
-   The blackholing threshold is determined by the security credit score of your account.

    **Note:** The security credit score only influences the blackholing threshold and does not influence the scrubbing threshold.


Complete these steps to calculate the threshold:

1.  The SLB backstage provides the recommended threshold value that can ensure normal running of the instance according to the purchased bandwidth.

    **Note:** The outbound bandwidth of a Pay-As-You-Go instance is the peak bandwidth in the region. Currently the peak bandwidth in Mainland China is 5 Gbit/s. For more information, see [EN-US\_TP\_15672.md\#](intl.en-US/Limits/Peak bandwidths in different regions.md#).

    -   The relationship between SLB bandwidth and traffic scrubbing threshold \(bit/s\)
        -   When the SLB bandwidth < 100 Mbit/s, the default traffic scrubbing threshold \(bit/s\) = 120 Mbit/s
        -   When the SLB bandwidth \> 100 Mbit/s, the default traffic scrubbing threshold \(bit/s\) = bandwidth × 1.2
    -   The relationship between SLB bandwidth and traffic scrubbing threshold \(packet/s\)

        Traffic scrubbing threshold \(packet/s\) = \(SLB bandwidth/500\) × 150000

        The SLB bandwidth is in Mbit/s.

    -   The relationship between SLB bandwidth and blackholing threshold \(bit/s\)
        -   When the SLB bandwidth < 1 Gbit/s, the default blackholing threshold \(bit/s\) = 2 Gbit/s
        -   When the SLB bandwidth \> 1 Gbit/s, the default blackholing threshold \(bit/s\) = MAX \(SLB bandwidth × 1.5, 2 Gbit/s\)
2.  Alibaba Cloud Security calculates the threshold according to the recommended value, the security credit score and the resource conditions in different regions.
    -   Rules for determining the traffic scrubbing threshold \(bit/s\) and the traffic scrubbing threshold \(packet/s\)

        The minimum traffic scrubbing threshold \(bit/s\) is 1,000 M and the minimum traffic scrubbing threshold \(packet/s\) is 300,000.

        -   If the threshold recommended by SLB is lower than the minimum cleaning threshold, the minimum threshold is used.
        -   If the threshold recommended by SLB is higher than the minimum cleaning threshold, the recommended threshold is used.
    -   Alibaba Cloud Security determines the blackholing threshold according to the security credit score of your account.

## View thresholds {#section_f35_ljc_wdb .section}

You can view the thresholds of an instance in the SLB console as a RAM user. If not, you must authorize the RAM account first. For more information, see [Allow read-only access to Anti-DDoS Basic](#section_c4n_wjc_wdb).

To view thresholds, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/).
2.  Select the region of the target SLB instance.
3.  Rest the pointer over the DDoS icon next to the target SLB instance to view the following thresholds. You can click the link to go to the DDoS console to view more information.
    -   Traffic Scrubbing Threshold \(bit/s\): When the inbound traffic exceeds this value, scrubbing is triggered.
    -   Traffic Scrubbing Threshold \(packet/s\): When the inbound packets exceed this value, scrubbing is triggered.
    -   Blackholing Threshold: When the inbound traffic exceeds this value, blackholing is triggered.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15694/15645485067339_en-US.png)


## Allow read-only access to Anti-DDoS Basic {#section_c4n_wjc_wdb .section}

To allow read-only access to Anti-DDoS Basic, follow these steps:

**Note:** Use the Alibaba Cloud account to complete the authorization.

1.  Use the Alibaba Cloud account to log on to the RAM console.
2.  In the left-side navigation pane, click **Users**, find the target RAM user and click **Manage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/15645485062872_en-US.png)

3.  Click **User Authorization Policies**, and then click **Edit Authorization Policy**.
4.  In the displayed dialog box, search **AliyunYundunDDosReadOnlyAccess**, and then add it to the Selected Authorization Policy Name list. Click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4157/15645485062873_en-US.png)


## View the security credit score {#section_chv_cjy_gfb .section}

The security credit score is provided by Alibaba Cloud based on your attack history, purchase history, account activity, security level, expectation and more. With a higher security credit score, you can have a higher free blackholing threshold and a shorter blackholing duration \(how long the blackholing status lasts\).

To view the security credit score, follow these steps:

1.  Log on to the [Anti-DDoS Basic console](https://yundun.console.aliyun.com/?p=ddosnext#/instance/cn-hangzhou).
2.  Select **Anti-DDoS Basic** \> **Instances**.
3.  Click the **Security Credibility** link to view the security credit score of the account.

    **Note:** Security credit scores are region-based.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15694/156454850712959_en-US.png)


