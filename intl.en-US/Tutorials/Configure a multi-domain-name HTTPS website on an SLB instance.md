# Configure a multi-domain-name HTTPS website on an SLB instance {#concept_rks_s4t_q2b .concept}

This tutorial introduces how to configure a domain name extension.

## Scenario {#section_eqs_54t_q2b .section}

This tutorial uses a guaranteed-performance SLB instance \(SLB1\) in the China \(Hangzhou\) region as an example. An HTTPS listener with one-way authentication is added to the SLB instance. You want to forward requests from the domain name \*.example1.com to the VServer group test1 and forward requests from the domain name www.example2.com to the VServer group test2.

To achieve this, follow these steps:

1.  Add an HTTPS listener.
2.  Configure forwarding rules.
3.  Add a domain name extension.

## Prerequisites {#section_krq_z4t_q2b .section}

-   Create a guaranteed-performance SLB instance \(SLB1\) in China \(Hangzhou\). For more information, see [Create an SLB instance](../../../../reseller.en-US/User Guide/Server Load Balancer instance/Create an SLB instance.md#).
-   Upload the certificate required in this tutorial. For more information, see [Create a certificate](../../../../reseller.en-US/User Guide/证书管理/Create a certificate.md#).

    -   By default, the listener uses the certificate named as default.
    -   Upload a certificate \(example1\) for domain name \* .example1.com to use.
    -   Upload a certificate \(example2\) for domain name www.example2.com to use.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17020/155905383545105_en-US.png)


## Step 1 Add an HTTPS listener {#section_s3n_qpt_q2b .section}

To add an HTTPS listener, follow these steps:

1.  In the left-side navigation pane, click **Instances** \> **Server Load Balancer**.
2.  On the Server Load Balancer page, locate the target instance SLB1 and click **Configure Listener** in the **Actions** column.

    If it is the first time you configure the listener, you can also click **Configure** in the **Port/Health Check/Backend Server** column.

3.  Configure the listener.

    The configurations used in this tutorial are as follows. For more information, see [Add an HTTPS listener](../../../../reseller.en-US/User Guide/Listeners/Add an HTTPS listener.md#).

    -   Mutual Authentication: Disable.
    -   SSL Certificate: Select the uploaded server certificate.
    -   Backend Servers: Create VServer groups test1 and test2.

## Step 2 Configure forwarding rules {#section_dxm_2qt_q2b .section}

To configure forwarding rules, follow these steps:

1.  Click the ID of the instance SLB1.
2.  On the Listeners tab, find the created HTTPS listener and click **Add Forwarding Rules**.
3.  On the Add Forwarding Rules page, configure forwarding rules. For more information, see [Add domain-name based or URL-based forwarding rules](../../../../reseller.en-US/Tutorials/Traffic forwarding based on domain name or URL.md#).

    In this tutorial, three domain name-based forwarding rules are configured and URLs are left empty.

    -   Set a rule name, and then enter \* .example1.com in the **Domain Name** column, select the VServer group test1 and click **Add Forwarding Rules**.
    -   Set a rule name, and then enter www.example2.com in the **Domain Name** column, select the VServer group test2 and click **OK**.
    **Note:** The domain names configured in the forwarding rules must be the same as the domain names added in the certificate and [Step 3. Add a domain name extension](../../../../reseller.en-US/Tutorials/Configure a multi-domain-name HTTPS website on an SLB instance.md#section_bk4_ypt_q2b).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17020/155905383511911_en-US.png)


## Step 3 Add a domain name extension {#section_bk4_ypt_q2b .section}

To add a domain name extension, follow these steps:

1.  Click the ID of the instance SLB1.
2.  On the Listeners tab, find the created HTTPS listener, choose **More** \> **Additional Domains**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17020/155905383510044_en-US.png)

3.  On the Additional Domains page, click **Add Additional Domain** to add a domain name extension.

    -   Enter a domain name. The domain name can only contain letters, numbers, hyphens \(-\), or periods \(.\).

        Domain name-based forwarding rules support exact match and wildcard match.

        -   Exact domain name: www.aliyun.com
        -   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

            When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

            |Type|Request URL|Domain name based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:---|:----------|:--------------------------------|
            |:-------------|:------------|:-------------------|
            |Exact match|www.aliyun.com|✓|×|×|
            |Wildcard match|market.aliyun.com|×|✓|×|
            |Wildcard match|info.market.aliyun.com|×|×|✓|

    -   Select the certificate associated with the domain name.

        **Note:** The domain name in the certificate must be the same as the added domain name extension.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17020/155905383511910_en-US.png)


**Note:** After the configuration is complete, if there is a problem, restart the browser to avoid the impact of the cache on the results.

