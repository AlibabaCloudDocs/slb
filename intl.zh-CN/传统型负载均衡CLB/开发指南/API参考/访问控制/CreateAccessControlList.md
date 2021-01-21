# CreateAccessControlList

调用CreateAccessControlList创建访问控制策略组。

您可以创建多个访问控制策略组，每个策略组可包含多个IP地址条目或IP地址段条目。访问控制策略组的限制如下：

-   每个地域单账号可创建50个访问控制策略组
-   单账号每次可添加50条IP地址条目
-   每个访问控制策略组可包含300天条目
-   每个监听可绑定50个访问控制策略组

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=CreateAccessControlList&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|CreateAccessControlList|要执行的操作，取值：**CreateAccessControlList** |
|AclName|String|是|rule1|访问控制策略组名称，长度限制为1~80个字符，只支持中文、字母、数字和半角句号（.）、短划线（-）、正斜线（/）和下划线（\_）。访问控制策略组名称必须为地域内唯一。 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。 |
|AddressIPVersion|String|否|ipv4|IP版本，可以设置为**ipv4**或者**ipv6**。

 **说明：** 目前支持创建IPv6实例且实例类型必须为性能保障型实例的可用区如下：华东1地域的E、F两个可用区、华北2地域的F、G两个可用区、华东2地域的所有可用区和华南1地域的D、E两个可用区。 |
|ResourceGroupId|String|否|rg-atstuj3rt\*\*\*\*\*\*|访问控制策略组所在的资源组ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AclId|String|acl-rj9xpxzcwxrukois\*\*\*\*\*\*\*|访问控制策略组ID。 |
|RequestId|String|988CB45E-1643-48C0-87B4-928DDF77EA49|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=CreateAccessControlList
&AclName=rule1
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<CreateAccessControlListResponse>
    <RequestId>988CB45E-1643-48C0-87B4-928DDF77EA49</RequestId>
    <AclId>acl-rj9xpxzcwxrukois******</AclId>
</CreateAccessControlListResponse>
```

`JSON` 格式

```
{
    "AclId": "acl-rj9xpxzcwxrukoi******",
    "RequestId": "988CB45E-1643-48C0-87B4-928DDF77EA49"
}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

