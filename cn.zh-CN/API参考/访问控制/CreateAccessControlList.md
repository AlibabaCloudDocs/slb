# CreateAccessControlList {#doc_api_Slb_CreateAccessControlList .reference}

调用CreateAccessControlList创建访问控制策略组。

您可以创建多个访问控制策略组，每个策略组可包含多个IP地址条目或IP地址段条目。访问控制策略组的限制如下：

-   每个地域单账号可创建的访问控制策略组个数：50
-   单账号每次可添加的IP地址条目个数：50
-   每个访问控制策略组可包含的条目个数：300
-   每个监听可绑定的访问控制策略组个数：50

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=CreateAccessControlList)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAccessControlList|要执行的操作，取值：**CreateAccessControlList**

 |
|AclName|String|是|rule1|访问控制策略组名称，需要保证Region内唯一。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 |
|AddressIPVersion|String|否|ipv4|IP版本，可以设置为ipv4或者ipv6。

 **说明：** 目前支持创建IPv6实例且实例类型必须为性能保障型实例的可用区如下：华东1地域的E、F两个可用区、华北2地域的F、G两个可用区、华东2地域的所有可用区和华南1地域的D、E两个可用区。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AclId|String|acl-rj9xpxzcwxrukois65yw3|访问控制策略组ID。

 |
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=CreateAccessControlList
&AclName=rule1
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateAccessControlListResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
  <AclId>acl-rj9xpxzcwxrukois65yw3</AclId>
</CreateAccessControlListResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"AclId":"acl-rj9xpxzcwxrukois65yw3",
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

