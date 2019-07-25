# Add domain-name based or URL-based forwarding rules {#concept_sh5_nj5_vdb .concept}

SLB supports forwarding client request based on the domain name and request URL. You can forward client requests from different URLs to different backend servers by adding forwarding rules.

## Introduction to domain-name based or URL-based forwarding rules {#section_hll_n31_wdb .section}

Layer-7 listeners support configuring forwarding rules to distribute requests based on domain names or request URLs. You can add different forwarding rules associated with different VServer groups to a Layer-7 listener \(A VServer group consists of multiple ECS instances\). For example, you can forward all read requests to a group of backend servers and forward all write requests to another group of backend servers to optimize resource usage.

After forwarding rules are configured, the system will check whether a client request matches the configured forwarding rules:

-   If the client request matches a forwarding rule, the request will be forwarded to the VServer group specified in the forwarding rule.
-   If not, the request will be forwarded to the VServer group configured in the listener.
-   If none of the above conditions are met, the request will be forwarded to all the backend ECS instances added to the backend server pool.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/2798_en-US.png)

You do not need to configure health check settings for each forwarding rule. The following table shows how the health check is done with different configurations.

|Dimension|Health check configuration|The backend server where the health check is performed|
|:--------|:-------------------------|:-----------------------------------------------------|
|Backend servers|Use the health check configurations of the listener.|All the ECS instances.|
|VServer group|Use the health check configurations of the listener.|The ECS instances in the VServer group.|
|Forwarding rules|Use the health check configurations of the listener.|The ECS instances in the VServer group associated with the listener.|

**Note:** Because the port numbers of the backend servers are different in a server group, do not specify the health check port when a server group is used. Otherwise, the health check may fail due to inconsistent port numbers.

## Configurations of domain-name based or URL-based forwarding rules {#section_b4s_bj1_wdb .section}

You can configure forwarding rules based on the domain name, URL, or both:

-   Domain name only

    When configuring forwarding rules based on a domain name, omit the URL field. For the domain name, only letters, digits, dashes \(-\), and periods \(.\) are permitted.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/2801_en-US.png)

    The domain name supports both exact matching and wildcard matching. For example:

    -   Exact domain name: www.aliyun.com
    -   Wildcard domain name: \*.aliyun.com, \*.market.aliyun.com

        When a request matches multiple forwarding rules, the exact domain takes high priority.

        |Mode| Request URL|Domain name|
        |:---|:-----------|:----------|
        | | |www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
        |Exact match|www.aliyun.com|√| | |
        |Wildcard domain name match|market.aliyun.com| | | |
        |Wildcard domain name match|info.market.aliyun.com| | |√|

-   URL only

    When configuring forwarding rules based on the request path, omit the domain name field. Note the following rules when configuring a URL-based forwarding rule:

    -   Only letters, numbers and the following special characters are allowed:

        -. /%? \#&

    -   The URL must start with a slash \(/\), but cannot contain only one slash \(/\).

        **Note:** If only one slash \(/\) is entered, the URL based forwarding rule will not apply correctly.

    -   The URL forwarding supports string matching according to the string order.  For example /admin、/bbs、/test.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/2804_en-US.png)

-   Domain-name and URL-based forwarding

    If you want to forward traffic based on the same domain name, but different paths, you can configure a forwarding rule with both domain name and URL. We recommend further configuring a domain-only forwarding rule to avoid access errors due to no matching URLs.

    For example, there are two domain names: `www.aaa.com` and `www.bbb.com`. The requirement is to forward the requests from www.aaa.com/index.html to ServerGroup1 and forward other requests from xxx.html to ServerGroup2. You need to configure the following forwarding rules. If rule2 is absent, requests from `www.aaa.com` will get a 404 error.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/2807_en-US.png)


## Configure domain-name based or URL-based forwarding rules {#section_z1n_t1b_wdb .section}

Before adding forwarding rules, make sure:

-   You have created a Layer-7 \(HTTP/HTTPS\) listener. For more information, see [Layer-7 listeners](intl.en-US/User Guide/Listener/Listeners overview.md#).
-   You have created a VServer group.  For more information, see Create a [VServer group](intl.en-US/User Guide/Backend servers/Create a VServer group.md#).

To add a forwarding rule, complete these steps:

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-hangzhou).
2.  On the Instances page, select a region.
3.  Click the ID of the SLB instance.
4.  In the left-side navigation pane, click **Listeners**.
5.  Find the target HTTP/HTTPS listener, click **Add Forwarding Rules**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4135/6421_en-US.png)

6.  On the Forwarding Rules page, click **Add Forwarding Rules**.
7.  In the Add Forwarding Rules dialog box, configure rules and click **Confirm**.
8.  Click **Add Forwarding Rules +**to add another rule.

