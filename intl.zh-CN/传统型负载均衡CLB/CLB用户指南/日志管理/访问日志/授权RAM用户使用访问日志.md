# 授权RAM用户使用访问日志

RAM用户使用负载均衡访问日志功能前，需要阿里云账号对其进行授权。

阿里云账号已开通日志访问功能。

1.  以阿里云账号登录[RAM访问控制台](https://ram.console.aliyun.com/overview)。
2.  单击**RAM角色管理**，查看阿里云账号是否具有负载均衡日志访问角色**AliyunLogArchiveRole**。

    如果没有该角色权限，请以阿里云账号登录负载均衡控制台，选择**日志管理** \> **访问日志** ，单击**立即授权**，然后在弹出的对话框，单击**同意授权**，授权SLB访问日志服务。

    **说明：** 该操作只有首次配置时需要。


1.  创建授权策略：

    1.  使用阿里云账号登录访问控制RAM控制台。

    2.  在左侧导航栏，单击**权限策略管理**，然后单击**创建权限策略**。

    3.  输入策略名称，如**SlbAccessLogPolicySet**。

    4.  选择配置模式为`%脚本配置;`，输入以下策略内容。

        ```
        {
        "Statement": [
         {
           "Action": [
             "slb:Create*",
             "slb:List*"
           ],
           "Effect": "Allow",
           "Resource": "acs:log:*:*:project/*"
         },
         {
           "Action": [
             "log:Create*",
             "log:List*"
           ],
           "Effect": "Allow",
           "Resource": "acs:log:*:*:project/*"
         },
         {
           "Action": [
             "log:Create*",
             "log:List*",
             "log:Get*",
             "log:Update*"
           ],
           "Effect": "Allow",
           "Resource": "acs:log:*:*:project/*/logstore/*"
         },
         {
           "Action": [
             "log:Create*",
             "log:List*",
             "log:Get*",
             "log:Update*"
           ],
           "Effect": "Allow",
           "Resource": "acs:log:*:*:project/*/dashboard/*"
         },
         {
           "Action": "cms:QueryMetric*",
           "Resource": "*",
           "Effect": "Allow"
         },
         {
           "Action": [
             "slb:Describe*",
             "slb:DeleteAccessLogsDownloadAttribute",
             "slb:SetAccessLogsDownloadAttribute",
             "slb:DescribeAccessLogsDownloadAttribute"
           ],
           "Resource": "*",
           "Effect": "Allow"
         },
         {
           "Action": [
             "ram:Get*",
             "ram:ListRoles"
           ],
           "Effect": "Allow",
           "Resource": "*"
         }
        ],
        "Version": "1"
        }
        ```

    5.  单击**确定**。

2.  给RAM用户授权：

    1.  在访问控制RAM控制台，选择**授权** \> **新增授权**。

        ![新增授权](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6061004161/p241803.png)

    2.  选择授权范围和被授权主体。

        ![授权](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/zh-CN/6061004161/p241784.png)

    3.  在权限策略名称列表中选择相应的权限策略。

    4.  单击**确定**。

    5.  返回**授权**页面，确认该用户已具有新建的权限策略，则可以使用负载均衡日志访问功能。


