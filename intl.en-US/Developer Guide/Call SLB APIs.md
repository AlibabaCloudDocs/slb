# Call SLB APIs {#concept_xvm_tff_cz .concept}

When you call Server Load Balancer \(SLB\) APIs, HTTP GET requests are sent to the API service address of SLB, and the system responds according to the parameters set in the request. Both the requests and responses are UTF-8 encoded.

## Request syntax {#section_mqj_q3f_mdb .section}

SLB APIs use RPC style. To call SLB APIs, send HTTP GET requests.

The structure of an SLB API request is as follows:

```
http://Endpoint/?Action=xx&Parameters
```

where,

-   Endpoint: The service address of SLB APIs is slb.aliyuncs.com.
-   Action: the name of the action. For example, if you need to query created SLB instances, the action is DescribeLoadBalancers.
-   Version: the version of the API. The version of SLB APIs is 2014-05-15.
-   Parameters: the request parameters. Separate multiple parameters by using ampersands \(&\).

    Request paramters include common parameters and API-specific parameters. Common parameters include API version and identity authentication information among other parameters. For more information, see [Common parameters](intl.en-US/Developer Guide/Common parameters.md).


The following is an example of calling DescribeLoadBalancers to query created SLB instances.

**Note:** The following code has been edited to ease readability.

``` {#public}
https://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&Format=xml 
&Version=2014-05-15 
&Signature=xxxx%xxxx%3D 
&SignatureMethod=HMAC-SHA1 
&SignatureNonce=15215528852396 
&SignatureVersion=1.0 
&AccessKeyId=key-test 
&TimeStamp=2012-06-01T12:00:00Z 
…
```

## RAM user authorization {#section_mlp_qmf_mdb .section}

To maintain account security, we recommend that you use the Access Keys \(AKs\) of RAM users to call APIs. Before you call APIs by using the AKs of RAM users, you need to grant permissions to the RAM users by attaching corresponding policies to them.

For more information, see [RAM authentication](intl.en-US/Developer Guide/RAM authentication.md).

## Request signature {#section_jtc_ymf_mdb .section}

Authentication is required by the SLB service for each API call, which is provided by the inclusion of signature information in the request.

For more information about the calculation of signatures, see [RPC API signature](https://www.alibabacloud.com/help/doc-detail/66384.htm).

SLB uses an AccessKeyID and AccessKeySecret pair \(that is, an AK\) and symmetric encryption to authenticate the identity of the request sender. AKs are certificates that Alibaba Cloud issues to Alibaba Cloud accounts and RAM users for authentication. It is similar to a logon password. The AccessKeyID is used to identify the visitor's identity. The AccessKeySecret is the key used to encrypt the signature string. The server uses the AccessKeySecret to decrypt the signature string. The AccessKeySecret must be kept confidential.

A request in an API call is signed in the following format:

```
https://endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

Take the API call of DescribeLoadBalancers as an example. If your AccessKeyID is `testid`, and your AccessKeySecret is `testsecret`, then, the URL in the signature is as follows:

``` {#public1}
http://slb.aliyuncs.com/?Action=DescribeLoadBalancers
&TimeStamp=2016-02-23T12:46:24Z 
&Format=XML
&AccessKeyId=testid
&SignatureMethod=HMAC-SHA1
&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
&Version=2014-05-26 
&SignatureVersion=1.0 
```

To generate the signature, follow these steps:

1.  Create the string to be signed by using the request parameter.

    ```
    GET&%2F&AccessKeyId%3Dtestid%26Action%3DDescribeRegions%26Format%3DXML%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf%26SignatureVersion%3D1.0%26TimeStamp%3D2016-02-23T12%253A46%253A24Z%26Version%3D2014-05-26
    ```

2.  Calculate the HMAC value of the string.

    Add an ampersand \(&\) after the AccessKeySecret to add the key of the HMAC value. In this example, the key is `testsecret&`.

    ```
    CT9X0VtwR86fNWSnsc6v8YGOjuE=
    ```

3.  Add the signature to the request parameter.

    ``` {#public3}
    http://slb.aliyuncs.com/?Action=DescribeLoadBalancers
    &TimeStamp=2016-02-23T12:46:24Z 
    &Format=XML 
    &AccessKeyId=testid 
    &SignatureMethod=HMAC-SHA1 
    &SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf 
    &Version=2014-05-26 
    &SignatureVersion=1.0 
    &Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D 
    ```


