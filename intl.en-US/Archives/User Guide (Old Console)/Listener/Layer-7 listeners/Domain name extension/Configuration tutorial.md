# Configuration tutorial {#concept_blk_jy1_wdb .concept}

This tutorial introduces detailed steps for configuring a domain name extension.

## Scenario {#section_eqs_54t_q2b .section}

This tutorial takes SLB1, the guaranteed-performance SLB instance in China \(Hangzhou\) region as an example. In this tutorial, an HTTPS listener is created and one-way authentication is used. You need to forward requests with the domain name \*.example1.com to the VServer group test1 and forward requests from the domain name www.example2.com to the VServer group test2.

You need to complete these steps:

1.  Add an HTTPS listener.
2.  Configure forwarding rules.
3.  Add a domain name extension.

## Prerequisites {#section_krq_z4t_q2b .section}

-   Create a guaranteed-performance SLB instance, SLB1, in China \(Hangzhou\). For more information, see [Create an SLB instance](reseller.en-US/User Guide/SLB instances/Create an SLB instance.md#).
-   Upload the certificate required in this tutorial. For more information, see [Upload certificates](reseller.en-US/User Guide/Certificate management/Upload certificates.md#).
    -   The default certificate used by the listener is default.
    -   The certificate used by the domain name \* .example1.com is example1.
    -   The certificate used by the domain name www.example2.com is example2.

## Step 1 Create an HTTPS listener {#section_wvf_3nb_wdb .section}

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  On the Instances page, click **Create SLB Instance**.

    Configure the SLB instance. For more information, see [Create an SLB instance](reseller.en-US/User Guide/SLB instances/Create an SLB instance.md#).

    **Note:** Only guaranteed-performance instances support configuring SNI.

3.  Go back to the Instances page, and then click the ID of the created SLB instance.
4.  In the left-side navigation pane, click **Listeners** and then click **Add Listener**.
5.  Configure the listener.

    The configurations used in this tutorial are as follows. For more information, see [Layer-7 listener configurations](reseller.en-US/User Guide/Listener/Layer-7 listeners/Layer-7 listener configurations.md#).

    -   **Mutual Authentication**: Disable
    -   **Server Certificate**: Upload a server certificate named as default.
6.  Select **Servers** \> **VServer Groups**, click **Create VServer Group**, and create VServer groups test1 and test2.

## Step 2 Add forwarding rules {#section_fns_2qc_wdb .section}

1.  On the Listeners page, find the created HTTPS listener and click **Add Forwarding Rules**.
2.  On the Add Forwarding Rules page, click **Add Forwarding Rules**.
3.  Configure forwarding rules. For more information, see [Add domain-name based or URL-based forwarding rules](reseller.en-US/User Guide/Listener/Layer-7 listeners/Add domain-name based or URL-based forwarding rules.md#).

    In this tutorial, domain name-based forwarding rules are configured and URLs are left empty.

    -   Set the rule name, enter \* .example1.com in the **Domain Name** action column, select the test1 VServer group and click **Add Forwarding Rule**.
    -   Set the rule name, enter www.example2.com in the **Domain Name** action column, and select the test2 VServer group and click **OK**.

## Step 3 Add a domain name extension {#section_ykj_pvb_wdb .section}

1.  On the Listeners page, find the created HTTPS listener, and then click **More** \> **Domain Extensions**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/13400/15389926132851_en-US.png)

2.  Click **Add Domain Extension** and configure a domain name:
    -   Domain Name: Enter a domain name.

        Both exact match and wildcard match are supported:

        -   Exact domain name: www.aliyun.com

        -   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

            When a request matches multiple domain name forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table \(√ indicates that the domain name is matched, — indicates that the domain name is not matched\).

            |Type|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:---|:----------|:--------------------------------|
            |:-------------|:------------|:-------------------|
            |Exact match|www.aliyun.com|✔|-|—|
            |Wildcard match|Market.aliyun.com|—|✔|—|
            |Wildcard match|info.market.aliyun.com|-|—|✔|

        -   Certificate: Select the certificate used by this domain name.

            If the certificate is not uploaded yet, click **Import Certificate**.

            **Note:** The domain name in the certificate must be the same as the added domain name extension.

3.  Repeat step 2 to add more domain name extensions.

