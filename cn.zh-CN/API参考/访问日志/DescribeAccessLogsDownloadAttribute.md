# DescribeAccessLogsDownloadAttribute {#reference_k2w_gjl_l2b .reference}

查询访问日志转发规则。

## 调试 {#section_fyn_t1b_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DescribeAccessLogsDownloadAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_md3_jjl_l2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：DescribeAccessLogsDownloadAttribute

|
|RegionId|String|是|SLB实例所在的Region。|
|LogType|String|否|取值为layer4或者layer7，四层或者七层访问日志，默认为layer7。|
|PageNumber|int|否|默认为1，最小值为1。|
|PageSize|int|否|默认为20，最小值为1，最大值为50。|

## 请求示例 {#section_jpk_bll_l2b .section}

```

https://slb.aliyuncs.com?Action=ModifyVServerGroupBackendServers
&RegionId=cn-hangzhou
&LogType=layer7
```

## 返回示例 {#section_mvj_dll_l2b .section}

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    	<Count>1</Count>
    	<LogsDownloadAttributes>
    		<LogsDownloadAttribute>
    			<LoadBalancerId>lb-bp1sof7s257tuo1ofrzzc</LoadBalancerId>
    			<LogProject>test-log-project</LogProject>
    			<LogStore>test-log-store</LogStore>
    			<LogType>layer7</LogType>
    			<Region>cn-hangzhou</Region>
    			<RoleArn>acs:ram::16559286049xxxxxx7:role/aliyunlogwriteonlyrole</RoleArn>
    		</LogsDownloadAttribute>
    	</LogsDownloadAttributes>
    	<PageNumber>1</PageNumber>
    	<PageSize>20</PageSize>
    	<RequestId>FC1F244F-A20E-43F3-9BA1-C21149157243</RequestId>
    	<TotalCount>1</TotalCount>
    ```

-   JSON格式

    ```
    
    {
    "Count": 1,
    "LogsDownloadAttributes": {
    "LogsDownloadAttribute": [
    {
    "LoadBalancerId": "lb-bp1sof7s257tuo1ofrzzc",
    "LogProject": "test-log-project",
    "LogStore": "test-log-store",
    "LogType": "layer7",
    "Region": "cn-hangzhou",
    "RoleArn": "acs:ram::165592860491xxxx7:role/aliyunlogwriteonlyrole"
    }
    ]
    },
    "PageNumber": 1,
    "PageSize": 20,
    "RequestId": "FC1F244F-A20E-43F3-9BA1-C21149157243",
    "TotalCount": 1
    }
    ```


