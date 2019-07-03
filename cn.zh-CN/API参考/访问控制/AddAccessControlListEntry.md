# AddAccessControlListEntry {#doc_api_Slb_AddAccessControlListEntry .reference}

调用AddAccessControlListEntry在访问控制策略组中添加IP条目。

每个策略组可包含多个IP地址条目或IP地址段条目，访问控制策略组的条目限制如下：

-   单账号每次可添加的IP地址条目个数：50
-   每个访问控制策略组可包含的条目个数：300

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Slb&api=AddAccessControlListEntry)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|AddAccessControlListEntry|要执行的操作，取值：**AddAccessControlListEntry**。

 |
|AclId|String|是|acl-bp1l0kk4gxce43kze\*\*\*\*\*|访问控制策略组ID。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 |
|AclEntrys|String|否|\[\{"entry":"10.0.0.0/24","comment":"privaterule1"\},\{"entry":"192.168.0.0/16","comment":"privaterule2"\}\]|访问控制策略组中要添加的IP条目，可以指定IP地址或IP地址段（CIDR block），多个IP地址/地址段之间用逗号隔开。

 **说明：** 每次最多可添加50个条目。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA4|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://[Endpoint]/?Action=AddAccessControlListEntry
&AclId=acl-bp1l0kk4gxce43kze*****
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<AddAccessControlListEntryResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
</AddAccessControlListEntryResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

