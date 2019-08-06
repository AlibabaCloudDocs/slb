# DescribeAccessControlListAttribute {#doc_api_Slb_DescribeAccessControlListAttribute .reference}

调用DescribeAccessControlListAttribute查询访问控制策略组的配置。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlListAttribute&type=RPC&version=2014-05-15)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccessControlListAttribute|要执行的操作，取值：**DescribeAccessControlListAttribute**。

 |
|AclId|String|是|acl-bp1l0kk4gxce43kzet04s|要查询的访问控制策略组ID。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|AclEntryComment|String|否|test|访问控制策略组的条目的备注信息。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AclEntrys| | |访问控制策略组的信息列表。

 |
|AclEntryComment|String|访问控制条目。|访问控制条目备注。

 |
|AclEntryIP|String|192.168.0.1|访问控制条目IP。

 |
|AclId|String|acl-bp1l0kk4gxce43kzet04s|访问控制策略组ID。

 |
|AclName|String|doctest|访问控制策略组名称。

 |
|AddressIPVersion|String|ipv4|关联的实例的IP类型。

 |
|RelatedListeners| | |该访问控制策略组已绑定的监听列表。

 |
|AclType|String|white|访问控制的类型：

 -   **black**：黑名单
-   **white**：白名单

 |
|ListenerPort|Integer|443|绑定的监听的前端端口。

 |
|LoadBalancerId|String|lb-bp13jaf5qli5xmgl1miup|负载均衡实例的ID。

 |
|Protocol|String|https|绑定的监听的协议类型。

 |
|RequestId|String|C9906A1D-86F7-4C9C-A369-54DA42EF206A|请求ID。

 |
|ResourceGroupId|String|rg-\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|企业资源组ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=DescribeAccessControlListAttribute
&AclId=acl-bp1l0kk4gxce43kzet04s
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAccessControlListAttributeResponse>
	  <AclId>acl-bp1l0kk4gxce43kzet04s</AclId>
	  <RelatedListeners>
		    <RelatedListener>
			      <AclType>white</AclType>
			      <LoadBalancerId>lb-bp13jaf5qli5xmgl1miup</LoadBalancerId>
			      <Protocol>https</Protocol>
			      <ListenerPort>443</ListenerPort>
		    </RelatedListener>
	  </RelatedListeners>
	  <AclName>doctest</AclName>
	  <RequestId>C9906A1D-86F7-4C9C-A369-54DA42EF206A</RequestId>
	  <AddressIPVersion>ipv4</AddressIPVersion>
</DescribeAccessControlListAttributeResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"AclId":"acl-bp1l0kk4gxce43kzet04s",
	"RequestId":"C9906A1D-86F7-4C9C-A369-54DA42EF206A",
	"AclName":"doctest",
	"RelatedListeners":{
		"RelatedListener":[
			{
				"AclType":"white",
				"LoadBalancerId":"lb-bp13jaf5qli5xmgl1miup",
				"Protocol":"https",
				"ListenerPort":443
			}
		]
	},
	"AddressIPVersion":"ipv4"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

