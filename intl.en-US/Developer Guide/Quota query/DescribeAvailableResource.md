# DescribeAvailableResource {#doc_api_Slb_DescribeAvailableResource .reference}

Queries available resources in a specified region. Resource limits do not apply to users in the whitelist.

**Note:** Only available resources and corresponding zones are returned.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=AddVServerGroupBackendServers) to perform debug operations and generate code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeAvailableResource| The name of this action.

 Value: **DescribeAvailableResource**

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region you want to query.

 |
|AddressIPVersion|String|No|ipv4| Optional. The IP version of the resources to be queried.

 Valid values: **ipv4 | ipv6**

 |
|AddressType|String|No|vpc| Optional. The network type of the resources to be queried.

 Valid values: **vpc | classic-internet | classic-intranet**

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AvailableResources| | | A list of available resources and corresponding zones.

 |
|└MasterZoneId|String|cn-shanghai-a| The primary zone ID.

 |
|└SlaveZoneId|String|cn-shanghai-b| The secondary zone ID.

 |
|└SupportResources| | | The resources available in the corresponding zone.

 |
|└AddressIPVersion|String|ipv4| The IP version of the resources.

 Valid values: **ipv4 | ipv6**

 |
|└AddressType|String|classic\_internet| The network type of the resources.

 Valid values: **vpc | classic-internet | classic-intranet**

 |
|RequestId|String|173B0EEA-22ED-4EE2-91F9-3A1CDDFFBBBA| The ID of the request.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

http(s)://[Endpoint]/?Action=DescribeAvailableResource
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeAvailableResource>
  <RequestId>173B0EEA-22ED-4EE2-91F9-3A1CDDFFBBBA</RequestId>
  <AvailableResources>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-b</SlaveZoneId>
      <MasterZoneId>cn-shanghai-a</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-a</SlaveZoneId>
      <MasterZoneId>cn-shanghai-b</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-c</SlaveZoneId>
      <MasterZoneId>cn-shanghai-b</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-b</SlaveZoneId>
      <MasterZoneId>cn-shanghai-c</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-e</SlaveZoneId>
      <MasterZoneId>cn-shanghai-d</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-f</SlaveZoneId>
      <MasterZoneId>cn-shanghai-e</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv6</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-d</SlaveZoneId>
      <MasterZoneId>cn-shanghai-e</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-e</SlaveZoneId>
      <MasterZoneId>cn-shanghai-f</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-g</SlaveZoneId>
      <MasterZoneId>cn-shanghai-f</MasterZoneId>
    </AvailableResource>
    <AvailableResource>
      <SupportResources>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_internet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>classic_intranet</AddressType>
        </SupportResource>
        <SupportResource>
          <AddressIPVersion>ipv4</AddressIPVersion>
          <AddressType>vpc</AddressType>
        </SupportResource>
      </SupportResources>
      <SlaveZoneId>cn-shanghai-f</SlaveZoneId>
      <MasterZoneId>cn-shanghai-g</MasterZoneId>
    </AvailableResource>
  </AvailableResources>
</DescribeAvailableResource>

```

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"173B0EEA-22ED-4EE2-91F9-3A1CDDFFBBBA",
	"AvailableResources":{
		"AvailableResource":[
			{
				"SlaveZoneId":"cn-shanghai-b",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-a"
			},
			{
				"SlaveZoneId":"cn-shanghai-a",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-b"
			},
			{
				"SlaveZoneId":"cn-shanghai-c",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-b"
			},
			{
				"SlaveZoneId":"cn-shanghai-b",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-c"
			},
			{
				"SlaveZoneId":"cn-shanghai-e",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-d"
			},
			{
				"SlaveZoneId":"cn-shanghai-f",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-e"
			},
			{
				"SlaveZoneId":"cn-shanghai-d",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						},
						{
							"AddressIPVersion":"ipv6",
							"AddressType":"classic_internet"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-e"
			},
			{
				"SlaveZoneId":"cn-shanghai-e",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-f"
			},
			{
				"SlaveZoneId":"cn-shanghai-g",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-f"
			},
			{
				"SlaveZoneId":"cn-shanghai-f",
				"SupportResources":{
					"SupportResource":[
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_internet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"classic_intranet"
						},
						{
							"AddressIPVersion":"ipv4",
							"AddressType":"vpc"
						}
					]
				},
				"MasterZoneId":"cn-shanghai-g"
			}
		]
	}
}
```

## Error codes { .section}

For a list of error codes, visit the [API Error Center](https://error-center.aliyun.com/status/product/Slb).

