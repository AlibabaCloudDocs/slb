# DescribeLogsDownloadAttribute {#reference_i4m_srh_p2b .reference}

Query the health check log feature.

## Request parameters {#section_pnv_dvh_p2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform.Valid value: DescribeLogsDownloadAttribute

|
|RegionId|String | Yes|Query the region with health check logs enabled.|

## Response parameters {#section_gd1_lvh_p2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|
|OSSBucketName|String|The OSS bucket where logs are to be stored.|
|LogType|String|The type of the logs to store.|
|RoleName|String|The name of the RAM role that you allow SLB to act.|

## Examples {#section_yrs_rvh_p2b .section}

**Request example**

```

https://slb.aliyuncs.com/?Action=DescribeLogsDownloadAttribute
&RegionId=cn-hangzhou
&<CommonParameters>
```

```

https://slb.aliyuncs.com/?Action=DescribeLogsDownloadAttribute
&RegionId=cn-hangzhou
&<CommonParameters>
```

**Response example**

```

```

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
          <DescribeLogsDownloadAttributeResponse>
              <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
              <RoleName>acs:ram::1655928604919847:role/aliyunslbdefaultrole</RoleName>
              <OSSBucketName>test-report</OSSBucketName>
              <LogType>HealthLog</LogType>
          </DescribeLogsDownloadAttributeResponse>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    "RoleName":"acs:ram::1655928604919847:role/aliyunslbdefaultrole",
    "OSSBucketName":"test-report",
    "LogType":"HealthLog"
    }
    ```


