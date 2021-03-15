# 更新HTTPS证书

介绍如何使用Python SDK给一个SLB实例创建一个HTTPS监听，并更新该实例下HTTPS监听使用的服务器证书。

在华北3张家口地域已经有两台状态为**运行中**的ECS实例。

在开始运行示例脚本前，您还需确保完成准备工作，更多信息，请参见[准备工作](/intl.zh-CN/传统型负载均衡CLB/CLB开发指南/SDK 参考/Python SDK示例/准备工作.md)。

本次示例分为以下几步，为SLB实例添加HTTPS监听，更新HTTPS监听的证书。

1.  在华北3张家口地域创建一个名为SLB1的SLB实例，主可用区为cn-zhangjiakou-a，备可用区为cn-zhangjiakou-b，实例计费类型为按量计费，规格为slb.s1.small，其他配置使用系统默认值。
2.  将张家口地域的两台ECS实例添加到默认服务器组，用来分发流量，ECS实例的后端服务权重都为100。
3.  上传服务器证书。
4.  创建HTTPS监听，SLB实例前端使用的端口为80，后端服务器开放用来接收请求的端口为443，关闭健康检查和会话保持，监听带宽峰值为6 Mbps，其他使用默认值。
5.  上传新的服务器证书。
6.  更新新建HTTPS监听的服务器证书。
7.  删除新建的SLB实例。

1.  在下载的SDK目录中，打开aliyun-openapi-python-sdk-examples\\sdk\_examples\\examples\\slb文件夹。

2.  使用编辑器打开upload\_server\_certificate.py文件，您需要配置用户鉴权参数ACS\_CLIENT，其他参数根据实际情况配置后，保存退出。

    **说明：** 因为用户鉴权是每个SDK必须执行的操作，所以可以在常量文件中配置AcsClient参数的值，在场景代码中调用常量文件。

3.  进入upload\_server\_certificate.py所在的目录，执行如下命令，运行更新HTTPS证书示例。

    ```
    python upload_server_certificate.py
    ```

    系统显示类似如下：

    ```
    ---------------------------create_load_balancer---------------------------
    {
      "VpcId": "",
      "AddressIPVersion": "ipv4",
      "LoadBalancerName": "SLB1",
      "ResourceGroupId": "rg-axxxxxxxxxxxy",
      "VSwitchId": "",
      "RequestId": "1DEF72EE-CA5C-449D-9E97-2CE460DE7F7A",
      "Address": "123.XX.XX.212",
      "NetworkType": "classic",
      "LoadBalancerId": "lb-8vxxxxxxxxxxxf"
    }
    
    ---------------------------upload_server_certificate---------------------------
    {
      "ExpireTimeStamp": 1732169065000,
      "RegionIdAlias": "cn-zhangjiakou",
      "AliCloudCertificateName": "",
      "RegionId": "cn-zhangjiakou",
      "CommonName": "test",
      "ServerCertificateName": "test",
      "ExpireTime": "2024-11-21T06:04:25Z",
      "ResourceGroupId": "rg-axxxxxxxxxxxyy",
      "RequestId": "D6FB8B7C-B0EA-43E7-AD8F-E0201A9E1A13",
      "Fingerprint": "cd:90:1b:7b:49:4d:1d:90:f6:01:de:9a:81:7d:31:a7:38:1d:84:8d",
    
      "AliCloudCertificateId": "",
      "IsAliCloudCertificate": 0,
      "ServerCertificateId": "12xxxxxxxxxxxx3_16xxxxxxxxxx6_-1xxxxxxxx13_-1xxxxxx72"
    }
    
    ---------------------------create_https_listener---------------------------
    {
      "RequestId": "FC70EDC8-06EC-4E1C-97BE-D81571DA23B4"
    }
    
    ---------------------------upload_server_certificate---------------------------
    {
      "ExpireTimeStamp": 1567857600000,
      "RegionIdAlias": "cn-zhangjiakou",
      "AliCloudCertificateName": "",
      "RegionId": "cn-zhangjiakou",
      "CommonName": "doc.aliyun-slb.top",
      "ServerCertificateName": "doc.aliyun-slb.top",
      "ExpireTime": "2019-09-07T12:00:00Z",
      "ResourceGroupId": "rg-acxxxxxxxxxxxxy",
      "RequestId": "913E991F-BCC9-4A3D-9802-19084E2CE271",
      "Fingerprint": "8c:47:1b:a7:8f:02:27:3a:35:7c:e3:47:4a:5f:55:02:ed:e3:57:1e",
    
      "SubjectAlternativeNames": {
        "SubjectAlternativeName": [
          "doc.aliyun-slb.top"
        ]
      },
      "AliCloudCertificateId": "",
      "IsAliCloudCertificate": 0,
      "ServerCertificateId": "12xxxxxxxxxxxx3_16xxxxxxx716_4xxxxxxx4_-14xxxxxxxxxx9"
    }
    
    ---------------------------set_https_listener_attribute-------------------------
    --
    {
      "RequestId": "14275D2B-20F2-4D96-9FC8-7BB2B110155C"
    }
    
    ---------------------------delete_load_balancer---------------------------
    {
      "RequestId": "2A1DF87C-842A-4C1E-AA61-23EB365EB86F"
    }
    ```


