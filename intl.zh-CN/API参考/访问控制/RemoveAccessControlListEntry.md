# RemoveAccessControlListEntry {#doc_api_859285 .reference}

使用RemoveAccessControlListEntry删除访问控制策略组中的IP条目。

## 调试 {#apiExplorer .section}

单击[这里](https://api.aliyun.com/#product=Slb&api=RemoveAccessControlListEntry)在OpenAPI Explorer中进行可视化调试，并生成SDK代码示例。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|RemoveAccessControlListEntry|要执行的操作，取值：**RemoveAccessControlListEntry**。

 |
|AclId|String|是|acl-bp1l0kk4gxce43kzet04s|访问控制策略组ID。

 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。

 |
|AclEntrys|String|否|\[\{"entry":"10.0.0.0/24","comment":"privaterule1"\}\]|访问控制策略组中要添加的IP条目，可以指定IP地址或IP地址段（CIDR block），多个IP地址/地址段之间用逗号隔开。

 **注意**：如果访问控制策略组关联了监听，不允许删除组内的所有IP条目。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

/?Action=RemoveAccessControlListEntry
&AclId=acl-bp1l0kk4gxce43kzet04s
&RegionId=cn-hangzhou
&AclEntrys=[{"entry":"10.0.0.0/24","comment":"privaterule1"}]
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<RemoveAccessControlListEntryResponse>
  <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
</RemoveAccessControlListEntryResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

异常返回示例

## 错误码 { .section}

[查看本产品错误码](https://error-center.aliyun.com/status/product/Slb)

