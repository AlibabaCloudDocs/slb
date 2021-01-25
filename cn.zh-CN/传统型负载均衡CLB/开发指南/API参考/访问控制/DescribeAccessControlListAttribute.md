# DescribeAccessControlListAttribute

调用DescribeAccessControlListAttribute查询访问控制策略组的配置。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlListAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeAccessControlListAttribute|要执行的操作，取值：**DescribeAccessControlListAttribute**。 |
|AclId|String|是|acl-bp1l0k\*\*\*\*\*\*\*\*kzet04s|要查询的访问控制策略组ID。 |
|RegionId|String|是|cn-hangzhou|访问控制策略组的地域ID。

 您可以通过调用[DescribeRegions](~~27584~~)接口查询地域ID。 |
|AclEntryComment|String|否|test|访问控制策略组的条目的备注信息。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|AclEntrys|Array of AclEntry| |访问控制策略组的信息列表。 |
|AclEntry| | | |
|AclEntryComment|String|访问控制条目。|访问控制条目备注。 |
|AclEntryIP|String|192.168.0.1|访问控制条目IP。 |
|AclId|String|acl-bp1l0k\*\*\*\*\*\*\*\*kzet04s|访问控制策略组ID。 |
|AclName|String|doctest|访问控制策略组名称。 |
|AddressIPVersion|String|ipv4|关联的实例的IP类型。 |
|RelatedListeners|Array of RelatedListener| |该访问控制策略组已绑定的监听列表。 |
|RelatedListener| | | |
|AclType|String|white|访问控制的类型：

 -   **black**：黑名单
-   **white**：白名单 |
|ListenerPort|Integer|443|绑定的监听的前端端口。 |
|LoadBalancerId|String|lb-bp13j\*\*\*\*\*\*\*\*1miup|负载均衡实例的ID。 |
|Protocol|String|https|绑定的监听的协议类型。 |
|RequestId|String|C9906A1D-86F7-4C9C-A369-54DA42EF206A|请求ID。 |
|ResourceGroupId|String|rg-\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*|企业资源组ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeAccessControlListAttribute
&AclId=acl-bp1l0k********kzet04s
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeAccessControlListAttributeResponse>
  <AclEntrys>
        <AclEntry>
              <AclEntryIP>192.168.0.1</AclEntryIP>
              <AclEntryComment>访问控制条目。</AclEntryComment>
        </AclEntry>
  </AclEntrys>
  <ResourceGroupId>rg-******************</ResourceGroupId>
  <RequestId>C9906A1D-86F7-4C9C-A369-54DA42EF206A</RequestId>
  <AddressIPVersion>ipv4</AddressIPVersion>
  <AclId>acl-bp1l0k********kzet04s</AclId>
  <RelatedListeners>
        <RelatedListener>
              <ListenerPort>443</ListenerPort>
              <AclType>white</AclType>
              <LoadBalancerId>lb-bp13j********1miup</LoadBalancerId>
              <Protocol>https</Protocol>
        </RelatedListener>
  </RelatedListeners>
  <AclName>doctest</AclName>
</DescribeAccessControlListAttributeResponse>
```

`JSON`格式

```
{
    "AclEntrys":
    {
        "AclEntry":
        [
            {
                "AclEntryIP":"192.168.0.1",
                "AclEntryComment":"访问控制条目。"
                }
                ]
                },
                "ResourceGroupId":"rg-******************",
                "RequestId":"C9906A1D-86F7-4C9C-A369-54DA42EF206A",
                "AddressIPVersion":"ipv4",
                "AclId":"acl-bp1l0k********kzet04s",
                "RelatedListeners":
                {
                    "RelatedListener":
                    [
                        {
                            "ListenerPort":"443",
                            "AclType":"white",
                            "LoadBalancerId":"lb-bp13j********1miup",
                            "Protocol":"https"
                            }
                            ]
                            },
                            "AclName":"doctest"}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

