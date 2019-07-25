# DeleteLogsDownloadAttribute {#reference_mcc_vwh_p2b .reference}

Delete the health check log configuration.

## Request parameters {#section_b5l_ywh_p2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String |Yes|The action to perform.Valid value: DeleteLogsDownloadAttribute

|
|RegionId|String | Yes|Delete the health check log configuration of this region.|

## Response parameters { .section}

|Name|Type|Required|
|----|----|--------|
|RequestId|String|The ID of the request.|

## Examples {#section_z5y_txh_p2b .section}

**Request example**

```

https://slb.aliyuncs.com/?Action=DeleteLogsDownloadAttribute
&RegionId=cn-hangzhou
&<CommonParameters>
```

```

https://slb.aliyuncs.com/?Action=DeleteLogsDownloadAttribute
&RegionId=cn-hangzhou
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
          <DeleteLogsDownloadAttributeResponse>
              <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
          </DeleteLogsDownloadAttributeResponse>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    }
    ```


