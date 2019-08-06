# DescribeAccessControlListAttribute {#doc_api_Slb_DescribeAccessControlListAttribute .reference}

Queries the settings of an access control list.

## Debug {#apiExplorer .section}

Use [OpenAPI Explorer](https://api.aliyun.com/#product=Slb&api=DescribeAccessControlListAttribute) to perform debug operations and generate SDK code examples.

## Request parameters {#parameters .section}

|Parameter|Type|Required?|Example value|Description|
|---------|----|---------|-------------|-----------|
|Action|String|Yes|DescribeAccessControlListAttribute| The name of this action. Value: **DescribeAccessControlListAttribute**

 |
|AclId|String|Yes|acl-bp1l0kk4gxce43kzet04s| The ID of the access control list to be queried.

 |
|RegionId|String|Yes|cn-hangzhou| The ID of the region to which the access control list belongs.

 To query the region ID, call [DescribeRegions](~~27584~~).

 |
|AclEntryComment|String|No|test| Optional. A note to an IP entry in the access control list.

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example value|Description|
|---------|----|-------------|-----------|
|AclEntrys| | | A list of IP entries in the access control list.

 |
|└AclEntryComment|String|IP entry| A note to the IP entry in the access control list.

 |
|└AclEntryIP|String|192.168.0.1| An IP entry in the access control list.

 |
|AclId|String|acl-bp1l0kk4gxce43kzet04s| The ID of the queried access control list.

 |
|AclName|String|doctest| The name of the queried access control list.

 |
|AddressIPVersion|String|ipv4| The IP address type of the associated SLB instance.

 |
|RelatedListeners| | | A list of listeners that are associated with the access control list.

 |
|└AclType|String|white| The access control type:

 -   **black**: Indicates a blacklist.
-   **white**: Indicates a whitelist.

 |
|└ListenerPort|Integer|443| The frontend port of the listener that is associated with the access control list.

 |
|└LoadBalancerId|String|lb-bp13jaf5qli5xmgl1miup| The ID of the SLB instance.

 |
|└Protocol|String|https| The protocol type of the listener that is associated with the access control list.

 |
|RequestId|String|C9906A1D-86F7-4C9C-A369-54DA42EF206A| The ID of the request.

 |
|ResourceGroupId|String|rg-\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*\*| The ID of the enterprise resource group.

 |

## Examples {#demo .section}

Request example

``` {#request_demo}

/? Action=DescribeAccessControlListAttribute
&AclId=acl-bp1l0kk4gxce43kzet04s
&RegionId=cn-hangzhou
&<CommonParameters>

```

Response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeAccessControlListAttributeResponse>
  <AclId>acl-bp1l0kk4gxce43kzet04s</AclId>
  <RelatedListeners>
    <RelatedListener>
      <AclType>white</AclType>
      <LoadBalancerId>lb-bp13jaf5qli5xmgl1miup</LoadBalancerId>
      <Protocol>https</Protocol>
      <ListenerPort>443</ListenerPort>
    </RelatedListener>
  </RelatedListeners>
  <AclName>doctest</AclName>
  <RequestId>C9906A1D-86F7-4C9C-A369-54DA42EF206A</RequestId>
  <AddressIPVersion>ipv4</AddressIPVersion>
</DescribeAccessControlListAttributeResponse>

```

`JSON` format

``` {#json_return_success_demo}
{
	"AclId":"acl-bp1l0kk4gxce43kzet04s",
	"RequestId":"C9906A1D-86F7-4C9C-A369-54DA42EF206A",
	"AclName":"doctest",
	"RelatedListeners":{
		"RelatedListener":[
			{
				"AclType":"white",
				"LoadBalancerId":"lb-bp13jaf5qli5xmgl1miup",
				"Protocol":"https",
				"ListenerPort":443
			}
		]
	},
	"AddressIPVersion":"ipv4"
}
```

## Error codes {#section_597_ds5_yje .section}

[See common error codes.](https://error-center.alibabacloud.com/status/product/Slb)

