Add DNS settings 
=====================================

Alibaba Cloud DNS is a distributed database that maps domain names to IP addresses. You can use Alibaba Cloud DNS to resolve a domain name to the public IP address of an SLB instance.

Context
-------

For example, the domain name of your website is www.aliyun.com and the website runs on an ECS instance that uses the public IP address 1.1.1.1. After you create an SLB instance, the public IP address 2.2.2.2 is allocated to the instance. You want to add the ECS instance where your website runs to the backend server pool and resolve the domain name www.aliyun.com to 2.2.2.2. We recommend that you use the A record to resolve the domain name to the IP address.

Procedure
---------

1. Log on to the [Alibaba Cloud DNS console](https://dns.console.aliyun.com/?spm=a2c4g.11186623.2.15.28ac30b0FUD0d8#/dns/domainList).

   

2. On the Domains tab, click **Add Domain Name** to add a domain name.

   

3. On the **Domains** tab, find the added domain name, click **Configure** in the **Actions** column, and complete the DNS settings.

   



