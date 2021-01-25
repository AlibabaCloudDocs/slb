# FAQ about SLB instances

The following questions about Server Load Balancer \(SLB\) instances are frequently asked:

-   [Can I change a shared-performance instance to a guaranteed-performance instance?](#section_erv_zby_wdb)
-   [What are the specifications of a shared-performance instance?](#section_frv_zby_wdb)
-   [How do I select suitable specifications for a guaranteed-performance instance?](#section_nmk_fcy_wdb)
-   [Can I change the specifications of a guaranteed-performance instance?](#section_lrv_zby_wdb)

## Can I change a shared-performance instance to a guaranteed-performance instance?

Yes, you can change a shared-performance instance to a guaranteed-performance instance.

After a shared-performance instance is changed to a guaranteed-performance instance, you are charged based on the specifications of the guaranteed-performance instance starting from April 1, 2018. The guaranteed-performance instance cannot be changed back to its original shared-performance instance.

## What are the specifications of a shared-performance instance?

Shared-performance instances do not guarantee the performance. No specifications are available.

## How do I select suitable specifications for a guaranteed-performance instance?

-   You can select the largest specifications for a pay-as-you-go instance, because pay-as-you-go instances are charged according to their actual usage and do not incur fees when they are idle.

## Can I change the specifications of a guaranteed-performance instance?

Yes, you can change the specifications of a guaranteed-performance instance.

-   You can upgrade or downgrade the specifications of a guaranteed-performance instance. For more information, see [Change the configurations of a pay-as-you-go SLB instance]().

**Note:**

-   After a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some previously created SLB instances are deployed in old clusters. If you change such a shared-performance instance to a guaranteed-performance instance, a network interruption may occur for 10 to 30 seconds due to instance migration. We recommend that you make the change during off-peak hours.

