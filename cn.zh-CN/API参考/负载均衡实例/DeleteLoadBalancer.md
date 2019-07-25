# DeleteLoadBalancer {#doc_api_Slb_DeleteLoadBalancer .reference}

调用DeleteLoadBalancer删除后付费的负载均衡实例。

**说明：** 如果负载均衡实例上还有监听或者绑定了相应的标签，也会一并被删除。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DeleteLoadBalancer&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DeleteLoadBalancer|要执行的操作。

 取值：**DeleteLoadBalancer**。

 |
|LoadBalancerId|String|是|lb-bp1h66tp5uat84khmqc9e|负载均衡实例的ID。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DeleteLoadBalancer
&LoadBalancerId=lb-bp1h66tp5uat84khmqc9e
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteLoadBabalancerResponse>
	  <RequestId>E3F602B8-A162-4683-A7EC-49364E597259</RequestId>
</DeleteLoadBabalancerResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"0D9B7343-AC1F-498C-A18A-78FE14A7C3A3"
}
```

如果删除的实例开启了删除保护，系统会报以下错误：

-   JSON格式

    ```
    
        {
    	"RequestId": "7B7AB375-1EA6-4A18-9D1C-F258F2D57638",
    	"HostId": "slb.aliyuncs.com",
    	"Code": "OperationDenied.DeleteProtectionIsOn",
    	"Message": "The loadbalancer can't be deleted due to DeleteProtection is enabled."
         }
       
    ```

-   XML格式

    ```
    
       <?xml version="1.0" encoding="UTF-8" ?>
            <DeleteLoadBabalancerResponse>
    	<RequestId>7B7AB375-1EA6-4A18-9D1C-F258F2D57638</RequestId>
    	<HostId>slb.aliyuncs.com</HostId>
    	<Code>OperationDenied.DeleteProtectionIsOn</Code>
    	<Message>The loadbalancer can't be deleted due to DeleteProtection is enabled.</Message>
           </DeleteLoadBabalancerResponse>
       
    ```


## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

