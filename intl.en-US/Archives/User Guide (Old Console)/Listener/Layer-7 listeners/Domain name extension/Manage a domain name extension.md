# Manage a domain name extension {#concept_ypl_xvh_r2b .concept}

An HTTP listener of guaranteed-performance SLB support configuring multiple certificates. Therefore, an HTTP listener can forward requests destined for different domain names to different backend servers.

## SNI overview {#section_kfl_lsc_wdb .section}

Server Name Indication \(SNI\) is an extension to the SSL/TLS protocol, allowing a server to install multiple certificates on the same IP address. Only the guaranteed-performance instances support SNI. When a client accessing SLB, the certificate configured for the domain name is used by default. If no certificate is configured for the domain name, the certificates configured for the HTTPS listener is used.

When you want to resolve multiple domain names to the IP address of an SLB instance, distinguish access sources by domain name and use HTTPS to encrypt the requests, you can configure SNI.

The SNI function is available in all regions.

**Note:** FinCloud does not support SNI.

## Add a domain name extension {#section_ykj_pvb_wdb .section}

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select the target region and all SLB instances in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  In the left-side navigation pane, click Listeners.
5.  On the Listeners page, find the created HTTPS listener, and then click **More** \> **Domain Extensions**.

    ![](images/8773_en-US.png)

6.  Click **Add Domain Extension** and configure the domain name:
    1.   Enter the domain name. The domain name can only contain letters, numbers, dashes, or dots.

        Domain name forwarding rules support exact match and wildcard match.

        -   Exact domain name: www.aliyun.com
        -   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

            When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

            |Type|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:---|:----------|:--------------------------------|
            |:-------------|:------------|:-------------------|
            |Exact match|www.aliyun.com|✓|×|×|
            |Wildcard match|Market.aliyun.com|×|✓|×|
            |Wildcard match|info.market.aliyun.com|×|×|✓|

    2.  Select the certificate associated with the domain name.

        **Note:** The domain name in the certificate must be the same as the added domain name extension.

    3.  Click **Confirm**.

        ![](images/8792_en-US.png)

7.  On the Listeners page, find the created HTTPS listener and click **Add Forwarding Rules**.
8.  On the Add Forwarding Rules page, click **Add Forwarding Rules**.
9.  For more information, see [Add domain-name based or URL-based forwarding rules](reseller.en-US/User Guide/Listener/Layer-7 listeners/Add domain-name based or URL-based forwarding rules.md#).

    **Note:** Make sure that the domain name configured in the forwarding rule is the same as the added domain name extension.


## Edit a domain name extension {#section_fns_2qc_wdb .section}

You can replace the certificate used by an added domain name extension.

To edit a domain name extension, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select the target region and all SLB instance in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  In the left-side navigation pane, click Listeners.
5.  On the Listeners page, find the created HTTPS listener, and then click **More** \> **Domain Extensions**.
6.  Find the target domain name extension and then click **Edit**.
7.  In the Edit Domain Extension dialog box, select a new certificate and then click **Confirm**.

    ![](images/8795_en-US.png)


## Delete a domain name extension {#section_htc_j1p_42b .section}

To delete a domain name extension, complete these steps:

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb).
2.  Select the target region and all SLB instance in this region are displayed.
3.  Click the ID of the target SLB instance.
4.  In the left-side navigation pane, click Listeners.
5.  On the Listeners page, find the created HTTPS listener, and then click **More** \> **Domain Extensions**.
6.  Find the target domain name extension and then click **Remove**.
7.  In the displayed dialog box, click **Confirm**.

