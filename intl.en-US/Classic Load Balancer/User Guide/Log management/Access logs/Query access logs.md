# Query access logs

This topic describes how to query logs through the Server Load Balancer \(SLB\) console and the Log Service console.

1.  Go to the log query page.

    You can go to the log query page from the SLB or Log Service console:

    -   SLB console

        On the Access Logs \(Layer-7\) page, click **View Logs** in the **Actions** column.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3291019951/p7479.png)

    -   Log Service console

        On the Logstores page, click **Search** of the SLB Logstore entry.

        ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3291019951/p12838.png)

2.  Click the target log field to view detailed information.

    ![](../images/p12857.png)

3.  Enter an SQL statement to query specific access logs.

    For example, enter the following SQL statement to query the top 20 clients that send the most access requests. It helps with the analysis of the sources of access requests and business decision-making.

    ```
    * | select ip_to_province(client_ip) as client_ip_province, count(*) as pv group by
          client_ip_province order by pv desc limit 50
    ```

    ![](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/3291019951/p2494.png)


