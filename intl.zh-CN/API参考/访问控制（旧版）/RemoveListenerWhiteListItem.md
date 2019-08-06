# RemoveListenerWhiteListItem {#doc_api_Slb_RemoveListenerWhiteListItem .reference}

调用RemoveListenerWhiteListItem删除监听白名单中的IP。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=RemoveListenerWhiteListItem&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveListenerWhiteListItem|要执行的操作。

 取值：**RemoveListenerWhiteListItem**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|ListenerPort|Integer|是|80|监听端口。

 |
|LoadBalancerId|String|是|lb-8vb86hxixo8lvsja86jaz|负载均衡实例的ID。

 |
|SourceItems|String|是|1.1.1.1|访问控制列表。支持输入IP地址或IP地址段（CIDR block形式），多个IP地址或地址段用逗号（,）分隔。

 **说明：** 如果所有IP都被删除，则无法访问该监听。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|CEF72CEB-54B6-4AE8-B225-F876FF7BA984|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=RemoveListenerWhiteListItem
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&SourceItems=1.1.1.1
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveListenerWhiteListItemResponse>
		  <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</RemoveListenerWhiteListItemResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":" CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

