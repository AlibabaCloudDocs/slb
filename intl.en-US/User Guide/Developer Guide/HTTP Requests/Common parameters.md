# Common parameters

This topic describes common parameters, including common request parameters and common response parameters. Common parameters are required by all API operations.

## Common request parameters

Common request parameters must be included in all Server Load Balancer \(SLB\) API requests.

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Format|String|No|The format in which to return the response. Valid values: JSON and XML. Default value: JSON. |
|Version|String|Yes|The version number of the API. Specify the version number in the YYYY-MM-DD format. Set the value to 2014-05-15. |
|AccessKeyId|String|Yes|The AccessKey ID provided to you by Alibaba Cloud.|
|Signature|String|Yes|The signature string of the request.|
|SignatureMethod|String|Yes|The encryption method of the signature string. Set the value to HMAC-SHA1. |
|Timestamp|String|Yes|The timestamp of the request. Specify the time in the ISO 8601 standard in the YYYY-MM-ddTHH:mm:ssZ format. The time must be in UTC. Example: 2013-01-10T12:00:00Z, which specifies 20:00:00 on January 10, 2013 \(UTC+8\). |
|SignatureVersion|String|Yes|The version of the signature encryption algorithm. Set the value to 1.0. |
|SignatureNonce|String|Yes|A unique and random number that is used to prevent replay attacks. You must use different numbers for different requests. |
|ResourceOwnerAccount|String|No|The account that owns the resource to be accessed by the API request.|

Examples

```
http://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&TimeStamp=2014-05-19T10%3A33%3A56Z
&Format=xml
&AccessKeyId=testid
&SignatureMethod=Hmac-SHA1
&SignatureNonce=NwDAxvLU6tF*****
&Version=2014-05-15
&SignatureVersion=1.0
&Signature=*Signature*
```

## Common response parameters

API responses use the HTTP response format where a 2xx status code indicates a successful call and a 4xx or 5xx status code indicates a failed call. Responses can be returned in either the JSON or XML format. You can specify the response format in the request. The default response format is JSON.

Every response returns a unique RequestID regardless of whether the call is successful.

-   XML format

    ```
    <? xml version="1.0" encoding="utf-8"? > 
        <!—Result Root Node-->
        <Interface Name+Response>
            <!—Return Request Tag-->
            <RequestId>4C467B38-3910-447D-87BC-AC049166F216</RequestId>
            <!—Return Result Data-->
        </Interface Name+Response>
    					
    ```

-   JSON format

    ```
    {
        "RequestId":"4C467B38-3910-447D-87BC-AC049166F216",
        /*Return Result Data*/
        }
    ```


