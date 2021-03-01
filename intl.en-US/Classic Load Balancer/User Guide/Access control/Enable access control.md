# Enable access control

This topic describes how to enable access control for a listener. You can enable access control for each listener of a Classic Load Balancer \(CLB\). You can set whitelists or blacklists for different listeners to regulate network access control.

Before you enable access control, make sure that the following requirements are met:

-   A network ACL is created. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md).
-   A listener is created.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  Select the region where the CLB instance that you want to manage is created.

3.  Click the ID of the CLB instance.

4.  Click the **Listener** tab, find the listener that you want to manage, and then choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/8730954161/p97293.png)** \> **Set Access Control** in the **Actions** column.

5.  Set the following parameters and click **OK**.

    |Parameter|Description|
    |---------|-----------|
    |**Enable Access Control**|Turn on the switch to enable access control for the listener.|
    |**Access Control Method**|Select an access control method. Valid values:    -   **Whitelist**: After you set a whitelist for a listener, the listener forwards only requests from IP addresses or CIDR blocks that are added to the whitelist.

However, your business may be adversely affected if the whitelist is not set properly. After you set a whitelist for a CLB listener, only requests from IP addresses or CIDR blocks that are added to the whitelist are distributed by the listener. After you enable the whitelist, if no IP address is added to the whitelist, the listener does not forward requests.

    -   **Blacklist**: After you set a blacklist for a CLB listener, the listener blocks requests from IP addresses or CIDR blocks that are added to the blacklist.

After you enable a blacklist, if no IP address is added to the blacklist, the listener forwards all requests. |
    |**Access Control List**|Select a network ACL.IPv6 instances can be associated only with IPv6 network ACLs, and IPv4 instances can be associated only with IPv4 network ACLs.

**Note:** Separate multiple IP entries with commas \(,\). You can add up to 300 IP entries to each network ACL. IP entries must be unique within each network ACL. |


