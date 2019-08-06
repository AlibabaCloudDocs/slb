# DeleteLogsDownloadAttribute {#reference_mcc_vwh_p2b .reference}

删除健康检查日志配置。

## 调试 {#section_xmq_2bb_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DeleteLogsDownloadAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_b5l_ywh_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DeleteLogsDownloadAttribute

|
|RegionId|String|是|删除该Region的健康检查日志设置。|

## 返回参数 { .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求的ID。|

## 示例 {#section_z5y_txh_p2b .section}

**请求示例**

```

https://slb.aliyuncs.com/?Action=DeleteLogsDownloadAttribute
&RegionId=cn-hangzhou
&<公共请求参数>
```

```

https://slb.aliyuncs.com/?Action=DeleteLogsDownloadAttribute
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
          <DeleteLogsDownloadAttributeResponse>
              <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
          </DeleteLogsDownloadAttributeResponse>
    ```

-   JSON格式

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710"
    }
    ```


