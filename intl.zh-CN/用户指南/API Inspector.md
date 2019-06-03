# API Inspector {#concept_kpn_tls_2gb .concept}

API Inspector是一个实验性的功能，旨在让用户查看控制台的每一步操作背后的API调用，并自动生成各语言版本的 API 代码，可通过Cloud Shell和API Explorer 在线调试。

## 功能特点 {#section_jy1_xls_2gb .section}

API Inspector与API Explorer、Cloud Shell三位一体，成为阿里云用户学习和调试API的一体化解决方案，具有以下特性：

-   自动录制：想要什么功能的API，在控制台操作相应的功能即可获得相关API调用，详情参见[自动录制API调用](#section_olp_yls_2gb)。
-   一键生成：自动生成各语种的API代码片段参数预填充，可直接运行，详情参见[一键生成API代码](#section_cyh_1ms_2gb)。
-   在线调试：结合API Explorer、Cloud Shell一键在线调试，免开发环境搭建，所见即所得，详情参见[API Explorer在线调试](#section_vxc_gms_2gb)和[Cloud Shell在线调试](#section_rvx_dms_2gb)。

## 开启API Inspector功能 {#section_jdj_qns_2gb .section}

完成以下操作，开启API Inspector功能：

1.  登录[负载均衡管理控制台](https://slb.console.aliyun.com/slb)。
2.  单击页面右下角的![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380634810_zh-CN.png)。

## 自动录制API调用 {#section_olp_yls_2gb .section}

此处以修改负载均衡实例名称为例，演示API Inspector的自动录制功能。

1.  选择**实例** \> **实例管理**。
2.  将某个负载均衡实例的名称修改为**SLB1**。
3.  单击**确定**，完成实例名称修改。
4.  单击页面右侧的**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380634810_zh-CN.png)**，可以看到上述操作涉及的所有API调用。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734821_zh-CN.png)

5.  支持勾选**隐藏Describe类接口**，查看功能核心接口，本示例为SetLoadBalancerName。

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734825_zh-CN.png)


## 一键生成API代码 {#section_cyh_1ms_2gb .section}

控制台操作的功能调用的API录制完成后，单击API名称，一键生成Python、Java、Go、Node.js和PHP格式的API代码片段参数预填充。

**说明：** 单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734833_zh-CN.png)**复制对应格式的代码段，可直接运行。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734832_zh-CN.png)

## API Explorer在线调试 {#section_vxc_gms_2gb .section}

控制台操作的功能调用的API录制完成后，单击**前往OpenApi平台**或者**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734835_zh-CN.png)**，可以直接到[OpenAPI Explorer控制台](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName)调试对应的功能且API参数值已经按照控制台操作自动生成。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734837_zh-CN.png)

**说明：** 单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734836_zh-CN.png)**查看文档，可以查看调用API的详细参数设置信息。

## Cloud Shell在线调试 {#section_rvx_dms_2gb .section}

控制台操作的功能调用的API录制完成后，展开调用API详情后，单击**![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734846_zh-CN.png)**，可以使用Cloud Shell一键在线调试功能。

**说明：** 使用Cloud Shell一键调试功能，推荐关联并创建一个OSS Bucket保存您常用脚本和文件，但会产生少量的OSS使用费用。也可以选择暂不创建。

负载均衡使用Cloud Shell调试功能的云命令行格式如下：

``` {#codeblock_75i_6lw_qbz}
aliyun slb actionName --parameter1value1 --paramter2value2...
```

如本次示例中调用的SetLoadBalancerName接口修改负载均衡实例名称为SLB1，运行的云命令行为：

``` {#codeblock_8bg_2kn_u28}
aliyun slb SetLoadBalancerName --RegionId cn-hangzhou --LoadBalancerName SLB1 --LoadBalancerId lb-bp1b6c719dfa08exfuca5
```

返回值为：

``` {#codeblock_4u7_bs3_4yr}
{"RequestId":"14466282-B00F-49C1-B11E-FB8D3772E3DA"}
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/155954380734847_zh-CN.png)

