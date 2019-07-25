# Configure a whitelist {#task_lcm_kpc_f2b .task}

Whitelist is a method for access control. It applies to scenarios where an application only allows access from some specific IP addresses.

**Note:** SLB has released a new version of the access control function, which supports configuring whitelists and black lists. You can migrate the previously configured whitelist to the new version. For more information, see [Migrate to the new access control](intl.en-US/User Guide/Access control/Migrate to the new access control.md#).

Note the following when configuring whitelists:

-   Enabling whitelist poses some business risks. If a whitelist is configured, only the IP addresses in the list can access the listeners of the SLB instance.
-   If you enable the whitelist function without adding any IP entry in the corresponding access control list, no requests are forwarded.
-   When configuring a whitelist, the access to SLB listeners may be interrupted shortly.

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-beijing). 
2.  Select the region where the SLB instance is located. 
3.  Click the ID of the SLB instance. 
4.  In the left-side navigation pane, click **Listeners**. 
5.  Find the target listener, and then click **More** \> **Set Access Control**. 
6.  In the displayed dialog box, complete these steps: 
    1.  Click the **Enable Access Control** switch. 
    2.  Enter the IP addresses to allow to access the listener. Separate multiple IP addresses using comma. Up to 300 IP addresses are allowed. You can also enter CIDR blocks.
    3.  Click **Confirm**. 

