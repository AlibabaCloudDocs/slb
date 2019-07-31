# API Inspector {#concept_kpn_tls_2gb .concept}

API Inspector is an experimental feature. With API Inspector, you can view the API calls behind each operation in the console, and automatically generate API code of different languages. You can debug online through Cloud Shell or OpenAPI Explorer.

## Features {#section_jy1_xls_2gb .section}

API Inspector, OpenAPI Explorer, and Cloud Shell form an integrated solution for you to learn and debug APIs. API Inspector has the following features:

-   Automatic recording: To obtain related API calls, you only need to perform operations in the console. For more information, see [Automatically record API calls](#section_olp_yls_2gb).
-   Code generating with one click: API code scripts in different languages with pre-filled parameters are generated and can be run directly. For more information, see [Generate API codes with one click](#section_cyh_1ms_2gb).
-   Online debugging: When API Inspector is used together with OpenAPI Explorer and Cloud Shell, one-click online debugging can be implemented and you do not need to build the development environment. What you see is what you get. For more information, see [Debug online through OpenAPI Explorer](#section_vxc_gms_2gb) and [Debug online through Cloud Shell](#section_rvx_dms_2gb).

## Enable API Inspector {#section_jdj_qns_2gb .section}

To enable API Inspector, follow these steps:

1.  Log on to the [SLB console](https://slb.console.aliyun.com/slb).
2.  In the lower-right corner of the page, click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848534810_en-US.png).

## Automatically record API calls {#section_olp_yls_2gb .section}

In this topic, modifying the name of an SLB instance is taken as an example to demonstrate the automatic recording function of API Inspector.

1.  Choose **Instances** \> **Server Load Balancer**.
2.  Modify the name of an SLB instance to **SLB1**.
3.  Click **OK**.
4.  Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848534810_en-US.png)** on the right side of the page. Then you can see all API calls related to the preceding operation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848634821_en-US.png)

5.  You can click **Hide Describe Class** to view core APIs. In this example, the core API is SetLoadBalancerName.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848634825_en-US.png)


## Generate API codes with one click {#section_cyh_1ms_2gb .section}

After API recording is completed, click the API name to generate API code scripts in Python, Java, Go, Node.js, and PHP, with pre-filled parameters.

**Note:** Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848634833_en-US.png)** to copy the code scripts of the corresponding format, which can be run directly.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848634832_en-US.png)

## Debug online through OpenAPI Explorer {#section_vxc_gms_2gb .section}

After the API recording is completed, click **OpenAPI Explorer** or **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848734835_en-US.png)** to go to the [OpenAPI Explorer console](https://api.aliyun.com/#product=Slb&api=SetLoadBalancerName) to debug the corresponding function. The API parameter values have been automatically generated according to operations in the console.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848734837_en-US.png)

**Note:** Click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848734836_en-US.png)** to view the document describing parameter details of the called API.

## Debug online through Cloud Shell {#section_rvx_dms_2gb .section}

After API recording, unfold the API calling details and click **![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848734846_en-US.png)** to use the online one-click debugging function of Cloud Shell.

**Note:** If you use the one-click debugging function of Cloud Shell, we recommend that you create and associate an OSS bucket to store your frequently used scripts and files. However, some OSS fees will be generated. You can also choose not to create an OSS bucket.

The command format for the Cloud Shell debugging of SLB is as follows:

``` {#codeblock_75i_6lw_qbz}
aliyun slb actionName --parameter1value1 --paramter2value2...
```

In this example, the called SetLoadBalancerName API modifies the name of the SLB instance to SLB1. The corresponding command is:

``` {#codeblock_8bg_2kn_u28}
aliyun slb SetLoadBalancerName --RegionId cn-hangzhou --LoadBalancerName SLB1 --LoadBalancerId lb-bp1b6c719dfa08exfuca5
```

The returned value is:

``` {#codeblock_4u7_bs3_4yr}
{"RequestId":"14466282-B00F-49C1-B11E-FB8D3772E3DA"}
```

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/81371/156454848734847_en-US.png)

