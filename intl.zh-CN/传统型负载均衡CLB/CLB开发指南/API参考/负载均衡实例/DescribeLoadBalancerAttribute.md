# DescribeLoadBalancerAttribute

调用DescribeLoadBalancerAttribute查询指定负载均衡实例的详细信息。如果后端设置在虚拟服务器组下面，请调用DescribeVServerGroupAttribute查询。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeLoadBalancerAttribute&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeLoadBalancerAttribute|要执行的操作。

 取值：**DescribeLoadBalancerAttribute**。 |
|LoadBalancerId|String|是|lb-bp1b6c719dfa08ex\*\*\*\*\*|负载均衡实例ID。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例的地域ID。

 您可以从[地域和可用区](~~40654~~)列表或通过调用[DescribeRegions](~~25609~~)接口查询地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|LoadBalancerId|String|lb-bp1o94dp5i6ea\*\*\*\*\*\*\*|负载均衡实例的ID。 |
|RegionId|String|cn-hangzhou|负载均衡实例所在地域ID。 |
|RegionIdAlias|String|hangzhou|负载均衡实例所属的地域别名。 |
|LoadBalancerName|String|lb-instance-test|负载均衡实例的名称。 |
|LoadBalancerStatus|String|active|负载均衡实例状态：

 -   **inactive**：实例已停止，此状态的实例监听不会再转发流量。
-   **active**：实例运行中，实例创建后，默认状态为**active**。
-   **locked**：实例已锁定，实例已经欠费或被阿里云锁定。 |
|Address|String|42.XX.XX.6|负载均衡实例的服务地址。 |
|AddressType|String|internet|负载均衡实例的地址类型。 |
|NetworkType|String|vpc|负载均衡实例的网络类型。 |
|VpcId|String|vpc-25dvzy9f8\*\*\*\*\*|私网负载均衡实例的专有网络ID。 |
|Bandwidth|Integer|5|按带宽计费的公网型实例的带宽峰值。 |
|CreateTime|String|2017-08-31T02:49:05Z|负载均衡实例的创建时间。 |
|ListenerPorts|List|80|负载均衡实例前端使用的端口。 |
|ListenerPortsAndProtocol|Array of ListenerPortAndProtocol| |负载均衡实例前端使用的端口和协议。 |
|ListenerPortAndProtocol| | | |
|ListenerPort|Integer|443|负载均衡实例前端使用的端口。 |
|ListenerProtocol|String|https|负载均衡实例前端使用的协议。 |
|Description|String|监听描述。|负载均衡监听端口和协议描述。 |
|ForwardPort|Integer|80|转发到的目的监听端口，必须是已经存在的HTTPS监听端口。 |
|ListenerForward|String|yes|是否启用监听转发。 |
|BackendServers|Array of BackendServer| |负载均衡实例的后端服务器列表。 |
|BackendServer| | | |
|ServerId|String|i-djghr2\*\*\*\*|后端服务器实例ID。 |
|Weight|Integer|90|后端服务器的权重。 |
|Description|String|用来接收转发请求的后端服务器|后端服务器描述。 |
|Type|String|ecs|后端服务器类型。 |
|MasterZoneId|String|cn-hangzhou-b|负载均衡实例的主可用区ID。 |
|AddressIPVersion|String|ipv4|IP版本。取值：**ipv4**或**ipv6**。 |
|AutoReleaseTime|Long|1513947075000|释放时间的时间戳。 |
|CreateTimeStamp|Long|1504147745000|负载均衡实例创建时间戳。 |
|DeleteProtection|String|off|是否开启实例删除保护。

 取值：**on**或**off**。 |
|EndTime|String|2999-09-08T16:00:00Z|负载均衡实例结束时间。 |
|EndTimeStamp|Long|32493801600000|负载均衡实例结束时间戳。 |
|InternetChargeType|String|paybybandwidth|公网类型实例付费方式。

 取值：

 -   **paybybandwidth**：按带宽计费。
