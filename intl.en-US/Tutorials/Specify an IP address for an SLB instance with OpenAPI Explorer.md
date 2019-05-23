# Specify an IP address for an SLB instance with OpenAPI Explorer {#task_rz1_xqj_mfb .task}

This topic describes how to specify an intranet IP address when you create a Server Load Balancer \(SLB\) instance using OpenAPI Explorer. Specifically, when you create an SLB instance in a VPC network using OpenAPI Explorer, you can specify the IP address used by the CIDR block of the VSwitch where the SLB instance to be created belongs as the intranet IP address of the SLB instance.

1.  Log on to the [OpenAPI Explorer](https://api.aliyun.com/). 
2.  Search for the CreateLoadBalancer API. 
3.  Configure required parameters. Some parameters are listed here. For a full list, see [../../../../dita-oss-bucket/SP\_23/DNSLB11870158/EN-US\_TP\_4182.md\#](../../../../intl.en-US/Developer Guide/Server Load Balancer (SLB) instances/CreateLoadBalancer.md#).
    -   RegionId: the region to which the SLB instance belongs. In this example, select cn-hangzhou.
    -   VpcId: the ID of the VPC where the SLB instance belongs.

        To view the VPC ID, follow these steps:

        1.  Log on to the VPC console.
        2.  In the upper-left corner, select the region to which the target VPC belongs. In this example, select **China \(Hangzhou\)**.
        3.  View the target VPC ID from the VPC list.
    -   VSwitchId: the ID of the VSwitch to which the SLB instance belongs. To specify the IP address of the SLB instance, this parameter is required.

        To view the ID of the target VSwitch, follow these steps:

        1.  Log on to the VPC console.
        2.  In the upper-left corner, select the region to which the target VPC belongs. In this example, select **China \(Hangzhou\)**.
        3.  Click the target VPC ID.
        4.  Click the number of VSwitch in the **Network Resources** area.
        5.  View the VSwitch ID from the VSwitch list.
        6.  To view the destination CIDR block of the VSwitch, click the VSwitch ID. In this example, the destination CIDR block is 192.168.0.0/24.
    -   Address: the intranet IP address of the SLB instance. This IP address must belong to the destination CIDR block of the VSwitch \(for example, 192.168.0.3\).
4.  Click **Submit Request**. The response parameters are as follows:
    -   XML format

        ```
        <?xml version="1.0" encoding="UTF-8" ?>
        	<NetworkType>vpc</NetworkType>
        	<LoadBalancerName>auto_named_slb</LoadBalancerName>
        	<Address>192.168.0.3</Address>
        	<ResourceGroupId>rg-acfmxazb4ph6aiy</ResourceGroupId>
        	<RequestId>09197EEB-7013-4F56-A5CE-A756FFE5B75D</RequestId>
        	<AddressIPVersion>ipv4</AddressIPVersion>
        	<LoadBalancerId>lb-bp1h66tp5uat84khmqc9e</LoadBalancerId>
        	<VSwitchId>vsw-bp14cagpfysr29feg5t97</VSwitchId>
        	<VpcId>vpc-bp18sth14qii3pnvodkvt</VpcId>
        ```

    -   JSON format

        ```
        {
            "NetworkType": "vpc", 
            "LoadBalancerName": "auto_named_slb", 
            "Address": "192.168.0.3", 
            "ResourceGroupId": "rg-acfmxazb4ph6aiy", 
            "RequestId": "09197EEB-7013-4F56-A5CE-A756FFE5B75D", 
            "AddressIPVersion": "ipv4", 
            "LoadBalancerId": "lb-bp1h66tp5uat84khmqc9e", 
            "VSwitchId": "vsw-bp14cagpfysr29feg5t97", 
            "VpcId": "vpc-bp18sth14qii3pnvodkvt"
        }
        ```

5.  Log on to the [SLB console](https://slb.console.aliyun.com/slb/cn-hangzhou/slbs) and select the China \(Hangzhou\) region to check whether the SLB instance with the intranet IP address 192.168.0.3 has been created. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/23817/155860422813814_en-US.png)


