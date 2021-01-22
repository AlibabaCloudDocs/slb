# Specify an IP address for an SLB instance by using OpenAPI Explorer

This topic describes how to specify an internal IP address when you create a Server Load Balancer \(SLB\) instance by using OpenAPI Explorer. You can specify the IP address used by the CIDR block of the VSwitch to which the SLB instance to be created belongs as the internal IP address of the SLB instance.

1.  Log on to the [OpenAPI Explorer console](https://api.aliyun.com/).

2.  Search for the CreateLoadBalancer API operation.

3.  Configure the parameters.

    Only some parameters are listed here. For more information, see [Create an SLB instance](/intl.en-US/Classic Load Balancer/User Guide/Instance/Create an SLB instance.md).

    -   RegionId: the region ID of the SLB instance. For this example, it is cn-hangzhou.
    -   VpcId: the ID of the VPC to which the SLB instance belongs.

        You can log on to the Virtual Private Cloud console and select China \(Hangzhou\) to view the VPC ID.

    -   VSwitchId: the ID of the VSwitch to which the SLB instance belongs. This parameter is required when you specify an SLB IP address.

        You can log on to the Virtual Private Cloud console and click the ID of the VPC to which the SLB instance belongs. Click the number of VSwitches on the Resources tab to view the ID of the VSwitch.

        Click the ID of the VSwitch to view the CIDR block of the VSwitch. Example: 192.168.0.0/24.

    -   Address: the internal IP address of the SLB instance. This IP address must belong to the CIDR block of the VSwitch. For this example, it is 192.168.0.3.
4.  Click **Submit Request**.

    The following response parameters are returned:

    -   XML format

        ```
        <? xml version="1.0" encoding="UTF-8" ? >
            <NetworkType>vpc</NetworkType>
            <LoadBalancerName>auto_named_slb</LoadBalancerName>
            <Address>192.168.0.3</Address>
            <ResourceGroupId>rg-acfmxazb4ph*****</ResourceGroupId>
            <RequestId>09197EEB-7013-4F56-A5CE-A756FFE5B75D</RequestId>
            <AddressIPVersion>ipv4</AddressIPVersion>
            <LoadBalancerId>lb-bp1h66tp5uat84kh******</LoadBalancerId>
            <VSwitchId>vsw-bp14cagpfysr29fe*****</VSwitchId>
            <VpcId>vpc-bp18sth14qii3pn*****</VpcId>
        ```

    -   JSON format

        ```
        {
            "NetworkType": "vpc", 
            "LoadBalancerName": "auto_named_slb", 
            "Address": "192.168.0.3", 
            "ResourceGroupId": "rg-acfmxazb4******", 
            "RequestId": "09197EEB-7013-4F56-A5CE-A756FFE5B75D", 
            "AddressIPVersion": "ipv4", 
            "LoadBalancerId": "lb-bp1h66tp5uat84******", 
            "VSwitchId": "vsw-bp14cagpfysr29*******", 
            "VpcId": "vpc-bp18sth14qii3*********"
        }
        ```

5.  Log on to the [Server Load Balancer console](https://slb.console.aliyun.com/slb/cn-hangzhou/slbs) and select the China \(Hangzhou\) region. Check whether the SLB instance to which the 192.168.0.3 IP address is assigned is created.


