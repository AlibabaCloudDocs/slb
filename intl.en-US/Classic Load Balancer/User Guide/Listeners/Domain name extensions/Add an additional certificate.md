# Add an additional certificate

This topic describes how to add an additional certificate to a listener of an SLB instance.

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **Instances** \> **Instances**.

3.  On the Instances page, find the SLB instance to which you want to add an additional certificate and click its instance ID.

4.  On the page that appears, click the **Listener** tab. On the Listener tab, find the HTTPS listener you create, and choose **![More](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/1919031161/p230808.png)** \> **Manage Additional Certificate** in the Actions column.

5.  In the Manage Additional Certificate panel, click **Add Additional Certificate**.

    1.  Enter a domain name. A domain can contain only letters, digits, hyphens \(-\), and periods \(.\), and must start with a letter or a digit. To check whether the domain is valid, use the [domain detection tool](https://zijian.aliyun.com).

        Domain name-based forwarding rules include exact matching and wildcard matching.

        -   Exact domain name: www.aliyun.com
        -   Wildcard domain name: \*.aliyun.com and \*.market.aliyun.com

            When a request matches multiple forwarding rules, exact matching prevails over exact wildcard matching, and exact wildcard matching prevails over less exact wildcard matching. The following table describes the priority of domain name-based forwarding rules.

            |Mode|Request URL|Domain name-based forwarding rule|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:---|:----------|:--------------------------------|
            |:-------------|:------------|:-------------------|
            |Exact matching|www.aliyun.com|✓|×|×|
            |Exact wildcard matching|market.aliyun.com|×|✓|×|
            |Less exact wildcard matching|info.market.aliyun.com|×|×|✓|

    2.  Select the certificate associated with the domain name.

        **Note:** The domain name in the certificate must be the same as the added additional certificate.

    3.  Click **OK**.

        An additional certificate takes effect only when it is configured with a forwarding rule and the domain name specified in the rule is the same as that in the additional certificate.

6.  If no forwarding rules are configured, click **Configure Rule** in the **Information** dialog box, or go to the **Listener** tab of the instance,

7.  find the HTTPS listener, and click **Add Forwarding Rules** in the corresponding Actions column.

8.  In the Add Forwarding Rules panel, click **Add Forwarding Rules**

9.  Configure forwarding rules. For more information, see [Forward requests based on domain names or URLs](/intl.en-US/Tutorials/Forward requests based on domain names or URLs.md).

    **Note:** Make sure that the domain name configured in the forwarding rule is the same as the added additional certificate.


**Related topics**  


[CreateDomainExtension](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Domain name extensions (Beta)/CreateDomainExtension.md)

