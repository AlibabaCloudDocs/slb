# SetLogsDownloadAttribute {#reference_lyl_mrp_42b .reference}

Configure the health check log feature.

## Request parameters {#section_qhq_4rp_42b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform.Valid value: SetLogsDownloadAttribute

|
|RegionId|String | Yes|The region that requires enabling health check logs. The action applies to all SLB instances in this region.|
|LogType|String | Yes|You can store three types of logs, including health check logs, access logs and error logs.Valid values: HealthLog,AccessLog/HealthLog/AccessLog.

Full configuration is required each time. If you export access logs after enabling health logs, you must enter HealthLog,AccessLog.

Currently only HealthLog is supported.

|
| |String | Yes|The OSS bucket that the logs are to be stored.Make sure the OSS bucket already exists.

|
| |String| No|The name of the RAM role that you allow SLB to play.Default value: aliyunslbdefaultrole

|

## Response parameters {#section_pbs_ksp_42b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|

## Examples {#section_qjx_rsp_42b .section}

**Request example**

```

https://slb.aliyuncs.com?Action=SetLogsDownloadAttribute
&RegionId=cn-hangzhou
&LogType=HealthLog
&OSSBucketName=test-report
&<CommonParameters>
```

```

https://slb.aliyuncs.com?Action=SetLogsDownloadAttribute
&RegionId=cn-hangzhou
&LogType=HealthLog
&OSSBucketName=test-report
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
       <SetLogsDownloadAttributeResponse>
           <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
       </SetLogsDownloadAttributeResponse>
    ```

-   JSON format

    ```
    {
          "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
     }
    ```


