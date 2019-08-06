# DescribeLogsDownloadStatus {#reference_nqn_dgj_p2b .reference}

Query the health check log feature.

## Request parameters {#section_m2f_fgj_p2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform.Valid value: DescribeLogsDownloadStatus

|
|RegionId|String |Yes|The region that requires querying health check logs.|

## Response parameters {#section_lpg_4gj_p2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|
|LogsDownloadStatus|String|The status of log storage.|

## Examples {#section_whp_ygj_p2b .section}

**Request example**

```

https://slb.aliyuncs.com?Action=DescribeLogsDownloadStatus
&RegionId=cn-hangzhou
&<CommonParameters>
```

```

https://slb.aliyuncs.com?Action=DescribeLogsDownloadStatus
&RegionId=cn-hangzhou
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
       <DescribeLogsDownloadStatusResponse>
           <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
       </DescribeLogsDownloadStatusResponse>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


