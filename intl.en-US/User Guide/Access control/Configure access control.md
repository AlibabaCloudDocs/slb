# Configure access control {#concept_f1l_pzb_wdb .concept}

Server Load Balancer \(SLB\) provides an access control function for listeners. You can configure different whitelists or blacklists for different listeners.

You can configure access control when you create a listener or change access control configurations after a listener is created.

This topic describes how to configure access control after a listener is created.

## Enable access control {#section_ync_c1c_wdb .section}

Before you enable access control, make sure:

-   An access control list is created. For more information, see [Configure an access control list](intl.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).
-   A listener is created.

To enable access control, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Locate the target SLB instance and click the instance ID.
4.  On the Instance Details page, click the **Listeners** tab.
5.  Locate the target listener, and then choose **More** \> **Set Access Control**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15686/15597279257481_en-US.png)

6.  On the Access Control Settings page, enable access control, select an access control method and an access control list, and click **OK**.
    -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

        Enabling a whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP addresses in the corresponding access control list, no requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control list are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

        If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.


## Disable access control {#section_amn_q1c_wdb .section}

To disable access control, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select the region of the target SLB instance.
3.  Locate the target SLB instance and click the instance ID.
4.  On the Instance Details page, click the Listeners tab.
5.  Locate the target listener, and then click **More** \> **Set Access Control**.
6.  On the Access Control Settings page, disable access control and click **OK**.

