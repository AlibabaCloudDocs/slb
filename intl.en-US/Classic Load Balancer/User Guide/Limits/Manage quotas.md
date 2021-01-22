# Manage quotas

This topic describes how to query the quota usage of a cloud resource in the Server Load Balancer \(SLB\) console. If the remaining quota of a resource cannot meet your business requirements, you can apply for a quota increase.

## Apply for a quota increase

1.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb).

2.  In the left-side navigation pane, choose **SLB Lab** \> **Quota Management**.

3.  On the Quota Management page, you can view the usage of the SLB resources and the privileges of your account.

4.  To apply for a quota increase, click **Submit Application** in the **Actions** column.

    -   **Requested Value**: the number of resources that you require. The number must be greater than the current quota. For more information about the quotas of SLB resources, see [Limits](/intl.en-US/Classic Load Balancer/User Guide/Limits/Limits.md).
    -   **Reason**: the reasons for the application, including business scenarios and necessity.
    -   **Email**: the email address of the applicant.
    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/7231446951/p38136.png)

5.  Click **OK**.

    The system reviews your application. You can check whether your application is approved based on the application status: **Rejected** or **Approved**. After your application is approved, the quota is raised to the specified quantity.

    You can click **History** in the **Actions** column to view the application history.


## What do I do if the number of instances is insufficient?

If you need more guaranteed-performance instances but the number of instances has reached the quota, you can apply for a quota increase.

1.  Click **Submit Application** in the Actions column corresponding to the **slb\_privilege\_allow\_more\_guaranteed\_performance\_instances** privilege.


This privilege allows you to apply for more guaranteed-performance instances, but you cannot apply for more shared-performance instances.

