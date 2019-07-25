# Session persistence FAQ {#concept_hsj_3h5_vdb .concept}

## 1. What is session persistence? {#section_rbq_pgy_wdb .section}

Session persistence serves to forward session requests from the same client to a specified backend server for processing.

## 2. How can I enable session persistence? {#section_sbq_pgy_wdb .section}

You can choose whether to enable the session persistence function when configuring listeners. You can configure different session persistence policies for different listeners. The maximum session persistence duration is 86,400 seconds \(24 hours\).

## 3. What type of session persistence does SLB support? {#section_emc_qgy_wdb .section}

-   For Layer-4 \(TCP protocol\) services, session persistence is based on source IP addresses. The maximum duration of Layer-4 session persistence is 3,600 seconds.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4290/15382898943293_en-US.png)

-   For Layer-7 \(HTTP or HTTPS\) services, session persistence is based on cookies. The maximum duration of session persistence based on cookie inserting is 86,400 seconds \(24 hours\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4290/15382898943294_en-US.png)


## 4. What kind of cookie configurations are supported? {#section_vl2_23y_wdb .section}

HTTP/HTTPS listeners can use cookie inserting and rewriting methods to achieve session persistence.

-   Cookie inserting: When this method is used, you only need to specify the cookie timeout. For the first access by a client, SLB inserts a cookie \(inserts a SERVERID string in the HTTP/HTTPS response message\) in the response. The next request from the client will contain this cookie and SLB will forward the request to the same ECS instance.
-   Cookie rewriting: When this method is used, you can specify the cookie to be inserted in the HTTPS/HTTP response as needed. You must maintain the timeout and TTL of the cookie in the backend ECS instance. SLB rewrites the original cookie when it discovers a customized cookie. The next request from the client will contain this rewritten cookie and SLB will forward the request to the same ECS instance. For more information, see [Configure cookie in the backend server](../../../../reseller.en-US/Best Practices/Configure cookie in the backend server.md#).

## 5. Can I configure different session persistence rules for different domain names? {#section_w2n_l3y_wdb .section}

Yes.

You can configure different session persistence rules by using the cookie rewriting method.

## 6. What timeout value should I set for a cookie? { .section}

-   For cookie inserting, you can set a timeout value from 1 to 86400 seconds on the SLB console.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4290/15382898943295_en-US.png)

-   For cookie rewriting, you must maintain the timeout value on the backend ECS instance.

## 7. How to check the session persistence string? {#section_ysp_1jy_wdb .section}

You can use developer tools in the browser to view whether the response message contains the SERVERID string or a user-specified keyword, or you can run `curl www.xxx.com -c /tmp/cookie123` to save the cookie and then run `curl www.xxx.com -b /tmp/cookie123` to initiate the access.

## 8. Why the session persistence does not work sometimes? { .section}

-   Check whether the session persistence function has been enabled in the listener configuration.
-   HTTP/HTTPS listeners cannot insert session persistence cookies to the response messages containing 4xx response codes that are returned by backend servers.

    Resolution: Use TCP listeners instead. TCP listeners achieve session persistence based on the source IP address of the client. Additionally, you can configure cookies for the backend ECS instances and add cookie detection logic to guarantee that session persistence works.

-   302 redirection changes the SERVERID string.

    If a 302 redirection packet is returned by the backend servers when SLB is inserting a cookie, the SERVERID string in session persistence will be changed. Therefore, session persistence fails to work.

    Troubleshoot: Capture the request and returned response on the browser or use a tool to capture packets to check whether a 302 response message is returned. Then, compare the SERVERID strings in the packets to see if they are different.

    Resolution: Use TCP listeners instead. TCP listeners achieve session persistence based on the source IP address of the client. Additionally, you can configure cookies for the backend ECS instances and add cookie detection logic to guarantee that session persistence works.

-   Too short session persistence duration will also cause session persistence failure.

## 9. How can I use Linux curl to test the session persistence? {#section_m2j_3jy_wdb .section}

1.  Create test pages.

    Create test pages on all the backend ECS instances. The local intranet IP address is displayed, as shown in the following figure. The intranet IP address is used to verify the backend server to which client requests are distributed. Observe the consistency of this IP address to check whether session persistence works.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/4290/15382898943296_en-US.png)

2.  Perform curl test in a Linux environment.

    Assume that the IP address of an SLB instance is 1.1.1.1, and the URL of the created test page is  [http://1.1.1.1/check.jsp](http://1.1.1.1/check.jsp).

    1.  Log on to the Linux server used for test.
    2.  Run the following command to obtain the cookie.

        ```
        curl -c test.cookie http://1.1.1.1/check.jsp
        ```

        **Note:** The default session persistence method of SLB is cookie inserting, and the curl test does not save or send a cookie. Therefore you must save the cookie for test first. Otherwise, the curl test result is random. As a result, you will consider that session persistence does not work by mistake.

    3.  Run the following command to test session persistence.

        ```
        for ((a=1;a<=30;a++)); 2="" do="" curl="" -b="" 1.cookie=""
                    check.jsp="">/dev/null | grep '10.170.*';sleep 1; done`
        ```

        **Note:** a<=30 is the number of tests to do, you can change the number as needed. grep ‘10.170. \*' is the IP address to display, you can change it ccording to the intranet IP address of the backend ECS instance.

    4.  Observe the IP addresses returned in the preceding tests. If they are the intranet IP address of the same ECS instance, then session persistence works; otherwise, there is something wrong with the SLB session persistence.

