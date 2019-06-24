# 单SLB实例配置多域名HTTPS网站 {#concept_rks_s4t_q2b .concept}

本教程介绍配置扩展域名的详细操作步骤。

## 场景描述 {#section_eqs_54t_q2b .section}

本教程以华东1（杭州）地域的性能保障型负载均衡实例SLB1为例。在本教程中您会创建一个七层HTTPS监听，认证方式为单向认证，您需要将来自域名为\*.example1.com的前端请求转发至虚拟服务器组test1上，将来自域名为www.example2.com的前端请求转发至虚拟服务器组test2上。

您需要完成以下操作：

1.  添加HTTPS监听。
2.  配置转发规则。
3.  添加扩展域名。

## 前提条件 {#section_krq_z4t_q2b .section}

-   在华东1（杭州）地域创建性能保障型实例SLB1，具体操作请参见[创建负载均衡实例](../intl.zh-CN/用户指南/负载均衡实例/创建负载均衡实例.md#)。
-   上传本教程中需要使用的证书，具体操作请参见[创建证书](../intl.zh-CN/用户指南/证书管理/创建证书.md#)。

    -   监听使用的默认证书为default。
    -   域名\*.example1.com使用的证书为example1。
    -   域名www.example2.com使用的证书为example2。
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15661/15613552438320_zh-CN.png)


## 步骤一 添加HTTPS监听 {#section_s3n_qpt_q2b .section}

完成以下操作，添加七层HTTPS监听：

1.  在左侧导航栏，选择**实例** \> **实例管理**。
2.  在实例管理页面，单击性能保障型实例SLB1**操作**列的**监听配置向导**。

    首次配置监听，也可以单击**端口/健康检查/后端服务器**列的**点我开始配置**。

3.  配置监听。

    本操作的主要配置如下，其他配置参考[添加HTTPS监听](../intl.zh-CN/用户指南/监听/添加HTTPS监听.md#)。

    -   双向认证：关闭。
    -   SSL证书：选择服务器证书default。
    -   后端服务器：需要创建test1和test2两个虚拟服务器组。

## 步骤二 配置转发规则 {#section_dxm_2qt_q2b .section}

完成以下操作，配置转发规则：

1.  单击SLB1实例ID，进入实例详情页面。
2.  在监听页签下，找到已创建的HTTPS监听，单击**添加转发策略**。
3.  在转发策略页面，配置转发策略，详情请参见[基于域名/URL路径进行转发](../intl.zh-CN/教程专区/基于域名__URL路径进行转发.md#)。

    本教程中配置域名转发规则，URL不进行设置。

    -   设置规则名称，在**域名**操作列输入\*.example1.com，选择test1虚拟服务器组，单击**添加转发策略 +**。
    -   设置规则名称，在**域名**操作列输入www.example2.com，选择test2虚拟服务器组，单击**确认**。
    **说明：** 转发规则中设置的域名，必须与证书中和[步骤三 添加扩展域名](../intl.zh-CN/教程专区/单SLB实例配置多域名HTTPS网站.md#section_bk4_ypt_q2b)中添加的扩展域名保持一致。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17005/15613552438327_zh-CN.png)


## 步骤三 添加扩展域名 {#section_bk4_ypt_q2b .section}

完成以下操作，添加扩展域名：

1.  单击SLB1实例ID，进入实例详情页面。
2.  在监听页签下，找到已创建的HTTPS监听，选择**更多** \> **扩展域名管理**。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17020/156135524310044_zh-CN.png)

3.  在扩展域名管理页面，单击**添加扩展域名**，配置扩展域名。

    -   输入域名。域名只能使用字母、数字、连字符（-）、点（.）。

        域名转发策略支持精确匹配和通配符匹配两种模式：

        -   精确域名：www.aliyun.com
        -   通配符域名（泛域名）: \*.aliyun.com, \*.market.aliyun.com

            当前端请求同时匹配多条域名策略时，策略的匹配优先级为：精确匹配高于小范围通配符匹配， 小范围通配符匹配高于大范围通配符匹配，如下表所示。

            |模式|请求测试URL|配置的转发域名策略|
|www.aliyun.com|\*.aliyun.com|\*.market.aliyun.com|
            |:-|:------|:--------|
            |:-------------|:------------|:-------------------|
            |精确匹配|www.aliyun.com|✓|×|×|
            |泛域名匹配|market.aliyun.com|×|✓|×|
            |泛域名匹配|info.market.aliyun.com|×|×|✓|

    -   选择该域名关联的证书。

        **说明：** 证书中的域名和您添加的扩展域名必须一致。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17005/15613552438324_zh-CN.png)


**说明：** 配置完成后，如果出现问题，请尝试重启浏览器后再测试，避免缓存对结果的影响。

