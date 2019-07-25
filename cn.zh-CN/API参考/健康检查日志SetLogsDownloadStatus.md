# SetLogsDownloadStatus {#reference_esg_vz3_p2b .reference}

设置日志健康检查状态开关。

## 调试 {#section_a52_kbb_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=SetLogsDownloadStatus)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_utm_jdj_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：SetLogsDownloadStatus

|
|RegionId|String|是|需要开启健康检查日志的Region，适用于该Region下的所有SLB实例。|
|LogsDownloadStatus|String|是|日志存储的状态，取值：on|off（默认值）

|
|RoleName|String|否|用户允许SLB扮演的RAM角色名称。默认值：aliyunslbdefaultrole

|

## 返回参数 {#section_ttc_5dj_p2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求的ID。|

## 示例 {#section_bqs_m2j_p2b .section}

**请求示例**

```

https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
&RegionId=cn-hangzhou
&LogsDownloadStatus=on
&<公共请求参数>
```

```

https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
&RegionId=cn-hangzhou
&LogsDownloadStatus=on
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    
    https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
    &RegionId=cn-hangzhou
    &LogsDownloadStatus=on
    &<公共请求参数>
    ```

-   JSON格式

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
    }
    ```


