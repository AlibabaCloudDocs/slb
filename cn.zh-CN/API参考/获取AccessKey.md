# 获取AccessKey {#task_iln_hyk_5gb .task}

您可以为阿里云主账号和子账号创建一个访问密钥（AccessKey）。在调用阿里云API时您需要使用AccessKey完成身份验证。

AccessKey包括AccessKeyId和AccessKeySecret。

-   AccessKeyId：用于标识用户。
-   AccessKeySecret：用于验证用户的密钥。AccessKeySecret必须保密。

**警告：** 主账号Accesskey泄露会威胁您所有资源的安全。建议使用子账号（RAM用户）Accesskey进行操作，可有效降低Accesskey泄露的风险。

1.  以主账号登录[阿里云管理控制台](https://home.console.aliyun.com/new?spm=a2c4g.11186623.2.13.b22b5f81PaDcNA#/)。
2.  将鼠标置于页面右上方的账号图标，单击**accesskeys**。
3.  在**安全提示**页面，选择获取主账号还是子账号的Accesskey。 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/155979237638859_zh-CN.png)

4.  获取账号Accesskey。 
    -   获取主账号AccessKey
        1.  单击**继续使用AccessKey**。
        2.  在安全信息管理页面，单击**创建AccessKey**。
        3.  在手机验证页面，获取验证码，完成手机验证，单击**确定**。
        4.  在新建用户AccessKey页面，展开**AccessKey详情**，查看AccessKeyId和AccessKeySecret。可以单击**保存AK信息**，下载AccessKey信息。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/155979237738862_zh-CN.png)

    -   获取子账号AccessKey
        1.  单击**开始使用子用户AccessKey**。
        2.  如果未创建RAM用户，在系统跳转的[RAM访问控制台](https://ram.console.aliyun.com/users/new)的新建用户页面，创建RAM用户。如果是获取已有RAM用户的Accesskey，则跳过此步骤。
        3.  在[RAM访问控制台](https://ram.console.aliyun.com/users/new)的左侧导航栏，选择**人员管理** \> **用户**，搜索需要获取AccessKey的用户。
        4.  单击用户登录名称，在用户详情页认证管理页签下的用户AccessKey区域，单击**创建新的AccessKey**。
        5.  在手机验证页面，获取验证码，完成手机验证，单击**确定**。
        6.  在创建AccessKey页面，查看AccessKeyId和AccessKeySecret。可以单击**下载CSV文件**，下载AccessKey信息或者单击**复制**，复制AccessKey信息。

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/125197/155979237738866_zh-CN.png)


