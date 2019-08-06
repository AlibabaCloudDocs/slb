# DescribeLogsDownloadStatus {#reference_nqn_dgj_p2b .reference}

查询日志健康检查功能。

## 调试 {#section_fwm_nbb_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeLogsDownloadStatus)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_m2f_fgj_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DescribeLogsDownloadStatus

|
|RegionId|String|是|需要查询健康检查日志的Region。|

## 返回参数 {#section_lpg_4gj_p2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求的ID。|
|LogsDownloadStatus|String|日志存储的状态，是否开启。|

## 示例 {#section_whp_ygj_p2b .section}

**请求示例**

```

https://slb.aliyuncs.com?Action=DescribeLogsDownloadStatus
&RegionId=cn-hangzhou
&<公共请求参数>
```

```

https://slb.aliyuncs.com?Action=DescribeLogsDownloadStatus
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
       <DescribeLogsDownloadStatusResponse>
           <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
       </DescribeLogsDownloadStatusResponse>
    ```

-   JSON格式

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
    }
    ```


