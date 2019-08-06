# 从负载均衡服务中移除ECS实例 {#concept_mhh_xj5_vdb .concept}

直接从后端服务器池中移除ECS实例可能会造成业务中断，建议您先将ECS的权重设置为零后，再移除。

## 移除ECS实例 {#section_ed4_qbw_wdb .section}

直接将ECS实例从负载均衡实例中移除，可能会造成业务闪断。建议您按照以下步骤移除ECS实例：

1.  登录[负载均衡管理控制台](https://slbnew.console.aliyun.com/?spm=5176.2020520101.1002.d10slb.EUrBxg#/list/cn-hangzhou)。
2.  单击负载均衡实例的ID链接，进入实例详情页。
3.  在详情左侧导航栏，单击**服务器** \> **后端服务器**。

    如果您的ECS实例在虚拟服务器组或主备服务器组内，则选择对应的服务器组。

4.  将鼠标移至要移除的ECS实例的权重区域，单击出现的铅笔图标，然后将权重修改为0。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821503124_zh-CN.png)

5.  当负载均衡服务不再转发流量给该ECS实例后，单击**移除**。

## 流量排查 {#section_ukg_5cw_wdb .section}

把ECS从负载均衡实例中移除后，发现还有持续的业务请求，可以从以下两个方面排查。

-   查看该ECS是否加入了其他的负载均衡实例中。

    登录负载均衡管理控制台，可以根据ECS实例ID和内网IP查询该ECS实例所属的负载均衡实例。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821503126_zh-CN.png)

-   登录ECS实例，用`netstat`命令查看服务器端口监听情况。根据端口监听情况查看ECS本身是否对公网提供了其他服务。
    -   Windows： 运行`netstat -ano`，可以查看本机开放的全部端口。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821503130_zh-CN.png)

    -   Linux： 也可以使用该命令查看本机开放端口，或使用`netstat`命令的其他参数。

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4166/15421821503131_zh-CN.png)


