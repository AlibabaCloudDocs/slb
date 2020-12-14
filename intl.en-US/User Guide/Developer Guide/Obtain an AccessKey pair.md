# Obtain an AccessKey pair

This topic describes how to create an AccessKey pair for your Alibaba Cloud account or Resource Access Management \(RAM\) user. When you call Alibaba Cloud Server Load Balancer \(SLB\) API operations, SLB uses your AccessKey pair to verify your identity.

An AccessKey pair consists of an AccessKey ID and an AccessKey secret.

-   The AccessKey ID is used to verify the identity of the user.
-   The AccessKey secret is used to encrypt and verify the signature string. You must keep your AccessKey secret confidential.

**Warning:** If the AccessKey pair of your Alibaba Cloud account is disclosed, your resources may be exposed to potential risks. We recommend that you use the AccessKey pair of a RAM user to call API operations. This minimizes the risks of disclosing the AccessKey pair of your Alibaba Cloud account.

1.  Log on to the [Alibaba Cloud Management Console](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/) with your Alibaba Cloud account.

2.  Move the pointer over your account avatar in the upper-right corner and click **AccessKey Management**.

3.  In the **Note** dialog box, click Use Current AccessKey Pair or Use AccessKey Pair of RAM User.

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9364943851/p38859.png)

4.  Obtain the AccessKey pair of an account.

    -   Obtain the AccessKey pair of your Alibaba Cloud account.
        1.  Click **Use Current AccessKey Pair**.
        2.  On the AccessKey Management page, click **Create AccessKey**.
        3.  In the Phone Verification dialog box, obtain the verification code, complete the verification process, and then click **OK**.
        4.  In the Create User AccessKey dialog box, view the AccessKey ID and AccessKey secret.**** You can click **Download CSV File** to download the AccessKey pair.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9364943851/p38862.png)

    -   Obtain the AccessKey pair of a RAM user.
        1.  Click **Use AccessKey Pair of RAM User**.
        2.  Go to the [RAM console](https://ram.console.aliyun.com/users/new). On the Create User page, create a RAM user. If you want to obtain the AccessKey pair of an existing RAM user, skip this step.
        3.  In the left-side navigation pane of the [RAM console](https://ram.console.aliyun.com/users/new), choose **Identities** \> **Users**.
        4.  Find the RAM user and click the username. In the User AccessKeys section of the Authentication tab, click **Create AccessKey**.
        5.  On the Phone Verification page, obtain the verification code, complete the verification process, and then click **OK**.
        6.  In the Create AccessKey dialog box, view the AccessKey ID and AccessKey secret. To save the information of the AccessKey pair, you can click **Download CSV File** or **Copy** to copy the information of the AccessKey.

            ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9364943851/p38866.png)


