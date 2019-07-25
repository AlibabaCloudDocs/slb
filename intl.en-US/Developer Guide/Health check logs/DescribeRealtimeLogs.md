# DescribeRealtimeLogs {#reference_z52_r3j_p2b .reference}

Query health check logs.

## Request parameters {#section_epv_s3j_p2b .section}

|Name |Type|Required|Description |
|-----|----|--------|------------|
|Action |String | Yes|The action to perform.Valid value: DescribeRealtimeLogs.

|
|RegionId|String |Yes|The region that requires querying health check logs.|
|LogType|String | Yes|The type of the logs to be queried.Valid value: HealthLog.

|
|LogStartTime|String | Yes|The start time of logs to obtain.Format: yyyy-mm-ddThh:mm:ssZ.

You can obtain logs generated less than three days before.

|
|LogEndTime|String | Yes|The end time of logs to obtain.Format: yyyy-mm-ddThh:mm:ssZ.

You can obtain logs generated till now.

|
|LoadBalancerId|String| No|The ID of the SLB instance to query. It serves as a filter value.|
|RoleName|String| No|The name of the RAM role that you allow SLB to act.Default value: aliyunslbdefaultrole.

|

## Response parameters {#section_yxb_gnj_p2b .section}

|Name|Type|Description|
|----|----|-----------|
|RequestId|String|The ID of the request.|
|PageSize|String|The number of pages to return.|
|PageNumber|String|The number of rows per page. |
|Progress|String|Whether the query result includes all logs queried. If Progressing is returned, use the same parameters to call the API and then all logs can be obtained.|
|LBRealTimeLogsSet|Set|A list of realtime logs. For more information, see [Table 1](#table_ymn_2sj_p2b).|

|Name|Type|Description|
|----|----|-----------|
|LogDetail|String|Detailed log information.|

## Examples {#section_glr_qsj_p2b .section}

**Request example**

```

https://slb.aliyuncs.com?Action=DescribeRealtimeLogs
&RegionId=cn-hangzhou
&LogType=HealthLog
&LogStartTime=2017-06-13T11:50:20Z
&LogEndTime=2017-06-13T12:50:20Z
&<CommonParameters>
```

```

https://slb.aliyuncs.com?Action=DescribeRealtimeLogs
&RegionId=cn-hangzhou
&LogType=HealthLog
&LogStartTime=2017-06-13T11:50:20Z
&LogEndTime=2017-06-13T12:50:20Z
&<CommonParameters>
```

**Response example**

-   XML format

    ```
    <? xml version="1.0" encoding="UTF-8"? >
       <DescribeRealtimeLogsResponse>
           <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
           <PageNumber>1</PageNumber>
           <PageSize>50</PageSize>
           <Progress>Complete</Progress>
           <LBRealTimeLogsSet>
               <LBRealTimeLog>
                   <LogDetail>
                   2017-05-18 23:04:15 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error
                   </LogDetail>
                   <LogDetail>
                  2017-05-18 23:04:16 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error
                   </LogDetail>
                   <LogDetail>
                  2017-05-18 23:04:12 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error
                   </LogDetail>
               </LBRealTimeLog>
           </LBRealTimeLogsSet>
       </DescribeRealtimeLogsResponse>
    ```

-   JSON format

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    "PageNumber": "1",
    "PageSize":50,
    "progress": "Complete",
    "LBRealTimeLogsSet": {
    "LBRealTimeLog": [
    {"LogDetail": "2017-05-18 23:04:15 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error"},
    {“LogDetail": "2017-05-18 23:04:16 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error"},
    
    ]
    }
    }
    ```


