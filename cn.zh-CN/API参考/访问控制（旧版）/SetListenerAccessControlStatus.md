# SetListenerAccessControlStatus {#doc_api_Slb_SetListenerAccessControlStatus .reference}

调用SetListenerAccessControlStatus是否开启指定监听的白名单访问控制。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=SetListenerAccessControlStatus&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SetListenerAccessControlStatus|要执行的操作。

 取值：**SetListenerAccessControlStatus**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|AccessControlStatus|String|是|open\_white\_list|是否开启访问控制。取值：

 -   **open\_white\_list**：开启白名单访问控制。
-   **close**：关闭白名单访问控制。

 **说明：** 如果开启访问控制后，没有设置白名单则无法访问负载均衡服务。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1-65535**。

 |
|LoadBalancerId|String|是|lb-8vb86hxixo8lvsja86jaz|负载均衡实例的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=SetListenerAccessControlStatus
&AccessControlStatus=open_white_list
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<SetListenerAccessControlStatusResponse>
		  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</SetListenerAccessControlStatusResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

