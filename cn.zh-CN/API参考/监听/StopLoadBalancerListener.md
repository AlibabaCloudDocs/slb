# StopLoadBalancerListener {#slb_api_StopLoadBalancerListener .reference}

停止监听。

在调用该接口时，注意：

-   接口调用成功后，监听进入stopped状态。
-   当监听所属负载均衡实例的状态为locked时，调用此接口会失败。

## 请求参数 {#section_v5w_nds_cz .section}

|名称|类型|是否必须|描述|
|:-|:-|:---|:-|
|Action|String|是|要执行的操作。取值：StopLoadBalancerListener

|
|RegionId|String|是|负载均衡实例的地域。您可以通过调用 DescribeRegions接口获取地域ID。

|
|LoadBalancerId|String|是|负载均衡实例的ID。|
|ListenerPort|Integer|是|负载均衡实例前端使用的端口。取值：1-65535

|

## 返回参数 {#section_ssd_pds_cz .section}

|名称|类型|说明|
|:-|:-|:-|
|RequestId|String|请求ID。|

## 示例 {#section_oxr_pds_cz .section}

**请求示例**

``` {#public}
https://slb.aliyuncs.com/?Action=StopLoadBalancerListener
&LoadBalancerId=lb-t4nj5vuz8ish9emfk1f20
&ListenerPort=80
&公共请求参数
```

**返回示例**

-   XML格式

    ```
    <?xml version="1.0" encoding="UTF-8"?>
    <StopLoadBalancerListenerResponse>
    	<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
    </StopLoadBalancerListenerResponse>
    ```

-   JSON格式

    ```
    {
      "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
    }
    ```


