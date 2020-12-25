# Overview

This topic describes how to make API requests. This topic is intended for users who initiate HTTP or HTTPS GET requests by calling API operations based on URLs. To make a Server Load Balancer \(SLB\) API request, you must send an HTTP GET request to the SLB endpoint and add the request parameters that correspond to the API operation being called. After you call the API, the system returns a response. All requests and responses are encoded in UTF-8.

**Note:** If you are using the following tools to call the API, skip this topic:

-   [SDK](https://github.com/aliyun)
-   Alibaba Cloud[CLI](https://www.alibabacloud.com/help/zh/doc-detail/93539.html?spm=a2c5t.10695662.1996646101.searchclickresult.37665bbaBFUYgf)
-   [API Explorer](https://api.aliyun.com/)

The request URL can consist of different parameters but the request syntax is predefined. The URL contains common request parameters, the specified signature method, and operation-specific parameters. A sample request URL is provided for each API operation in the corresponding topic. To improve readability, the URL is encoded. You must encode the URL before making a request. After the request is verified based on your signature, the results are returned. Response parameters are displayed if the call succeeds, and an error message is displayed if the call fails. You can troubleshoot issues based on the common error codes and API operation-specific error codes.

**Note:** We recommend that you use the SDK to call operations and manage resources. This avoids manual authentication.

