# Migrate to the new access control {#concept_r2k_jdc_wdb .concept}

If you have already configured a whitelist for a listener, the system can automatically add the IP addresses or CIDR blocks in the whitelist to an access control list and apply the list to the listener.

## Migrate a whitelist to an access control list {#section_prf_k2c_wdb .section}

To migrate a previously configured whitelist to an access control list, complete these steps:

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-beijing).
2.  Select the region where the SLB instance is located, and then click the ID of the target SLB instance.
3.  In the left-side navigation pane, click **Listeners**.
4.  Find the target listener, and then click **More** \> **Set Access Control**.
5.  Click **Use New Access Control Features**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4161/2857_en-US.png)

6.  Enter a name of the access control list and click **Create Access Control List**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4161/2858_en-US.png)

7.  Click **Apply** to apply the list to the listener as a whitelist.

    **Note:** If you do not apply the list to a listener, the whitelist does not take effect.


## View the migrate access control list {#section_e5s_hfc_wdb .section}

To view the migrated access control list, complete these steps:

1.  Log on to the [SLB console](http://slbnew.console.aliyun.com/#/list/cn-beijing).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Find the created access control list and view the associated listener. You can click **Manage** to manage IP entries.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4161/2863_en-US.png)


