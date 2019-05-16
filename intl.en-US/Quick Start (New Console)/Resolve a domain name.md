# Resolve a domain name {#task_bh5_dll_vdb .task}

This topic describes Alibaba Cloud DNS. Alibaba Cloud DNS is a distributed database that maps domain names to IP addresses. You can use the DNS service to resolve a domain name to the public IP address of a Server Load Balancer \(SLB\) instance.

In this example, the domain name of your website is www.abc.com and the website runs on an ECS instance of which the public IP address is 1.1.1.1. An SLB instance is created and a public IP address 2.2.2.2 is allocated to the instance. You want to add the ECS instance hosting the website to the backend server pool and resolve the domain name www.abc.com to 2.2.2.2. We recommend that you add an A record resolution \(resolve a domain name to an IP address\).

1.  Log on to the [Alibaba Cloud DNS console](https://dc.console.aliyun.com/next/index?spm=5176.11783163.aliyun_sidebar.aliyun_sidebar_domain.2bc91eb9Ox2pHY#/domain/list/all-domain). 
2.  Click **Add Domain Name** to add a domain name. 
3.  On the Manage DNS page, find the added domain name, click **Configure** in the **Actions** column, and complete the DNS configuration. 

