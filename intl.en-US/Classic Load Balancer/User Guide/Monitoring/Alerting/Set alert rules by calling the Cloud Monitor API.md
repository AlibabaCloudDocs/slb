# Set alert rules by calling the Cloud Monitor API

This topic describes how to call the Cloud Monitor API to set alert rules for the metrics of Server Load Balancer \(SLB\).

-   SLB is the product label that has been configured in Cloud Monitor.
-   The namespace of SLB in Cloud Monitor is `acs_slb_dashboard`. For more information about how to obtain the value, see [DescribeProjectMeta](/intl.en-US/Classic Load Balancer/User Guide/Monitoring/Monitoring/View monitoring data by calling API operations.md).

The following figure shows the process to set alert rules by calling the Cloud Monitor API.

![Flowchart](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/5627031161/p230756.png)

The following section describes the process:

1.  Call the DescribeMetricMetaList operation to query the descriptions of SLB time series metrics that are supported in Cloud Monitor. For more information, see [Monitoring and alerting metrics](/intl.en-US/Classic Load Balancer/User Guide/Monitoring/Monitoring and alerting metrics.md).
2.  Call the PutContact operation to create or modify an alert contact.
3.  Call the PutContactGroup operation to create or modify an alert contact group.
4.  Call the PutResourceMetricRule operation to set an alert rule for a performance metric of a resource.
5.  Call the DescribeMetricRuleList operation to query a list of alert rules.

For example, assume that a TCP listener has been configured for the lb-bp1rbwvouuyipbc\*\*\* instance. The following section describes how to set rules to trigger Critical, Warn, and Info alerts when the number of unhealthy ECS instances exceeds the specified thresholds.

## DescribeMetricMetaList

You can call this operation to query the descriptions of time series metrics that are supported in Cloud Monitor. For more information, see [DescribeMetricMetaList](/intl.en-US/API Reference/Monitoring data on time series metrics of cloud services/DescribeMetricMetaList.md).

1.  Set the value of the request parameter **Namespace** to `acs_slb_dashboard`, and set other parameters to default values.

    Sample requests:

    ```
    http(s)://[Endpoint]/? Action=DescribeMetricMetaList
    &Namespace=acs_slb_dashboard
    &<Common request parameters>
    ```

2.  View the time series metrics of SLB based on the returned parameters. Check whether the **Qps** parameter is returned in this example.

    Sample responses:

    ```
    {
        "TotalCount": 53, 
        "RequestId": "789846B4-56FC-4681-998C-5B7DBDFBE28F", 
        "Resources": {
            "Resource": [
                {
                    "MetricName": "ActiveConnection", 
                    "Periods": "60,300", 
                    "Description": "Number of active connections on the port", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "DropConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "DropPacketRX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "DropPacketTX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "DropTrafficRX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "DropTrafficTX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "GroupTrafficRX", 
                    "Periods": "60", 
                    "Description": "", 
                    "Dimensions": "groupId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"groupId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum,Sum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "GroupTrafficTX", 
                    "Periods": "60", 
                    "Description": "", 
                    "Dimensions": "groupId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"groupId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum,Sum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "HeathyServerCount", 
                    "Periods": "60,300", 
                    "Description": "Number of healthy ECS instances", 
                    "Dimensions": "userId,instanceId,port,vip", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InactiveConnection", 
                    "Periods": "60,300", 
                    "Description": "Number of inactive connections on the port", 
                    "Dimensions": "userId,instanceId,port,protocol", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"port\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceActiveConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceDropConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceDropPacketRX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceDropPacketTX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceDropTrafficRX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceDropTrafficTX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"bits/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "bits/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceInactiveConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceMaxConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceMaxConnectionUtilization", 
                    "Periods": "60,300", 
                    "Description": "Maximum connection usage", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"%\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "%", 
                    "Statistics": "Average,Maximum,Minimum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceNewConnection", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceNewConnectionUtilization", 
                    "Periods": "60,300", 
                    "Description": "New connection usage", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"%\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "%", 
                    "Statistics": "Average,Maximum,Minimum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstancePacketRX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstancePacketTX", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average,Minimum,Maximum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceQps", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/s\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/s", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceQpsUtilization", 
                    "Periods": "60,300", 
                    "Description":"QPS usage", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"%\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "%", 
                    "Statistics": "Average,Maximum,Minimum", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceRt", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"ms\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "ms", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceStatusCode2xx", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/Second", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceStatusCode3xx", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/Second", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceStatusCode4xx", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/Second", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }, 
                {
                    "MetricName": "InstanceStatusCode5xx", 
                    "Periods": "60,300", 
                    "Description": "", 
                    "Dimensions": "userId,instanceId", 
                    "Labels": "[{\"name\":\"alertUnit\",\"value\":\"Count/Second\"},{\"name\":\"minAlertPeriod\",\"value\":\"60\"},{\"name\":\"metricCategory\",\"value\":\"instanceId\"},{\"name\":\"is_alarm\",\"value\":\"true\"}]", 
                    "Unit": "Count/Second", 
                    "Statistics": "Average", 
                    "Namespace": "acs_slb_dashboard"
                }
            ]
        }, 
        "Code": 200, 
        "Success": true
    }
    ```


