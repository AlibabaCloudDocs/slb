# DescribeRealtimeLogs {#reference_z52_r3j_p2b .reference}

查询健康检查日志。

## 调试 {#section_fdx_qbb_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeRealtimeLogs)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_epv_s3j_p2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DescribeRealtimeLogs

|
|RegionId|String|是|需要查询健康检查日志的Region。|
|LogType|String|是|需要查看的日志类型。取值：HealthLog。

|
|LogStartTime|String|是|需要获取日志的起始时间。格式为UTC时区 yyyy-mm-ddThh :mm :ssZ。

支持获取到当前时间前三天内的日志。

|
|LogEndTime|String|是|需要获取日志的结束时间。格式为UTC时区 yyyy-mm-ddThh :mm :ssZ。

支持获取截止到当前时间的日志。

|
|LoadBalancerId|String|否|需要查询的SLB实例ID，作为日志查询的过滤值。|
|RoleName|String|否|用户允许SLB扮演的RAM角色名称。默认值：aliyunslbdefaultrole

|

## 返回参数 {#section_yxb_gnj_p2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求的ID。|
|PageSize|String|分页显示，返回结果的页码。|
|PageNumber|String|分页显示，返回结果每页的日志个数。|
|Progress|String|当前响应中的日志是否是全部查询结果，如果返回Progressing，则继续使用相同参数调用此接口后，可以得到全部日志。|
|LBRealTimeLogsSet|Set|实时日志集合，详见[表 1](#table_ymn_2sj_p2b)。|

|名称|类型|描述|
|--|--|--|
|LogDetail|String|详细日志信息。|

## 示例 {#section_glr_qsj_p2b .section}

**请求示例**

```

https://slb.aliyuncs.com?Action=DescribeRealtimeLogs
&RegionId=cn-hangzhou
&LogType=HealthLog
&LogStartTime=2017-06-13T11:50:20Z
&LogEndTime=2017-06-13T12:50:20Z
&<公共请求参数>
```

```

https://slb.aliyuncs.com?Action=DescribeRealtimeLogs
&RegionId=cn-hangzhou
&LogType=HealthLog
&LogStartTime=2017-06-13T11:50:20Z
&LogEndTime=2017-06-13T12:50:20Z
&<公共请求参数>
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
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

-   JSON格式

    ```
    
    {
    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
    "PageNumber":"1",
    "PageSize":"50",
    "Progress":"Complete",
    "LBRealTimeLogsSet": {
    "LBRealTimeLog": [
    {"LogDetail": "2017-05-18 23:04:15 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error"},
    {“LogDetail": "2017-05-18 23:04:16 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error"},
    {"LogDetail": "2017-05-18 23:04:12 Instance ID: lb-2zeigiozw0atyyyhds1b2; 59.110.89.231:544 to 10.44.33.210:22 abnormal; cause: http parse status line error"}
    ]
    }
    }
    ```


