# Manage tags {#concept_dhb_cm3_42b .concept}

You can classify Server Load Balancer \(SLB\) instances by using tags.

Each tag consists of a key and a value. Before you use tags, note the following limits:

-   A tag cannot exist on its own and must be associated with an SLB instance.
-   Up to 10 tags can be associated with an SLB instance.
-   The key of each tag associated with an instance must be unique. Tags with the same key will be overwritten.
-   Tags cannot be used across regions and are region-specific resources. For example, tags that belong to the China \(Hangzhou\) region are invisible to the China \(Shanghai\) region.

## Add a tag {#section_xcy_l5n_vdb .section}

To add a tag, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select a region and find the target SLB instance.
4.  In the **Actions** column, choose **More** \> **Edit Tags**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16154/15645483397385_en-US.png)

5.  On the Edit Tags page, complete these steps:
    1.  If there are available tags, click **Saved Tags** and then select the tag to add.
    2.  If you want to create a new tag, on the Edit Tags page, click **New Tag**, enter the key and value of the new tag, and click **OK**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16154/15645483397386_en-US.png)

    3.  Click **OK**.

## Search instances by using a tag {#section_lyq_wvn_vdb .section}

To search instances by using a tag, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select a region.
4.  Click **Select a tag**, and select the tag to be used as the search criteria.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16154/15645483407388_en-US.png)

5.  To clear the filter criteria, you can click the delete icon next to the selected tag.

## Delete a tag {#section_nf2_3wn_vdb .section}

SLB does not support deleting tags of multiple instances in batches. You can remove the tags of only one instance at a time.

To delete a tag, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou).
2.  In the left-side navigation pane, choose **Instances** \> **Server Load Balancer**.
3.  Select a region and find the target instance.
4.  In the **Actions** column, choose **More** \> **Edit Tags**.
5.  On the Edit Tags page, click the delete icon next to the tag to be removed, and then click **OK**.

    **Note:** If a tag is removed from one instance and is not associated with any other instances, the tag is removed from the system.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/16154/15645483407387_en-US.png)


