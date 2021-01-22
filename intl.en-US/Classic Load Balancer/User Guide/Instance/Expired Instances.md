# Expired Instances

This topic describes how to renew an expired Server Load Balancer \(SLB\) instance. If an SLB instance has an overdue payment, it is added to the list of expired instances and, if not handled, released.

If you do not pay for an expired instance, the process by which the instance is released is as follows:

-   Subscription instances: The SLB instance is stopped and locked, and added to the list of expired instances after an overdue payment is detected. If after seven days the payment is not settled, the SLB instance is released.
-   Pay-as-you-go instances: The SLB instance runs normally for 24 hours after an overdue payment is detected. If after 24 hours the payment is not settled, the SLB instance is stopped and locked, and added to the list of expired instances, but not released. If after seven days the payment is not settled, the SLB instance is released.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).

2.  Choose **Instances** \> **Expired Instances**.

3.  View detailed information of overdue instances.

4.  Find the target SLB instance and click **Renew** in the **Actions** column. After the renewal is complete, the instance will be added back to the Server Load Balancers list.