## PutContact

You can call this operation to create an alert contact. If you have already added an alert contact, you can call this operation to modify the alert contact. For more information, see [PutContact](/intl.en-US/API Reference/Alert groups/PutContact.md).

1.  In the request parameters, set the name and contact information of the alert contact.

    In this example, configure the following parameters and set other parameters to default values:

    -   **ContactName**: the name of the alert contact.
    -   **Channels.Mail**: the email address of the alert contact. After you add or modify an email address, the recipient receives an email that contains an activation link. The system adds the recipient to the list of alert contacts only after the recipient activates the email address.
    Sample requests:

    ```
    http(s)://[Endpoint]/? Action=PutContact
    &ContactName=doctest
    &Channels.Mail=test@example.com
    &<Common request parameters>
    ```

2.  Check whether the alert contact is created based on the returned parameters.

    Sample responses:

    ```
    {
        "RequestId": "50E26BC3-B211-4713-9608-EE8CE2EAB7E1", 
        "Code": "200", 
        "Success": true
    }
    ```


## PutContactGroup

You can call this operation to create an alert contact group and modify an existing alert contact group. For more information, see [PutContactGroup](/intl.en-US/API Reference/Alert groups/PutContactGroup.md).

1.  In the request parameters, set the name and description of an alert contact group, and the names of the alert contacts in the group.

    In this example, configure the following parameters and set other parameters to default values:

    -   **ContactGroupName**: the name of the alert contact group.
    -   **Describe**: the description of the alert contact group.
    -   **ContactNames**: the names of the alert contacts in the group.
    Sample requests:

    ```
    http(s)://[Endpoint]/? Action=PutContactGroup
    &ContactGroupName=doctestgroup
    &ContactNames.1=doctest
    &Describe=SLB alert contact group
    &<Common request parameters>
    ```

2.  Check whether the alert contact group is created based on the returned parameters.

    Sample responses:

    ```
    {
        "RequestId": "B8B88837-99A4-4F0D-B445-5E9C072D154D", 
        "Code": "200", 
        "Success": true
    }
    ```


## PutResourceMetricRule

You can call this operation to configure an alert rule for a performance metric of a resource. For more information, see [PutResourceMetricRule](/intl.en-US/API Reference/Alert rules for time series metrics/PutResourceMetricRule.md).

