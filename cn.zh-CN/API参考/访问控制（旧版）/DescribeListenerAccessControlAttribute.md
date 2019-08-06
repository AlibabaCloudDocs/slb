# DescribeListenerAccessControlAttribute {#doc_api_Slb_DescribeListenerAccessControlAttribute .reference}

调用DescribeListenerAccessControlAttribute查询监听的白名单配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeListenerAccessControlAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeListenerAccessControlAttribute|要执行的操作。

 取值：**DescribeListenerAccessControlAttribute**。

 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。

 |
|ListenerPort|Integer|是|80|负载均衡实例前端使用的端口。

 取值：**1~65535**。

 |
|LoadBalancerId|String|是|lb-8vb86hxixo8lvsja86jaz|负载均衡实例的ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AccessControlStatus|String|open\_white\_list|是否开启访问控制：

 -   **open\_white\_list**表示开启白名单访问控制功能。
-   **close**表示关闭访问控制功能。

 |
|SourceItems|String|1.1.1.1,1.1.1.0/24|访问控制列表。

 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeListenerAccessControlAttribute
&ListenerPort=80
&LoadBalancerId=lb-8vb86hxixo8lvsja86jaz
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeListenerAccessControlAttributeResponse>
	  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
	  <AccessControlStatus>open_white_list</AccessControlStatus>
	  <SourceItems>1.1.1.1,1.1.1.0/24</SourceItems>
</DescribeListenerAccessControlAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
	"SourceItems":"1.1.1.1,1.1.1.0/24",
	"AccessControlStatus":"open_white_list"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