-   **paybytraffic**：按流量计费（默认值）。 |
|ListenerPortsAndProtocal|Array of ListenerPortAndProtocal| |监听端口或协议。 |
|ListenerPortAndProtocal| | | |
|ListenerPort|Integer|443|负载均衡实例前端使用的端口。 |
|ListenerProtocal|String|http|负载均衡实例前端使用的协议。 |
|LoadBalancerSpec|String|slb.s2.small|负载均衡实例的性能规格。 |
|ModificationProtectionReason|String|托管实例|设置修改保护状态的原因，长度为1~80个字符，必须以字母或中文开头，支持数字、半角句号（.）、下划线（\_）和短划线（-）。

 **说明：** 仅在`ModificationProtectionStatus`为**ConsoleProtection**时有效。 |
|ModificationProtectionStatus|String|ConsoleProtection|负载均衡修改保护状态：

 -   **NonProtection**：不限制修改保护，设置后会清空之前设置的`ModificationProtectionReason`。
-   **ConsoleProtection**：实例控制台修改保护状态。 |
|PayType|String|PrePay|负载均衡实例付费类型，取值**PayOnDemand**或**PrePay**。 |
|RenewalCycUnit|String|Month|自动续费周期，取值：**Year**或**Month**（默认值）。

 仅在**RenewalStatus**为**AutoRenewal**时有效。 |
|RenewalDuration|Integer|1|自动续费时长，仅在**RenewalStatus**为**AutoRenewal**时有效.

 -   **PeriodUnit**为**Year**时，取值：**1**、**2**或**3**。
-   **PeriodUnit**为**Month**时，取值：**1**、**2**、**3**或**6**。 |
|RenewalStatus|String|AutoRenewal|续费状态，取值：

 -   **AutoRenewal**：自动续费。
-   **Normal**：非自动续费，您需要自行续费负载均衡实例。
-   **NotRenewal**：不再续费。返回该值后，系统不再发送到期提醒，只在到期前第三天发送不续费提醒。 |
|RequestId|String|365F4154-92F6-4AE4-92F8-7FF34B540710|请求ID。 |
|ResourceGroupId|String|rg-atstuj3rtop\*\*\*\*\*|企业资源组ID。 |
|SlaveZoneId|String|cn-hangzhou-d|负载均衡实例的备可用区ID。 |
|VSwitchId|String|vsw-255ecrwq5\*\*\*\*\*|私网负载均衡实例的交换机ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeLoadBalancerAttribute
&LoadBalancerId=lb-bp1b6c719dfa08ex*****
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<DescribeLoadBalancerAttributeResponse>
  <RenewalDuration>1</RenewalDuration>
  <EndTime>2999-09-08T16:00:00Z</EndTime>
  <Address>42.250.6.**</Address>
  <ResourceGroupId>rg-atstuj3rtop*****</ResourceGroupId>
  <ListenerPortsAndProtocal>
        <ListenerPortAndProtocal>
              <ListenerPort>443</ListenerPort>
              <ListenerProtocal>http</ListenerProtocal>
        </ListenerPortAndProtocal>
  </ListenerPortsAndProtocal>
  <AddressIPVersion>ipv4</AddressIPVersion>
  <LoadBalancerId>lb-bp1o94dp5i6ea*******</LoadBalancerId>
  <ListenerPortsAndProtocol>
        <ListenerPortAndProtocol>
              <ListenerForward>yes</ListenerForward>
              <ListenerPort>443</ListenerPort>
              <Description>监听描述。</Description>
              <ForwardPort>80</ForwardPort>
              <ListenerProtocol>https</ListenerProtocol>
        </ListenerPortAndProtocol>
  </ListenerPortsAndProtocol>
  <BackendServers>
        <BackendServer>
              <Type>ecs</Type>
              <Description>用来接收转发请求的后端服务器</Description>
              <ServerId>i-djghr2****</ServerId>
              <Weight>90</Weight>
        </BackendServer>
  </BackendServers>
  <ModificationProtectionStatus>ConsoleProtection</ModificationProtectionStatus>
  <LoadBalancerSpec>slb.s2.small</LoadBalancerSpec>
  <NetworkType>vpc</NetworkType>
  <Bandwidth>5</Bandwidth>
  <ModificationProtectionReason>托管实例</ModificationProtectionReason>
  <MasterZoneId>cn-hangzhou-b</MasterZoneId>
  <ListenerPorts>
        <ListenerPort>80</ListenerPort>
  </ListenerPorts>
  <RequestId>365F4154-92F6-4AE4-92F8-7FF34B540710</RequestId>
  <CreateTime>2017-08-31T02:49:05Z</CreateTime>
  <VSwitchId>vsw-255ecrwq5*****</VSwitchId>
  <RenewalStatus>AutoRenewal</RenewalStatus>
  <RenewalCycUnit>Month</RenewalCycUnit>
  <PayType>PrePay</PayType>
  <SlaveZoneId>cn-hangzhou-d</SlaveZoneId>
  <InternetChargeType>paybybandwidth</InternetChargeType>
  <RegionIdAlias>hangzhou</RegionIdAlias>
  <LoadBalancerName>lb-instance-test</LoadBalancerName>
  <DeleteProtection>off</DeleteProtection>
  <VpcId>vpc-25dvzy9f8*****</VpcId>
  <EndTimeStamp>32493801600000</EndTimeStamp>
  <RegionId>cn-hangzhou</RegionId>
  <AddressType>internet</AddressType>
  <LoadBalancerStatus>active</LoadBalancerStatus>
  <CreateTimeStamp>1504147745000</CreateTimeStamp>
  <AutoReleaseTime>1513947075</AutoReleaseTime>
