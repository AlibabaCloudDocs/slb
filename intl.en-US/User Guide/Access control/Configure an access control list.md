# Configure an access control list {#concept_o1v_2hw_tdb .concept}

Server Load Balancer \(SLB\) provides you with an access control function. You can configure different access control rules \(access whitelist or blacklist\) for different listeners. Before configuring access control for a listener, you must first configure an access control list.

You can create multiple access control lists. Each list contains multiple IP addresses or CIDR blocks. Limits on access control lists are as follows:

|Resource|Limit|
|:-------|:----|
|The maximum number of access control lists per region.|50|
|The maximum number of IP entries added each time.|50|
|The maximum number of IP entries per access control list.|300|
|The maximum number of listeners with which an access control list can be associated|50|

## Create an access control list {#section_scs_whw_tdb .section}

To create an access control list, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select a region.
3.  In the left-side navigation pane, click Access Control.
4.  Click **Create Access Control List**, enter an access control list name, and click **OK**.

## Add IP entries {#section_dyr_kjw_tdb .section}

To add IP entries to the access control list, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Find the target access control list and click **Manage**.
5.  Add IP entries:
    -   Click **Add Multiple Entries**. In the displayed dialog box, add IP addresses or CIDR blocks and click **OK**.

        Note the following when you add IP entries:

        -   Each line should include only one IP entry. Use the Enter key to break lines.

        -   Use a vertical bar \(|\) to separate an IP address or a CIDR block with the description, for example, 192.168.1.0/24|description.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15685/15597279167335_en-US.png)

    -   Click **Add Entry**. In the displayed dialog box, add an IP address or a CIDR block and the description, and click **OK**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/15685/15597279167336_en-US.png)


## Delete IP entries {#section_cbm_gkw_tdb .section}

To delete IP entries, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Find the target access control list and click **Manage**.
5.  Click **Delete** in the **Actions** column of the target IP entry, or select multiple IP entries and click **Delete** at the bottom of the list.
6.  In the displayed dialog box, click **OK**.

