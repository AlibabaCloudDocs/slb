# SetLogsDownloadStatus {#reference_esg_vz3_p2b .reference}

Enable or disable health check logs.

## Request parameters {#section_utm_jdj_p2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform.Valid value: SetLogsDownloadStatus

|
|RegionId|String | Yes|The region that requires enabling health check logs. The action applies to all SLB instances in this region.|
|LogsDownloadStatus|String | Yes|The status of log storage.Valid value: on/off.

Default value: off.

|
|RoleName|String| No|The name of the RAM role that you allow SLB to act.Default value: aliyunslbdefaultrole.

|

## Response parameters {#section_ttc_5dj_p2b .section}

|Name|Type|Description |
|----|----|------------|
|RequestId|String|The ID of the request.|

## Examples {#section_bqs_m2j_p2b .section}

**Request example**

```

https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
&RegionId=cn-hangzhou
&LogsDownloadStatus=on
&<CommonParameters>
```

```

https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
&RegionId=cn-hangzhou
&LogsDownloadStatus=on
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    
    https://slb.aliyuncs.com?Action=SetLogsDownloadStatus
    &RegionId=cn-hangzhou
    &LogsDownloadStatus=on
    &<Common Request Parameters>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


