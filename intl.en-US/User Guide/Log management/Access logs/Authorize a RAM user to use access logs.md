# Authorize a RAM user to use access logs

Before a RAM user uses the access log function, the RAM user must be authorized by the corresponding Alibaba Cloud account.

The account has enabled the access log function.

1.  Log on to the RAM console by using the credentials of your account.
2.  Click **Roles** to see whether the account has the **AliyunLogArchiveRole**.

    If the account does not have this role, log on to the SLB console by using the credentials of the account, select **Logs** \> **Access Logs**, click **Authorize**. In the displayed dialog box, click **Confirm Authorization Policy**.

    **Note:** This operation is required only at the first time.


1.  Create an authorization policy:

    1.  Log on to the RAM console by using the credentials of your account.

    2.  In the left-side navigation pane, click **Policies**, and then click **Create Authorization Policy**.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/0735651851/p2509.png)

    3.  Click **Blank Template**.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1735651851/p2510.png)

    4.  Enter a policy name, such as **SlbAccessLogPolicySet**, and then enter the following policy. Click **Create Authorization Policy**.

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

    5.  Click **Close**.

2.  Attach the created policy to the RAM user:

    1.  In the left-side navigation pane, click **Users**.

    2.  Find the target RAM user \(the user who uses the SLB access log function\) and click **Authorize**.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1735651851/p2512.png)

    3.  Search the created authorization policy and attach the policy to the RAM user.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1735651851/p2513.png)

    4.  Click **OK**.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1735651851/p2514.png)

    5.  Go back to the user details page to check whether the policy has been attached to the target RAM user.

        ![](https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/en-US/1735651851/p2515.png)


