# Obtain an Access Key {#task_iln_hyk_5gb .task}

This topic describes how to create an Access Key \(AK\) for your Alibaba Cloud account and RAM users. You need the AK for authentication to call API actions.

An AK consists of an AccessKeyId and AccessKeySecret.

-   An AccessKeyId is used to identify the user.
-   An AccessKeySecret is the key used to authenticate the user. AccessKeySecret must be kept secret.

**Warning:** Do not use the AK of your account because this provides full access to all your resources. Instead, we recommend that you create and authorize RAM users to access your resources to maintain account security.

1.  Log on to the [Alibaba Cloud console](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/) with your account credentials.
2.  Rest the pointer over the image in the upper-right corner of the page and click **AccessKey**.
3.  In the **Security Tips** dialog box, select **Continue to manage AccessKey** or **Get Started with Sub Users' AccessKey**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/156403446338859_en-US.png)

4.  Obtain an AK. 
    -   Obtain an AK for your account.
        1.  Click **Continue to manage AccessKey**.
        2.  On the Security Management page, click **Create AccessKey**.
        3.  On the Phone Verification page, obtain the verification code, complete the verification process, and click **Confirm**.
        4.  On the Create User AccessKey page, click **AccessKey Details** to view the AccessKeyId and AccessKeySecret. You can click **Save AccessKey Information** to download the AK.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/156403446338862_en-US.png)

    -   Obtain an AK for a RAM user
        1.  Click **Get Started with Sub Users' AccessKey**.
        2.  Go to the [RAM console](https://ram.console.aliyun.com/users/new) and create a RAM user on the Create User page. Skip this step if you have created a RAM user.
        3.  Go to the [RAM console](https://ram.console.aliyun.com/users/new) and in the left-side navigation pane, choose **Identities** \> **Users**.
        4.  Find the target RAM user and click the user logon name. Then, click the Authentication tab. In the Access Keys section, click **Create AccessKey**.
        5.  On the Phone Verification page, obtain the verification code, complete the verification process, and click **Confirm**.
        6.  On the Create AccessKey page, view the AccessKeyId and AccessKeySecret. To download or save the AK, click **Download CSV File** or **Copy**.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/156403446338866_en-US.png)


