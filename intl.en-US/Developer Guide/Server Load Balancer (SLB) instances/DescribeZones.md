# DescribeZones {#doc_api_Slb_DescribeZones .reference}

Queries the zones in a region.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeZones) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeZones| The name of this action.

 Value: **DescribeZones**

 |
|RegionId|String|Yes|cn-hangzhou-d| The ID of the region.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|Zones| | | The list of available zones.

 |
|└ZoneId|String|cn-hangzhou-b| The ID of the zone.

 |
|└LocalName|String|China East 1 Zone B| The name of the zone.

 |
|└SlaveZones| | | The list of secondary zones.

 |
|└ZoneId|String|cn-hangzhou-g| The ID of the secondary zone.

 |
|└LocalName|String|East China 1 Zone G| The name of the secondary zone.

 |
|RequestId|String|A48D35FF-440A-4BC0-A4A2-A9BF69B7E43A| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/? Action=DescribeZones
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
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

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"3FF183FF-F4AA-40E8-8B5D-90788C6799C2",
	"Zones":{
		"Zone":[
			{
				"ZoneId":"cn-hangzhou-b",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-g",
							"LocalName":"China East 1 Zone G"
						},
						{
							"ZoneId":"cn-hangzhou-d",
							"LocalName":"China East 1 Zone D"
						}
					]
				},
				"LocalName":"China East 1 Zone B"
			},
			{
				"ZoneId":"cn-hangzhou-d",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-e",
							"LocalName":"China East 1 Zone E"
						}
					]
				},
				"LocalName":"China East 1 Zone D"
			},
			{
				"ZoneId":"cn-hangzhou-e",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-f",
							"LocalName":"China East 1 Zone F"
						},
						{
							"ZoneId":"cn-hangzhou-d",
							"LocalName":"China East 1 Zone D"
						}
					]
				},
				"LocalName":"China East 1 Zone E"
			},
			{
				"ZoneId":"cn-hangzhou-f",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-e",
							"LocalName":"China East 1 Zone E"
						}
					]
				},
				"LocalName":"China East 1 Zone F"
			},
			{
				"ZoneId":"cn-hangzhou-g",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-h",
							"LocalName":"China East 1 Zone H"
						},
						{
							"ZoneId":"cn-hangzhou-b",
							"LocalName":"China East 1 Zone B"
						}
					]
				},
				"LocalName":"China East 1 Zone G"
			},
			{
				"ZoneId":"cn-hangzhou-h",
				"SlaveZones":{
					"SlaveZone":[
						{
							"ZoneId":"cn-hangzhou-g",
							"LocalName":"China East 1 Zone G"
						}
					]
				},
				"LocalName":"China East 1 Zone H"
			}
		]
	}
}
```

## Error codes {#section_skq_jkm_yua .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidParameter|Illegal parameter, query.namespace is not auth.|The query.namespace parameter is invalid.|

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

