# Server Load Balancer instance FAQ

The following are frequently asked questions about Server Load Balancer \(SLB\) instances:

-   [Can I change a shared-performance instance to a guaranteed-performance instance?](#section_erv_zby_wdb)
-   [What are the specifications of a shared-performance instance?](#section_frv_zby_wdb)
-   [How do I select a suitable specification for a guaranteed-performance instance?](#section_nmk_fcy_wdb)
-   [Can I change the specification of a guaranteed-performance instance?](#section_lrv_zby_wdb)

## Can I change a shared-performance instance to a guaranteed-performance instance?

Yes.

After an SLB instance is changed to the guaranteed-performance type, it cannot be changed back.

## What are the specifications of a shared-performance instance?

Shared-performance instances do not guarantee the performance. No specifications are available.

## How do I select a suitable specification for a guaranteed-performance instance?

-   You can select the largest specification for a pay-as-you-go instance, because pay-as-you-go instances are charged according to the actual usage and no fees are incurred in idle time.

## Can I change the specification of a guaranteed-performance instance?

Yes.

-   You can upgrade or downgrade the specification of a guaranteed-performance instance. For more information, see [Change the specification of an SLB instance]().

**Note:**

-   After a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some previously created instances may exist in older clusters. If you change such a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds due to instance migration. Therefore, for such scenarios, we recommend that you make the change when the traffic is low.

