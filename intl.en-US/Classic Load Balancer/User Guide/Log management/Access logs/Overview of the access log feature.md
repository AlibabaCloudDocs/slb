# Overview of the access log feature

This topic provides an overview of the access log feature of Server Load Balancer \(SLB\). You can analyze access logs to better understand the activities and geographical distribution of client users and troubleshoot issues.

## Overview

You can activate the access log feature of SLB to record detailed information of all requests sent to SLB instances, including the time when requests are sent, client IP addresses, latency, request URLs, and server responses. As an Internet access point, SLB distributes a large number of access requests. You can use access logs to analyze the activities and geographical distribution of client users and troubleshoot issues.

After you enable the access log feature of SLB, you can store access logs in the Logstores of Alibaba Cloud Log Service for log collection and analysis. You can disable the access log feature at any time.

No extra fee is charged for the access log feature of SLB. You only need to pay for Log Service.

**Note:**

-   The access log feature can only be applied to Layer 7 SLB. This feature is available in all regions.
-   Make sure that the HTTP header value does not contain `||`. Otherwise, the exported logs may be misplaced.

## Benefits

The access log feature of SLB has the following advantages:

-   Easy to use

    This feature reduces log processing time for developers and O&M personnel so that they can focus on business development and technical research.

-   Capable of dealing with large amounts of data

    SLB access logs contain a large amount of data that needs to be processed. Therefore, you must consider performance and cost for log processing. Log Service analyzes 100 million logs within one second. Compared with self-managed open source solutions, Log Service is faster and more cost-effective.

-   Real-time

    Scenarios such as DevOps, monitoring, and alerting require real-time log data. Traditional methods cannot meet this requirement. For example, it is time-consuming to perform ETL operations and data analytics by using tools such as Hive. A significant amount of effort is spent on data integration. The access log feature of SLB, in conjunction with the powerful big data computing capabilities of Alibaba Cloud Log Service, can analyze and process real-time logs within seconds.

-   Elastic

    You can enable or disable the access log feature for selected SLB instances. You can set the storage period to a value ranging from 1 to 365 days. The capacity of a Logstore is scalable to meet business growth needs.


