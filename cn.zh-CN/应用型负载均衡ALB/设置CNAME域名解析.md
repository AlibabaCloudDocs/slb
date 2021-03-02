---
keyword: [域名解析, CNAME, 应用型负载均衡]
---

# 设置CNAME域名解析

CNAME域名解析即别名记录，当您需要将域名指向另一个域名，再由另一个域名提供IP地址时，就需要添加CNAME记录。阿里云应用型负载均衡ALB支持将您拥有的常用域名通过CNAME方式解析到ALB实例的公网服务域名上，使您可以更加方便地访问各种网络资源。

## 负载均衡SLB相关的域名解析方式简介

最常见的两种域名解析方式为A记录域名解析和CNAME域名解析。ALB对外提供域名，只支持CNAME域名解析。

-   **A记录域名解析**

    A记录域名解析又称IP指向，您可以设置子域名并指向到自己的目标主机IP上，从而实现通过域名找到指定IP。传统型负载均衡CLB默认对外提供公网IP访问，如需通过域名访问主机，可以配置A记录域名解析，具体实现方案如下图所示：

    ![A记录解析](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4030564161/p243954.png)

-   **CNAME域名解析**

    CNAME域名解析又称别名解析，您可以设置子域名并指向到其他域名，从而实现将一个域名指向另一个域名。应用型负载均衡ALB默认对外提供域名访问，如果通过其他域名访问请配置CNAME域名解析，具体实现方案如下图所示：

    ![CNAME解析](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/4030564161/p243959.png)


## 前提条件

已创建了ALB实例，具体操作，请参见[创建实例](/cn.zh-CN/应用型负载均衡ALB/ALB实例/创建实例.md)。

## ALB配置CNAME域名解析

1.  登录[应用型负载均衡控制台](https://slb.console.aliyun.com/alb/cn-hangzhou/albs)。

2.  在顶部菜单栏选择地域。

3.  选择要进行域名解析的ALB实例，复制其对应的DNS名称。

    ![复制DNS地址](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6835434161/p243960.png)

4.  完成以下步骤来添加CNAME解析记录。

    1.  登录[域名解析控制台](https://dns.console.aliyun.com/#/dns/domainList)。

    2.  在**域名解析**页面单击**添加域名**。

    3.  在**添加域名**对话框中输入您的主机域名，然后单击**确定**。

        **说明：** 您的主机域名需已完成TXT记录验证。

    4.  在目标域名的**操作**列单击**解析设置**。

    5.  在**解析设置**页面单击**添加记录**。

    6.  在**添加记录**面板配置以下信息完成CNAME解析配置，然后单击**确认**。

        |配置|说明|
        |--|--|
        |**记录类型**|在下拉列表中选择CNAME。|
        |**主机记录**|您的域名的前缀。|
        |**解析线路**|选择默认。|
        |**记录值**|输入加速域名对应的CNAME地址，即您复制的ALB实例的DNS名称。|
        |**TTL**|全称Time To Live，表示DNS记录在DNS服务器上缓存时间，本文使用默认值。|

        **说明：**

        -   新增CNAME记录实时生效，修改CNAME记录取决于本地DNS缓存的解析记录的TTL到期时间，一般默认为10分钟。
        -   添加时如遇添加冲突，请换一个解析域名。更多信息，请参见[解析记录互斥规则](https://help.aliyun.com/knowledge_detail/39787.html)

验证CNAME配置是否生效：在命令行中`ping`或`dig`您的自定义域名，如果被转向ALB实例的DNS名称，即表示CNAME配置已生效。

