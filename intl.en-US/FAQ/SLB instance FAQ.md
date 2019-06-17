# SLB instance FAQ {#concept_tkd_jh5_vdb .concept}

The following are frequently asked questions about SLB instances:

-   [Can I change a shared-performance instance to a guaranteed-performance instance?](#section_erv_zby_wdb)
-   [What are the specifications of a shared-performance instance?](#section_frv_zby_wdb)
-   [How do I select a suitable specification for a guaranteed-performance instance?](#section_nmk_fcy_wdb)
-   [Can I change the specification of a guaranteed-performance instance?](#section_lrv_zby_wdb)
-   [Are shared-performance instances still available for purchase?](#section_orv_zby_wdb)

## Can I change a shared-performance instance to a guaranteed-performance instance? {#section_erv_zby_wdb .section}

Yes.

After an SLB instance is changed to the guaranteed-performance type, it cannot be changed back.

## What are the specifications of a shared-performance instance? {#section_frv_zby_wdb .section}

Shared-performance instances do not guarantee the performance. No specifications are available.

## How do I select a suitable specification for a guaranteed-performance instance? {#section_nmk_fcy_wdb .section}

-   You can select the largest specification for a Pay-As-You-Go instance, because Pay-As-You-Go instances are charged according to the actual usage and no fees are incurred in idle time.

## Can I change the specification of a guaranteed-performance instance? {#section_lrv_zby_wdb .section}

Yes.

-   You can upgrade or downgrade the specification of a guaranteed-performance instance. For more information, see [Change the configuration](../../../../intl.en-US/Archives/User Guide (Old Console)/SLB instances/Change the configuration.md#).

**Note:** 

-   After a shared-performance instance is changed to a guaranteed-performance instance, it cannot be changed back.
-   Some previously created instances may exist in older clusters. If you change such a shared-performance instance to a guaranteed-performance instance, a brief disconnection of service may occur for 10 to 30 seconds due to instance migration. Therefore, for such scenarios, we recommend that you make the change when the traffic is low.

## Are shared-performance instances still available for purchase? {#section_orv_zby_wdb .section}

Yes.

However, shared-performance instances will be phased out in the future. Please pay attention to official notifications or emails.

