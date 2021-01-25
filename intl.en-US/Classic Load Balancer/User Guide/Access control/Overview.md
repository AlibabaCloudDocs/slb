# Overview

This topic describes how to enable access control for listeners of Server Load Balancer \(SLB\). You can configure access control when you create a listener or modify access control settings for created listeners.

## Access control list

You can set the access control list to whitelist or blacklist for a listener.

-   Whitelist: The listener forwards only requests from IP addresses or CIDR blocks in the selected access control list. Use this list to allow only specified IP addresses to access your service.

    The whitelist poses risks to your services. If you set the whitelist without adding any IP addresses to the selected access control list, the SLB listener does not forward any request.

-   Blacklist: The listeners blocks only requests from IP addresses or CIDR blocks in the selected access control list. Use this list to forbid specified IP addresses to access your service.

    If you set the blacklist without adding any IP addresses to the selected access control list, the SLB listener forwards all requests.


## Limits

-   You can bind one or more access control lists to each SLB listener. By default, you can bind up to three access control lists to a listener in one of the following regions. You can bind only one access control list to a listener in a region that is not specified in the following list.
    -   India \(Mumbai\)
    -   Indonesia \(Jakarta\)
    -   Japan \(Tokyo\)
    -   Germany \(Frankfurt\)
    -   Australia \(Sydney\)
    -   Malaysia \(Kuala Lumpur\)
    -   UK \(London\)
-   You can bind only IPv4 access control lists to IPv4 SLB instances and only IPv6 access control lists to IPv6 SLB instances.
-   The total sum of entries added to access control lists that are bound to the same listener must not exceed 1,000.
-   An access control list can be bound to up to 50 listeners.
-   The IP addresses in access control lists that are bound to the same listener must be unique.

## Procedure

The following figure shows how to configure access control for listeners.

![Procedure](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5999351161/p231734.png)

To configure access control for a listener, follow these steps:

-   Create an access control list and add IP addresses or CIDR blocks to the list. For more information, see [Create an access control list](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Create an access control list.md) and [Add IP entries](/intl.en-US/Classic Load Balancer/User Guide/Access control/Access control lists/Add IP entries.md).
-   Enable access control for the listener. For more information, see [Enable access control](/intl.en-US/Classic Load Balancer/User Guide/Access control/Enable access control.md).
-   You can disable access control in the listener configuration. For more information, see [Disable access control](/intl.en-US/Classic Load Balancer/User Guide/Access control/Disable access control.md).

