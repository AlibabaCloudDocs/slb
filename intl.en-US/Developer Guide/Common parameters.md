# Common parameters {#concept_nx2_pgf_cz .concept}

## Common request parameters {#section_zm5_rgf_cz .section}

Common request parameters are request parameters used by each API.

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Format|String|No|The format of the response. Valid value:JSON \(default\) | XML

|
|Version|String|Yes|The version of the API in the format of YYYY-MM-DD. Valid value:2014-05-15

|
|AccessKeyId|String|Yes|The AccessKey ID of the user who calls the API.|
|Signature|String|Yes|The request signature.|
|SignatureMethod|String|Yes|The algorithm used to create the request signature. Valid value:HMAC-SHA1

|
|Timestamp|String|Yes|The time at which the request was signed in the format of YYYY-MM-DDThh:mm:ssZ.For example, 2013-01-10T12:00: 00Z.

|
|SignatureVersion|String|Yes|The signature version to use. Valid value:1.0

|
|SignatureNonce|String|Yes|A random number for the signature to prevent from network attacks.Different random numbers must be used for different requests.

|
|ResourceOwnerAccount|String|No|The account owner of the resource that this request calls.|

**Example**

``` {#public}
http://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&TimeStamp=2014-05-19T10%3A33%3A56Z
&Format=xml
&AccessKeyId=testid
&Action=DescribeLoadBalancerAttribute
&SignatureMethod=Hmac-SHA1
&LoadBalancerId=*loadBalancerID*
&SignatureNonce=NwDAxvLU6tFE0DVb
&Version=2014-05-15
&SignatureVersion=1.0
&Signature=*Signature*
```

## Common response parameters {#section_rjn_1hf_cz .section}

The API response uses unified format. Returning 2XX HTTP status code indicates a successful call; returning 4xx or 5xx HTTP status code indicates a failed call. When a call succeeds, the formats of the returned data include XML and JSON. You can specify the format of the returned data when sending the request. The default format is JSON.

A RequestId is returned no matter the request is successful or not.

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? > 
        <!—The root node of the result-->
        <Action+Response>
            <!—The returned request tag-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!—The returned result-->
        </Interface name+response>
    
    ```

-   JSON format

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*The returned result*/
        }
    ```


