# SetAccessLogsDownloadAttribute {#reference_ohp_g32_l2b .reference}

添加访问日志转发规则。

## 调试 {#section_kr5_l1b_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetAccessLogsDownloadAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_zhn_51f_l2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：SetAccessLogsDownloadAttribute

|
|RegionId|String|是|SLB实例或者LogStore所在的Region。|
|LogsDownloadAttributes|String|是|访问日志转发规则，具体请参见[表 1](#table_mj3_kbf_l2b)。|

|名称|类型|是否必须|描述|
|--|--|----|--|
|LogProject|String|是|用户SLS的LogProject。|
|LogStore|String|是|用户SLS的LogStore。|
|LoadBalancerId|String|是|需要转发访问日志的LoadBalancerId。|
|LogType|String|否|取值为layer4或者layer7，四层或者七层访问日志，默认为layer7。|
|RoleName|String|否|用户SLS的访问RoleName，默认为aliyunlogwriteonlyrole。|

## 返回参数 {#section_yg3_hbf_l2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求ID。|

## 请求示例 {#section_wsl_ncf_l2b .section}

```

https://slb.aliyuncs.com?Action= SetAccessLogsDownloadAttribute
&RegionId=cn-hangzhou
& LogsDownloadAttributes =[
{"logProject":"my-project", "LogStore":"my-log-store", "LoadBalancerId":"lb-uf68ps3rekbljmdb0cxp7", "LogType":"layer7","RoleName":"aliyunlogwriteonlyrole"}
]
&公共请求参数
```

## 返回示例 {#section_x4s_qcf_l2b .section}

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    ```

-   JSON格式

    ```
    { "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C" }
    ```


