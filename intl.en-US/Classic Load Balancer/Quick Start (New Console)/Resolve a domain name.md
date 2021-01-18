Resolve a domain name 
==========================================

This topic describes Alibaba Cloud DNS. Alibaba Cloud DNS is a distributed database that maps domain names to IP addresses. You can use the DNS service to resolve a domain name to the public IP address of a Server Load Balancer (SLB) instance.

Context
-------

In this example, the domain name of your website is www.aliyun.com and the website runs on an ECS instance of which the public IP address is 1.1.1.1. An SLB instance is created and a public IP address 2.2.2.2 is allocated to the instance. You want to add the ECS instance hosting the website to the backend server pool and resolve the domain name www.aliyun.com to 2.2.2.2. We recommend that you add an **A record resolution** (resolve a domain name to an IP address).

Procedure
---------

1. Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/?spm=a2c4g.11186623.2.15.28ac30b0FUD0d8#/dns/domainList).

   

2. Click **Add Domain Name** to add a domain name.

   

3. On the **Manage DNS** page, find the added domain name, click **Configure** in the **Actions** column, and complete the DNS configuration.

   



