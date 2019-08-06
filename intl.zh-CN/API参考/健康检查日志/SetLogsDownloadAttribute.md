# SetLogsDownloadAttribute {#reference_lyl_mrp_42b .reference}

设置日志健康检查功能。

## 调试 {#section_dtc_x1b_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetLogsDownloadAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_qhq_4rp_42b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：SetLogsDownloadAttribute

|
|RegionId|String|是|需要开启健康检查日志的Region，适用于该Region下的所有LB实例。|
|LogType|String|是|一共有三种类型的日志可进行存储，包含健康检查日志、访问日志和错误日志。取值：HealthLog,AccessLog/HealthLog/AccessLog

每次传入必须是全量的配置，如果用户在开通HealthLog的情况下再输出AccessLog，需要传入HealthLog,AccessLog。

目前只支持HealthLog。

|
|OSSBucketName|String|是|日志即将写入的OSSBucket。设置时，必须保证该Bucket已经存在。

|
|RoleName|String|否|用户允许SLB扮演的RAM角色名称。默认值：aliyunslbdefaultrole

|

## 返回参数 {#section_pbs_ksp_42b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求的ID。|

## 示例 {#section_qjx_rsp_42b .section}

**请求示例**

```

https://slb.aliyuncs.com?Action=SetLogsDownloadAttribute
&RegionId=cn-hangzhou
&LogType=HealthLog
&OSSBucketName=test-report
&<公共请求参数>
```

```

https://slb.aliyuncs.com?Action=SetLogsDownloadAttribute
&RegionId=cn-hangzhou
&LogType=HealthLog
&OSSBucketName=test-report
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
       <SetLogsDownloadAttributeResponse>
           <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
       </SetLogsDownloadAttributeResponse>
    ```

-   JSON格式

    ```
    {
          "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
     }
    ```


