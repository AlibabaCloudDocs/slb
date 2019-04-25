# Call SLB APIs {#concept_xvm_tff_cz .concept}

Calling an SLB API is to send an HTTP GET request to the endpoint of SLB API. You must add required parameters in the request. After the API is called, a response is sent back. The request and response results are encoded using the UTF-8 character set.

## Request structure {#section_mqj_q3f_mdb .section}

SLB APIs belong to the RPC type. You can call SLB APIs by sending HTTP GET requests.

The request structure is as follows:

```
http://Endpoint/?Action=xx&Parameters
```

Where:

-   Endpoint: The endpoint of SLB APIs is slb.aliyuncs.com.
-   Action: The action to perform. For example, call the DescribeLoadBalancers API to query created SLB instances.
-   Version: The version of the API to call. The SLB API version is 2014-05-15.
-   Parameters: Request parameters. Use “&” to separate multiple parameters.

    Request parameters consist of common parameters and API specific parameters. Common parameters include API version, credentials, and so on. For more information, see [Common parameters](reseller.en-US/Developer Guide/Common parameters.md).


The following is an example using the DescribeLoadBalancers API to query the created SLB instances:

**Note:** To make it easy to read, the API request is displayed in the following format:

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

## API authorization {#section_mlp_qmf_mdb .section}

For the security of your account, we recommend that you use a RAM user to call APIs. Before using a RAM user to call an API, you must grant the RAM user the corresponding permission to call the API by creating an authorization policy and attaching the policy to the RAM user.

For more information, see [RAM authentication](reseller.en-US/Developer Guide/RAM authentication.md).

## API signature {#section_jtc_ymf_mdb .section}

To ensure the security of your API, you must sign the API request. Alibaba Cloud uses the signature in the request to verify the identity of the person who calls the API.

For more information, see [RPC API signature](https://www.alibabacloud.com/help/doc-detail/66384.htm).

SLB uses AccessKey ID and AccessKey Secret for symmetrical encryption to verify the identity of the requester. AccessKey is an identity credential issued to Alibaba Cloud accounts and the RAM users \(similar to the logon password\). The AccessKey ID is used to verify the identity of the user, and the AccessKey Secret is used to encrypt the signature string and is also the key used by the server to verify the signature string. The AccessKey Secret must be kept strictly confidential.

Add the signature to the API request in the following format:

```
https://endpoint/?SignatureVersion=1.0&SignatureMethod=HMAC-SHA1&Signature=CT9X0VtwR86fNWSnsc6v8YGOjuE%3D&SignatureNonce=3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf
```

Take the DescribeLoadBalancers API as an example. If the AccessKey ID is `testid`, the AccessKey Secret is `testsecret`, the original request URL is as follows:

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

Follow these steps to calculate the signature:

1.  Use the request parameters to create a canonicalized query string to sign.

    ```
    GET&%2F&AccessKeyId%3Dtestid%26Action%3DDescribeRegions%26Format%3DXML%26SignatureMethod%3DHMAC-SHA1%26SignatureNonce%3D3ee8c1b8-83d3-44af-a94f-4e0ad82fd6cf%26SignatureVersion%3D1.0%26TimeStamp%3D2016-02-23T12%253A46%253A24Z%26Version%3D2014-05-26
    ```

2.  Calculate the HMAC value of the string to sign.

    Append an ampersand \(“&”\) to the AccessKey Secret and use the new string as the key to calculate the HMAC value. In this example, the key is `testsecret&`.

    ```
    CT9X0VtwR86fNWSnsc6v8YGOjuE=
    ```

3.  Add the signature to the request parameters:

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


