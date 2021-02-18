# DescribeZones

Queries the zones in a region.

## Make the API call

[You can use OpenAPI Explorer to make API calls, search for API calls, perform debugging, and generate SDK example code.](https://api.aliyun.com/#product=Slb&api=DescribeZones&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeZones|The name of this action.

 Value: **DescribeZones** |
|RegionId|String|Yes|cn-hangzhou|The ID of the region to be queried. |
|OwnerAccount|String|No| | |

## Response parameters

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|RequestId|String|A48D35FF-440A-4BC0-A4A2-A9BF69B7E43A|The ID of the request. |
|Zones|Array| |The list of zones. |
|ZoneId|String|cn-hangzhou-b|The ID of the zone. |
|LocalName|String|China East 1 Zone B|The name of the zone. |
|SlaveZones|Array| |The list of secondary zones. |
|ZoneId|String|cn-hangzhou-g|The ID of the secondary zone. |
|LocalName|String|China East 1 Zone G|The name of the secondary zone. |

## Examples

Request example

```

http(s)://[Endpoint]/? Action=DescribeZones
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response example

`JSON` format

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
                            "LocalName": "China East 1 Zone G"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-d", 
                            "LocalName": "China East 1 Zone D"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-b", 
                "LocalName": "China East 1 Zone B"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-e", 
                            "LocalName": "China East 1 Zone E"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-d", 
                "LocalName": "China East 1 Zone D"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-f", 
                            "LocalName": "China East 1 Zone F"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-d", 
                            "LocalName": "China East 1 Zone D"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-e", 
                "LocalName": "China East 1 Zone E"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-e", 
                            "LocalName": "China East 1 Zone E"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-f", 
                "LocalName": "China East 1 Zone F"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-h", 
                            "LocalName": "China East 1 Zone H"
                        }, 
                        {
                            "ZoneId": "cn-hangzhou-b", 
                            "LocalName": "China East 1 Zone B"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-g", 
                "LocalName": "China East 1 Zone G"
            }, 
            {
                "SlaveZones": {
                    "SlaveZone": [
                        {
                            "ZoneId": "cn-hangzhou-g", 
                            "LocalName": "China East 1 Zone G"
                        }
                    ]
                }, 
                "ZoneId": "cn-hangzhou-h", 
                "LocalName": "China East 1 Zone H"
            }
        ]
    }
}

```

`XML` format

```
<DescribeZonesResponse>
  <RequestId>3FF183FF-F4AA-40E8-8B5D-90788C6799C2</RequestId>
	  <Zones>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-g</ZoneId>
					          <LocalName>China East 1 Zone G</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-d</ZoneId>
					          <LocalName>China East 1 Zone D</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-b</ZoneId>
			      <LocalName>China East 1 Zone B</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-e</ZoneId>
					          <LocalName>China East 1 Zone E</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-d</ZoneId>
			      <LocalName>China East 1 Zone D</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-f</ZoneId>
					          <LocalName>China East 1 Zone F</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-d</ZoneId>
					          <LocalName>China East 1 Zone D</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-e</ZoneId>
			      <LocalName>China East 1 Zone E</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-e</ZoneId>
					          <LocalName>China East 1 Zone E</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-f</ZoneId>
			      <LocalName>China East 1 Zone F</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-h</ZoneId>
					          <LocalName>China East 1 Zone H</LocalName>
				        </SlaveZone>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-b</ZoneId>
					          <LocalName>China East 1 Zone B</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-g</ZoneId>
			      <LocalName>China East 1 Zone G</LocalName>
		    </Zone>
		    <Zone>
			      <SlaveZones>
				        <SlaveZone>
					          <ZoneId>cn-hangzhou-g</ZoneId>
					          <LocalName>China East 1 Zone G</LocalName>
				        </SlaveZone>
			      </SlaveZones>
			      <ZoneId>cn-hangzhou-h</ZoneId>
			      <LocalName>China East 1 Zone H</LocalName>
		    </Zone>
	  </Zones>
</DescribeZonesResponse>
```

## Errors

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter|Illegal parameter, query.namespace is not auth.|The query.namespace parameter is not authorized.|

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

