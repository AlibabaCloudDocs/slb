# Expiring Instances {#task_ych_nm5_42b .task}

This topic describes how to renew an expiring Server Load Balancer \(SLB\) instance. If an SLB instance has an overdue payment, it is added to the list of expiring instances and, if not handled, released.

If you do not renew an expiring instance, the process by which the instance is released is as follows:

-   Subscription instances: The SLB instance is stopped and locked, and added to the list of expiring instances after an overdue payment is detected. If after seven days the payment is not settled, the SLB instance is released.
-   Pay-As-You-Go instances: The SLB instance runs normally for 24 hours after an overdue payment is detected. If after 24 hours the payment is not settled, the SLB instance is stopped and locked, and added to the list of expiring instances, but not released. If after seven days the payment is not settled, the SLB instance is released.

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  Choose **Instances** \> **Expiring Instances**.
3.  View detailed information of overdue instances.
4.  Find the target SLB instance and click **Renew** in the **Actions** column, then the instance will be added back to the Server Load Balancer list.

