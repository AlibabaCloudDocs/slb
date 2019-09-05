# Enable access control {#task_1597735 .task}

Server Load Balancer \(SLB\) provides an access control function for listeners. You can configure different whitelists or blacklists for different listeners.

Before you enable access control, make sure:

-   An access control list is created. For more information, see [Configure an access control list](reseller.en-US/Archives/User Guide (Old Console)/Access control/Configure an access control list.md#).
-   A listener is created.

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  Select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  On the Instance Details page, click the **Listeners** tab.
5.  Find the target listener, choose **More** \> **Set Access Control**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15686/15676506647481_en-US.png)

6.  On the Access Control Settings page, enable access control, select an access control method and an access control list, and click **OK**. 

    -   **Whitelist**: Only requests from IP addresses or CIDR blocks in the selected access control list are forwarded. It applies to scenarios where the application only allows access from some specific IP addresses.

        Enabling a whitelist poses some risks to your services. After a whitelist is configured, only the IP addresses in the list can access the listener. If you enable the whitelist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

    -   **Blacklist**: Requests from IP addresses or CIDR blocks in the selected access control list are not forwarded. It applies to scenarios where the application only denies access from some specific IP addresses.

        If you enable a blacklist without adding any IP addresses in the corresponding access control list, all requests are forwarded.

    **Note:** The access control function works only for new connection requests and does not affect existing connections.


