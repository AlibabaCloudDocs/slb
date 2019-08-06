# DeleteAccessLogsDownloadAttribute {#reference_gkx_ydf_l2b .reference}

删除访问日志转发规则。

## 调试 {#section_ayy_41b_rfb .section}

```
点击[这里](https://api.aliyun.com/#product=Slb&api=DeleteAccessLogsDownloadAttribute)在OpenAPI Explorer中可视化调试，并自动生成SDK调用示例。
```

## 请求参数 {#section_nnh_12f_l2b .section}

|名称|类型|是否必须|描述|
|--|--|----|--|
|Action|String|是|要执行的操作，取值：SetAccessLogsDownloadAttribute

|
|RegionId|String|是|SLB实例所在的Region。|
|LogsDownloadAttributes|String|是|访问日志转发规则，具体请参见[表 1](#table_bqj_3dk_l2b)。|

|名称|类型|是否必须|描述|
|--|--|----|--|
|LoadBalancerId|String|是|需要转发访问日志的LoadBalancerId。|

## 返回参数 {#section_vbn_43k_l2b .section}

|名称|类型|描述|
|--|--|--|
|RequestId|String|请求ID。|

## 请求示例 {#section_vbd_bjk_l2b .section}

```

https://slb.aliyuncs.com?Action=DeleteAccessLogsDownloadAttribute
&RegionId=cn-hangzhou
& LogsDownloadAttributes =[
{ "LoadBalancerId":"lb-uf68ps3rekbljmdb0cxp7" }]
```

## 返回示例 {#section_ilj_2jk_l2b .section}

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8" ?>
    	<RequestId>9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C</RequestId>
    ```

-   JSON格式

    ```
    
    {
    "RequestId":"9DEC9C28-AB05-4DDF-9A78-6B08EC9CE18C"
    }
    ```


