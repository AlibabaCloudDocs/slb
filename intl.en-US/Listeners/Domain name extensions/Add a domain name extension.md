# Add a domain name extension {#task_1580610 .task}

This topic describes how to add a domain name extension.

1.  Log on to the [Server Load Balancer console](https://partners-intl.console.aliyun.com/#/slb). 
2.  Select the region of the target SLB instance.
3.  Find the target SLB instance and click the instance ID.
4.  Click the **Listeners** tab.
5.  On the Listeners tab, find the target HTTPS listener, and choose **More** \> **Additional Domains** in the **Actions** column. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15661/15659396377466_en-US.png)

6.  Click **Add Additional Domain** and configure the domain name: 
    1.  Enter a domain name. The domain name can only contain letters, numbers, hyphens \(-\), and periods \(.\), and must start with a letter or a number. To check if the domain name you enter is valid, you can use the [Alibaba Cloud domain name check tool](https://zijian.aliyun.com). 

        Domain name-based forwarding rules support exact match and wildcard match.

        -   Exact domain name: www.aliyun.com
        -   Wildcard domain name \(generic domain name\): \*.aliyun.com, \*.market.aliyun.com

            When a request matches multiple forwarding rules, exact match takes precedence over small-scale wildcard match and small-scale wildcard match takes precedence over large-scale wildcard match, as shown in the following table.

            |Type|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:---|:----------|:--------------------------------|
            |:-------------|:------------|:-------------------|
            |Exact match|www.aliyun.com|✓|×|×|
            |Wildcard match|market.aliyun.com|×|✓|×|
            |Wildcard match|info.market.aliyun.com|×|×|✓|

    2.  Select the certificate associated with the domain name. 

        **Note:** The domain name in the certificate must be the same as the added domain name extension.

    3.  Click **OK**.
7.  On the Listeners tab, find the target HTTPS listener and click **Add Forwarding Rules** in the **Actions** column.
8.  On the Add Forwarding Rules page, configure the forwarding rule and click **Add Forwarding Rules**.
9.  For more information, see [Traffic forwarding based on domain names or URLs](../reseller.en-US/Tutorials/Traffic forwarding based on domain names or URLs.md#). 

    **Note:** Make sure that the domain name configured in the forwarding rule is the same as the added domain name extension.


**More information**  


[CreateDomainExtension](../reseller.en-US/Developer Guide/Domain name extensions (Beta)/CreateDomainExtension.md#)

