# DescribeZones

调用DescribeZones查询指定地域的可用区信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Slb&api=DescribeZones&type=RPC&version=2014-05-15)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|DescribeZones|要执行的操作。

 取值：**DescribeZones**。 |
|RegionId|String|是|cn-hangzhou|负载均衡实例地域ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Zones|Array of Zone| |可用区列表。 |
|Zone| | | |
|ZoneId|String|cn-hangzhou-b|可用区ID。 |
|LocalName|String|华东 1 可用区|可用区名称。 |
|SlaveZones|Array of SlaveZone| |主可用区对应的备可用区列表。 |
|SlaveZone| | | |
|ZoneId|String|cn-hangzhou-g|备可用区ID。 |
|LocalName|String|华东 1 可用区 G|备可用区名称。 |
|RequestId|String|A48D35FF-440A-4BC0-A4A2-A9BF69B7E43A|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=DescribeZones
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<DescribeZonesResponse>
  <RequestId>3FF183FF-F4AA-40E8-8B5D-90788C6799C2</RequestId>
	  <Zones>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-g</ZoneId>
					          <LocalName>华东 1 可用区 G</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-d</ZoneId>
					          <LocalName>华东 1 可用区 D</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-b</ZoneId>
			      <LocalName>华东 1 可用区 B</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-e</ZoneId>
					          <LocalName>华东 1 可用区 E</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-d</ZoneId>
			      <LocalName>华东 1 可用区 D</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-f</ZoneId>
					          <LocalName>华东 1 可用区 F</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-d</ZoneId>
					          <LocalName>华东 1 可用区 D</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-e</ZoneId>
			      <LocalName>华东 1 可用区 E</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-e</ZoneId>
					          <LocalName>华东 1 可用区 E</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-f</ZoneId>
			      <LocalName>华东 1 可用区 F</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-h</ZoneId>
					          <LocalName>华东 1 可用区 H</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-b</ZoneId>
					          <LocalName>华东 1 可用区 B</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-g</ZoneId>
			      <LocalName>华东 1 可用区 G</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-g</ZoneId>
					          <LocalName>华东 1 可用区 G</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-h</ZoneId>
			      <LocalName>华东 1 可用区 H</LocalName>
		    </Zone>
	  </Zones>
</DescribeZonesResponse>
```

`JSON` 格式

```
{
    "RequestId": "3FF183FF-F4AA-40E8-8B5D-90788C6799C2", 
    "Zones": {
        "Zone": [
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-g", 
                            "LocalName": "华东 1 可用区 G"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-d", 
                            "LocalName": "华东 1 可用区 D"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-b", 
                "LocalName": "华东 1 可用区 B"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-e", 
                            "LocalName": "华东 1 可用区 E"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-d", 
                "LocalName": "华东 1 可用区 D"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-f", 
                            "LocalName": "华东 1 可用区 F"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-d", 
                            "LocalName": "华东 1 可用区 D"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-e", 
                "LocalName": "华东 1 可用区 E"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-e", 
                            "LocalName": "华东 1 可用区 E"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-f", 
                "LocalName": "华东 1 可用区 F"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-h", 
                            "LocalName": "华东 1 可用区 H"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-b", 
                            "LocalName": "华东 1 可用区 B"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-g", 
                "LocalName": "华东 1 可用区 G"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-g", 
                            "LocalName": "华东 1 可用区 G"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-h", 
                "LocalName": "华东 1 可用区 H"
            }
        ]
    }
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidParameter|Illegal parameter, query.namespace is not auth.|query.namespace未授权，请您先授权再操作。|

访问[错误中心](https://error-center.aliyun.com/status/product/Slb)查看更多错误码。

