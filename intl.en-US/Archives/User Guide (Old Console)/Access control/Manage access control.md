# Manage access control {#concept_f1l_pzb_wdb .concept}

SLB provides you with the access control function. You can configure different whitelists or blacklists for different listeners.

You can configure access control when addling listeners. For more information, see [Configure a Layer-7 listener](intl.en-US/User Guide/Listener/Layer-7 listeners/Layer-7 listener configurations.md#) and [Configure a layer-4 listener](intl.en-US/User Guide/Listener/Layer-4 SLB Listener./Configure Layer-4 SLB listeners.md#). You can also modify or configure access control after the listener is created.

This document introduces how to configure access control after a listener is created.

## Enable access control {#section_ync_c1c_wdb .section}

Before enabling access control, make sure:

-   You have created an access control list. For more information, see [Configure an access control list](intl.en-US/User Guide/Access control/Configure an access control list.md#).
-   You have created a listener.

To enable access control, complete these steps:

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-beijing).
2.  Select the region where the SLB instance is located.
3.  Click the ID of the target SLB instance.
4.  In the left-side navigation pane, click **Listeners**.
5.  On the Listeners page, click **More** \> **Set Access Control** in the **Actions** column.
6.  In the displayed dialog box, enable access control, select an access control method and an access control list. Click **Confirm**.
    -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control lists are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

        Enabling whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP entry in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control lists are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

        If you enable a blacklist without adding any IP entry in the corresponding access control list, all requests are forwarded.


## Disable access control {#section_amn_q1c_wdb .section}

To disable access control, complete these steps:

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-beijing).
2.  Select the region where the SLB instance is located.
3.  Click the ID of the target SLB instance.
4.  In the left-side navigation pane, click **Listeners**.
5.  On the Listeners page, click **More** \> **Set Access Control** in the **Actions** column.
6.  In the displayed dialog box, disable access control.

