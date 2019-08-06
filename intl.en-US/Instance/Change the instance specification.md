# Change the instance specification {#concept_wtn_kpy_pgb .concept}

You can change a shared-performance instance to a guaranteed-performance instance, or modify the specification of a guaranteed-performance instance.

Before you modify the instance specification, note the following:

-   When you change a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds.

    We recommend that you change the instance type in a low-traffic period, or use DNS to schedule services to other SLB instances before you change the instance type.

-   After you change a shared-performance instance to a guaranteed-performance instance, you cannot change it back.

    You can use the simple I \(slb. s1.small\) specification after you change a shared-performance instance to a guaranteed-performance instance. This specification is free of charge.

-   Intranet SLB instances only support traffic-based billing and cannot be changed to instances that are billed based on bandwidth.

## Change the specification of a Pay-As-You-Go instance {#section_z4f_2qy_pgb .section}

To change the specification of a Pay-As-You-Go instance, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Find the target instance, choose **More** \> **Change Specification**.
4.  In the Configuration upgrade section, select a new specification, and complete the payment.

