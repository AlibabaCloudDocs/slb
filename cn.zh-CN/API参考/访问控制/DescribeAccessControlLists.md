# DescribeAccessControlLists {#doc_api_Slb_DescribeAccessControlLists .reference}

调用DescribeAccessControlLists查询已创建的访问控制策略组。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlLists)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccessControlLists|要执行的操作，取值：**DescribeAccessControlLists**。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|AclName|String|否|rule1|访问控制策略组名称。

 |
|AddressIPVersion|String|否|ipv4|访问控制策略组绑定的实例的IP类型。取值：

 -   **ipv4**：负载均衡实例的IP地址是IPv4类型。
-   **ipv6**：负载均衡实例的IP地址是IPv6类型。

 |
|PageNumber|Integer|否|1|列表的页码，默认值为1。

 |
|PageSize|Integer|否|10|分页查询时每页的行数，最大值为50，默认值为10。

 |
|ResourceGroupId|String|否|rg-atstuj3rtoptyui|企业资源组ID。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Acls| | |查询到的访问控制策略组列表。

 |
|└AclId|String|acl-bp1l0kk4gxce43kzet04s|访问控制策略组ID。

 |
|└AclName|String|rule1|访问控制策略组名称。

 |
|└AddressIPVersion|String|ipv4|关联的负载均衡实例的IP地址类型。

 |
|RequestId|String|B646EF-6147-4566|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=DescribeAccessControlLists
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeAccessControlListsResponse>
  <RequestId>3CB646EF-6147-4566-A9D9-CE8FBE86F971</RequestId>
  <Acls>
    <Acl>
      <AclId>acl-bp1j9vn2g7wm9wn0xassu</AclId>
      <AclName>test</AclName>
      <AddressIPVersion>ipv4</AddressIPVersion>
    </Acl>
    <Acl>
      <AclId>acl-bp1l0kk4gxce43kzet04s</AclId>
      <AclName>doctest</AclName>
      <AddressIPVersion>ipv4</AddressIPVersion>
    </Acl>
  </Acls>
</DescribeAccessControlListsResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"3CB646EF-6147-4566-A9D9-CE8FBE86F971",
	"Acls":{
		"Acl":[
			{
				"AclId":"acl-bp1j9vn2g7wm9wn0xassu",
				"AclName":"test",
				"AddressIPVersion":"ipv4"
			},
			{
				"AclId":"acl-bp1l0kk4gxce43kzet04s",
				"AclName":"doctest",
				"AddressIPVersion":"ipv4"
			}
		]
	}
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

