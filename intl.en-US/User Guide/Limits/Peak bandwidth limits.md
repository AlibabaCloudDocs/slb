# Peak bandwidth limits

Alibaba Cloud provides pay-by-bandwidth Server Load Balancer \(SLB\) instances and pay-by-data-transfer SLB instances. This topic describes the peak bandwidth limits of the two types of SLB instances.

## Peak bandwidth limits on SLB instances that use different billing methods

-   The maximum bandwidth of a pay-by-data-transfer instance is used as a reference. It indicates the upper limit of the peak bandwidth. This upper limit is not a guaranteed value.
-   For a pay-by-bandwidth SLB instance, its inbound peak bandwidth equals its outbound peak bandwidth. You are charged only for the outbound bandwidth that is consumed to transmit data from Alibaba Cloud to the Internet.
-   When SLB instances compete for resources, the peak bandwidth of pay-by-bandwidth SLB instances is guaranteed. However, the peak bandwidth of pay-by-data-transfer SLB instances may be limited.
-   The sum of the peak bandwidth of all pay-by-data-transfer SLB instances in each region under the same account cannot exceed 5 Gbit/s. If your business requires larger peak bandwidth, you can purchase pay-by-bandwidth SLB instances. You can purchase subscription SLB instances that are billed on a pay-by-bandwidth basis, or purchase pay-as-you-go SLB instances, and pay for the amount of bandwidth that you use. In addition, you can associate elastic IP addresses \(EIPs\) with SLB instances. In this case, the SLB instances are billed on a pay-by-95-percentile basis.

The maximum bandwidth values of pay-by-data-transfer SLB instances that are displayed in the SLB console shall prevail.

To view the maximum bandwidth of a pay-by-data-transfer SLB instance, perform the following operations:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou/slbs/lb-bp1w8s17q8x4pruibsaxd).
2.  In the left-side navigation pane, click **Instances**.
3.  On the **Instances** page, click the ID of the SLB instance that you want to manage.
4.  On the **Instance Details** page, you can view the maximum bandwidth.

![Bandwidth Peak](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5493796061/p187558.png)