1.  In the request parameters, set the alert threshold for the number of unhealthy ECS instances.

    In this example, configure the following parameters and set other parameters to default values.

    |Parameter|Description|
    |---------|-----------|
    |**RuleId**|The ID of the alert rule.|
    |**Namespace**|The namespace of SLB. Set the value to **acs\_slb\_dashboard**.|
    |**MetricName**|The names of metrics. You can query the result according to [DescribeMetricMetaList](#section_0k8_ru8_ww7) or set the parameter according to [Monitoring and alerting metrics](/intl.en-US/Classic Load Balancer/User Guide/Monitoring/Monitoring and alerting metrics.md). In this example, the metric that indicates the number of unhealthy ECS instances is **UnhealthyServerCount**. |
    |**Resources**|The resources to be associated with the alert rules. If you want to associate SLB instances with the alert rule, specify the instances in the `[{"instanceId":"lb-bp1rbwvouu******"}]` format.|
    |**ContactGroups**|The alert contact group. Separate multiple groups with commas \(,\).|
    |**Escalations.Critical.Statistics**|The method that is used to collect statistics about Critical alerts. Valid values:     -   Average: the average value
    -   Minimum: the minimum value
    -   Maximum: the maximum value |
    |**Escalations.Critical.ComparisonOperator**|The comparison operator of the threshold for Critical alerts. Valid values:     -   GreaterThanOrEqualToThreshold: greater than or equal to the threshold
    -   GreaterThanThreshold: greater than the threshold
    -   LessThanOrEqualToThreshold: less than or equal to the threshold
    -   LessThanThreshold: less than the threshold
    -   NotEqualToThreshold: not equal to the threshold
    -   GreaterThanYesterday: greater than the metric value at the same time yesterday
    -   LessThanYesterday: less than the metric value at the same time yesterday
    -   GreaterThanLastWeek: greater than the metric value at the same time last week
    -   LessThanLastWeek: less than the metric value at the same time last week
    -   GreaterThanLastPeriod: greater than the metric value in the last monitoring cycle
    -   LessThanLastPeriod: less than the metric value in the last monitoring cycle |
    |**Escalations.Critical.Threshold**|The threshold for triggering Critical alerts.|
    |**Escalations.Critical.Times**|The number of times that the metric value consecutively exceeds the threshold before a Critical alert is triggered.|
    |**Escalations.Warn.Statistics**|The method that is used to collect statistics about Warn alerts. Valid values:     -   Average: the average value
    -   Minimum: the minimum value
    -   Maximum: the maximum value |
    |**Escalations.Warn.ComparisonOperator**|The comparison operator of the threshold for Warn alerts. Valid values:     -   GreaterThanOrEqualToThreshold: greater than or equal to the threshold
    -   GreaterThanThreshold: greater than the threshold
    -   LessThanOrEqualToThreshold: less than or equal to the threshold
    -   LessThanThreshold: less than the threshold
    -   NotEqualToThreshold: not equal to the threshold
    -   GreaterThanYesterday: greater than the metric value at the same time yesterday
    -   LessThanYesterday: less than the metric value at the same time yesterday
    -   GreaterThanLastWeek: greater than the metric value at the same time last week
    -   LessThanLastWeek: less than the metric value at the same time last week
    -   GreaterThanLastPeriod: greater than the metric value in the last monitoring cycle
    -   LessThanLastPeriod: less than the metric value in the last monitoring cycle |
    |**Escalations.Warn.Threshold**|The threshold for triggering Warn alerts.|
    |**Escalations.Warn.Times**|The number of times that the metric value consecutively exceeds the threshold before a Warn alert is triggered.|
    |**Escalations.Info.Statistics**|The method that is used to collect statistics about Info alerts. Valid values:     -   Average: the average value
    -   Minimum: the minimum value
    -   Maximum: the maximum value |
    |**Escalations.Info.ComparisonOperator**|The comparison operator of the threshold for Info alerts. Valid values:     -   GreaterThanOrEqualToThreshold: greater than or equal to the threshold
    -   GreaterThanThreshold: greater than the threshold
    -   LessThanOrEqualToThreshold: less than or equal to the threshold
    -   LessThanThreshold: less than the threshold
    -   NotEqualToThreshold: not equal to the threshold
    -   GreaterThanYesterday: greater than the metric value at the same time yesterday
    -   LessThanYesterday: less than the metric value at the same time yesterday
    -   GreaterThanLastWeek: greater than the metric value at the same time last week
    -   LessThanLastWeek: less than the metric value at the same time last week
    -   GreaterThanLastPeriod: greater than the metric value in the last monitoring cycle
    -   LessThanLastPeriod: less than the metric value in the last monitoring cycle |
    |**Escalations.Info.Threshold**|The threshold for triggering Info alerts.|
    |**Escalations.Info.Times**|The number of times that the metric value consecutively exceeds the threshold before an Info alert is triggered.|

    Sample requests:

    ```
    http(s)://[Endpoint]/? Action=PutResourceMetricRule
    &ContactGroups=doctestgroup
    &MetricName=UnhealthyServerCount
    &Namespace=acs_slb_dashboard
    &Resources=[{"instanceId":"lb-bp1rbwvouuyipbc*****}]
    &Escalations.Critical.Statistics=Minimum
    &Escalations.Critical.ComparisonOperator=GreaterThanOrEqualToThreshold
    &Escalations.Critical.Threshold=100
    &Escalations.Warn.Statistics=Average
    &Escalations.Warn.ComparisonOperator=GreaterThanOrEqualToThreshold
    &Escalations.Warn.Threshold=30
    &Escalations.Info.Statistics=Maximum
    &Escalations.Info.ComparisonOperator=30
    &Escalations.Info.Threshold=30
    &<Common request parameters>
    ```

2.  Check whether the alert rule is created based on the returned **Success** value.

    Sample responses:

    ```
    {
        "Message":"",
        "RequestId":"C65B0B84-DDE8-4DCA-8663-5836773102D4",
        "Success":true,
        "Code":"200"
    }
    ```


## DescribeMetricRuleList

You can call this operation to query a list of alert rules. For more information, see [DescribeMetricRuleList](/intl.en-US/API Reference/Alert rules for time series metrics/DescribeMetricRuleList.md).

1.  In the request parameters, specify the SLB namespace and alert metrics to query detailed information about the alert metrics.

    In this example, configure the following parameters and set other parameters to default values:

    -   **Namespace**: Set the namespace of SLB to **acs\_slb\_dashboard**.
    -   **MetricName**: Specify the alert metrics to be queried.
    Request parameters:

    ```
    http(s)://[Endpoint]/? Action=DescribeMetricRuleList
    &Namespace=acs_slb_dashboard
    &MetricName=UnhealthyServerCount
    &<Common request parameters>
    ```

2.  View the details of the alert metrics specified in this example based on the returned parameters.

    Sample responses:

    ```
    {
        "RequestId": "F249E314-1763-4662-A347-BD54C739191E", 
        "Total": 1, 
        "Alarms": {
            "Alarm": [
                {
                    "GroupName": "", 
                    "SilenceTime": 86400, 
                    "ContactGroups": "doctestgroup", 
                    "NoEffectiveInterval": "", 
                    "MailSubject": "${serviceType}-${metricName}-${levelDescription} notification (${dimensions})", 
                    "RuleId": "123", 
                    "SourceType": "METRIC", 
                    "Period": 300, 
                    "Dimensions": "", 
                    "EffectiveInterval": "", 
                    "Namespace": "acs_slb_dashboard", 
                    "AlertState": "INSUFFICIENT_DATA", 
                    "GroupId": "", 
                    "MetricName": "UnhealthyServerCount", 
                    "EnableState": true, 
                    "Escalations": {
                        "Critical": { }, 
                        "Info": {
                            "ComparisonOperator": "LessThanThreshold", 
                            "Times": 3, 
                            "Statistics": "Average", 
                            "Threshold": "3"
                        }, 
                        "Warn": {
                            "ComparisonOperator": "GreaterThanThreshold", 
                            "Times": 3, 
                            "Statistics": "Average", 
                            "Threshold": "10"
                        }
                    }, 
                    "Webhook": "", 
                    "Resources": "[{\"instanceId\":\"lb-bp1rbwvouuyipbc*****\"}]", 
                    "RuleName": "UnhealthyServerCount"
                }
            ]
        }, 
        "Code": "200", 
        "Success": true
    }
    ```


