# DescribeAvailableResource

Queries resources that are available for purchase in the zones of a region.

**Note:** Only resources that are available for purchase and the corresponding zones are returned.

## Debugging

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Slb&api=DescribeAvailableResource&type=RPC&version=2014-05-15)

## Request parameters

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|Action|String|Yes|DescribeAvailableResource|The operation that you want to perform.

 Set the value to **DescribeAvailableResource**. |
|RegionId|String|Yes|cn-hangzhou|The ID of the region. |
|AddressType|String|No|vpc|The type of network.

 Valid values: **vpc, classic\_internet, and classic\_intranet.**.

 vpc: an internal SLB instance that is deployed in a virtual private cloud \(VPC\).

 classic\_internet: a public-facing SLB instance.

 classic\_intranet: an internal SLB instance that is deployed in a classic network. |
|AddressIPVersion|String|No|ipv4|The type of IP address.

 Valid values: **ipv4 and ipv6**. |

## Response parameters

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|RequestId|String|173B0EEA-22ED-4EE2-91F9-3A1CDDFFBBBA|The ID of the request. |
|AvailableResources|Array| |The zones and the supported resources. |
|MasterZoneId|String|cn-shanghai-a|The primary zone. |
|SlaveZoneId|String|cn-shanghai-b|The secondary zone. |
|SupportResources|Array| |The supported resources. |
|AddressType|String|classic\_internet|The type of network.

 Valid values: **vpc, classic-internet, and classic-intranet**. |
|AddressIPVersion|String|ipv4|The type of IP address.

 Valid values: **ipv4 and ipv6**. |

## Examples

Sample request

```
http(s)://[Endpoint]/? Action=DescribeAvailableResource
&RegionId=cn-hangzhou
&<Common request parameters>
```

Sample success responses

`XML` format

```
<DescribeAvailableResourceResponse>
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
     </DescribeAvailableResourceResponse>
```

`JSON` format

```
{
    "RequestId": "173B0EEA-22ED-4EE2-91F9-3A1CDDFFBBBA", 
    "AvailableResources": {
        "AvailableResource": [
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-b", 
                "MasterZoneId": "cn-shanghai-a"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-a", 
                "MasterZoneId": "cn-shanghai-b"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-c", 
                "MasterZoneId": "cn-shanghai-b"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-b", 
                "MasterZoneId": "cn-shanghai-c"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-e", 
                "MasterZoneId": "cn-shanghai-d"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-f", 
                "MasterZoneId": "cn-shanghai-e"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }, 
                        {
                            "AddressIPVersion": "ipv6", 
                            "AddressType": "classic_internet"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-d", 
                "MasterZoneId": "cn-shanghai-e"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-e", 
                "MasterZoneId": "cn-shanghai-f"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-g", 
                "MasterZoneId": "cn-shanghai-f"
            }, 
            {
                "SupportResources": {
                    "SupportResource": [
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_internet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "classic_intranet"
                        }, 
                        {
                            "AddressIPVersion": "ipv4", 
                            "AddressType": "vpc"
                        }
                    ]
                }, 
                "SlaveZoneId": "cn-shanghai-f", 
                "MasterZoneId": "cn-shanghai-g"
            }
        ]
    }
}
```

## Error codes

For a list of error codes, visit the [API Error Center](https://error-center.alibabacloud.com/status/product/Slb).

