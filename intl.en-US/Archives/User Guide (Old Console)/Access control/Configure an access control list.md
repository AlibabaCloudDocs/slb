# Configure an access control list {#concept_o1v_2hw_tdb .concept}

Server Load Balancer \(SLB\) provides you with the access control function. You can configure different access control rules \(access whitelist or blacklist\) for different listeners. Before configuring access control for listeners, you must first configure an access control list.

Currently, the access control function is available in the following regions:

-   Singapore
-   Australia \(Sydney\)
-   Malaysia \(Kuala Lumpur\)
-   Japan \(Tokyo\)
-   US \(Silicon Valley\)
-   US \(Virginia\)
-   Germany \(Frankfurt\)
-   UAE \(Dubai\)
-   India \(Mumbai\)

    It will be available in other regions successively.


You can create multiple access control lists. Each list contains multiple IP addresses or CIDR blocks. Limits on access control lists are as follows:

|Resource|Limits|
|:-------|:-----|
|The maximum number of access control lists per region|50|
|The maximum number of IP addresses added or deleted at each time|50|
|The maximum number of entries per access control list|300|
|The maximum number of listeners that an access control list can be added to|50|

## Create an access control list {#section_scs_whw_tdb .section}

1.  Log on to the [Server Load Balancer console](https://slbnew.console.aliyun.com).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Click **Create Access Control List**, enter the name of the list, and click **Confirm**.

## Add IP entries {#section_dyr_kjw_tdb .section}

1.  Log on to the [Server Load Balancer console](https://slbnew.console.aliyun.com).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Find the target access control list and click **Manage**.
5.  Add IP entries:
    -   Click **Add Multiple Entries**, and then add one or more IP addresses or CIDR blocks in the displayed dialog box.

        Note the following when adding entries:

        -   Each line is one entry. Use the Enter key to break lines.

        -   Use “|” to separate an IP address or CIDR block with the note. For example, “192.168.1.0/24|note”.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4159/1022_en-US.png)

    -   Click **Add Entry**, and then add an IP address or a CIDR block. Click **Confirm** to add an entry to the access control list.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4159/1023_en-US.png)


## Delete IP entries {#section_cbm_gkw_tdb .section}

1.  Log on to the [Server Load Balancer console](https://slbnew.console.aliyun.com).
2.  Select a region.
3.  In the left-side navigation pane, click **Access Control**.
4.  Find the target access control list and click **Manage**.
5.  Click **Delete** in the **Actions** column of the target IP entry, or select multiple IP entries and click **Delete** at the bottom of the entry table.
6.  In the displayed dialog box, click **Confirm**.