</DescribeLoadBalancerAttributeResponse>
```

`JSON`格式

```
{"RenewalDuration":"1",
"EndTime":"2999-09-08T16:00:00Z",
"Address":"42.250.6.**",
"ResourceGroupId":"rg-atstuj3rtop*****",
"ListenerPortsAndProtocal":
{
    "ListenerPortAndProtocal":
    [
        {
            "ListenerPort":"443",
            "ListenerProtocal":"http"
            }
            ]
            },
            
            "AddressIPVersion":"ipv4",
            "LoadBalancerId":"lb-bp1o94dp5i6ea*******",
            "ListenerPortsAndProtocol":
            {
                "ListenerPortAndProtocol":
            [
                {
                    "ListenerForward":"yes",
                    "ListenerPort":"443",
                    "Description":"监听描述。",
                    "ForwardPort":"80",
                    "ListenerProtocol":"https"
                    }
                    ]
                    },
                    "BackendServers":
                    {
                        "BackendServer":
                        [
                            {
                                "Type":"ecs",
                                "Description":"用来接收转发请求的后端服务器",
                                "ServerId":"i-djghr2****",
                                "Weight":"90"
                                }
                                ]
                                },
                                "ModificationProtectionStatus":"ConsoleProtection",
                                "LoadBalancerSpec":"slb.s2.small",
                                "NetworkType":"vpc",
                                "Bandwidth":"5",
                                "ModificationProtectionReason":"托管实例",
                                "MasterZoneId":"cn-hangzhou-b",
                                "ListenerPorts":
                                {
                                    "ListenerPort":"80"
                                    },
                                    "RequestId":"365F4154-92F6-4AE4-92F8-7FF34B540710",
                                    "CreateTime":"2017-08-31T02:49:05Z",
                                    "VSwitchId":"vsw-255ecrwq5*****",
                                    "RenewalStatus":"AutoRenewal",
                                    "RenewalCycUnit":"Month",
                                    "PayType":"PrePay",
                                    "SlaveZoneId":"cn-hangzhou-d",
                                    "InternetChargeType":"paybybandwidth",
                                    "RegionIdAlias":"hangzhou",
                                    "LoadBalancerName":"lb-instance-test",
                                    "DeleteProtection":"off",
                                    "VpcId":"vpc-25dvzy9f8*****",
                                    "EndTimeStamp":"32493801600000",
                                    "RegionId":"cn-hangzhou",
                                    "AddressType":"internet",
                                    "LoadBalancerStatus":"active",
                                    "CreateTimeStamp":"1504147745000",
                                    "AutoReleaseTime":"1513947075"}
```

## 错误码

访问[错误中心](https://error-center.alibabacloud.com/status/product/Slb)查看更多错误码。

