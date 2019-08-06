# Authorize a RAM user to configure access logs {#task_kdv_g4n_vdb .task}

Before a RAM user starts to use the access logging function, the RAM user must be authorized by the primary account.

1.  Create an authorization policy: 
    1.  Use the primary account to log on to the RAM console. 
    2.  In the left-side navigation pane, click **Policies**, and then click **Create Authorization Policy**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2509_en-US.png)

    3.  Click **Blank Template**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2510_en-US.png)

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

    1.  Click **Close**. 
2.  Attach the created policy to a RAM user 
    1.  In the left-side navigation pane, click **Users**. 
    2.  Find the target user \(the user who uses the SLB Access Log function\) and click **Authorize**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2512_en-US.png)

    3.  Search the created authorization policy and attach the policy to the RAM user. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2513_en-US.png)

    4.  Click **OK**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2514_en-US.png)

    5.  Go to the User Authorization Policies page to check if the policy has been attached to target RAM user. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4151/2515_en-US.png)


