# DescribeLogsDownloadAttribute {#reference_i4m_srh_p2b .reference}

查询日志健康检查功能。

## 调试 {#section_bkl_bbb_rfb .section}

```
点击这里在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_pnv_dvh_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
| Action|String|是|要执行的操作，取值：  DescribeLogsDownloadAttribute 

 |
| RegionId|String|是|查询设置健康检查功能的Region。|

## 返回参数 {#section_gd1_lvh_p2b .section}

|名称|类型|描述|
|--|--|--|
| RequestId|String|请求的ID。|
| OSSBucketName|String|日志即将写入的OSSBucket。|
| LogType|String|用户需存储的日志类型。|
| RoleName|String|用户允许SLB扮演的RAM角色名称。|

## 示例 {#section_yrs_rvh_p2b .section}

 **请求示例**

```

https://slb.aliyuncs.com/?Action=DescribeLogsDownloadAttribute
&RegionId=cn-hangzhou
&<公共请求参数>
```

```

https://slb.aliyuncs.com/?Action=DescribeLogsDownloadAttribute
&RegionId=cn-hangzhou
&<公共请求参数>
```

 **返回示例** 

```

```

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
          <DescribeLogsDownloadAttributeResponse>
              <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
              <RoleName>acs:ram::165592860:role/aliyunslbdefaultrole</RoleName>
              <OSSBucketName>test-report</OSSBucketName>
              <LogType>HealthLog</LogType>
          </DescribeLogsDownloadAttributeResponse>
    ```

-   JSON格式

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    "RoleName":"acs:ram::165592860xxxxx:role/aliyunslbdefaultrole",
    "OSSBucketName":"test-report",
    "LogType":"HealthLog"
    }
    ```


