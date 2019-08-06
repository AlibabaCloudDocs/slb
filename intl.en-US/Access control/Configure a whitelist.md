# Configure a whitelist {#task_lcm_kpc_f2b .task}

Whitelist is a method used to control the access of Server Load Balancer. It applies to scenarios where an application only allows access from some specific IP addresses.

**Note:** SLB has released a new version of the access control function, allowing you to configure both whitelists and blacklists. You can migrate the previously configured whitelist to the new version. For more information, see [Migrate to the new access control](reseller.en-US/User Guide/Access control/Migrate to the new access control.md#).

Note the following when configuring whitelists:

-   Enabling whitelist poses some business risks. After a whitelist is configured, only the IP addresses in the list can access the listener.
-   If you enable the whitelist function without adding any IP entry in the corresponding access control list, no requests are forwarded.
-   When you configure a whitelist, the access to Server Load Balancer may be interrupted for a short time.

1.  Log on to the [SLB console](https://partners-intl.aliyun.com/login-required#/slb). 
2.  Select the region where the target SLB instance is located. 
3.  Click the ID of the target SLB instance. 
4.  In the Listeners tab, select **More** \> **Set Access Control**. 
5.  In the displayed dialog box, configure as follows: 
    1.  Click the **Enable Access Control** switch. 
    2.  Enter the IP addresses that are allowed to access the listener. Separate multiple IP addresses using comma. Up to 300 IP addresses are allowed. You can also enter CIDR blocks.
    3.  Click **OK**. 

