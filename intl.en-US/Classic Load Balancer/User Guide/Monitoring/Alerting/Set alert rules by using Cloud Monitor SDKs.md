# Set alert rules by using Cloud Monitor SDKs

This topic describes how to use Cloud Monitor SDKs to set alert rules for the metrics of Server Load Balancer \(SLB\).

-   SLB is the product label that has been configured in Cloud Monitor.
-   The namespace of SLB in Cloud Monitor is `acs_slb_dashboard`. For more information about how to query the namespace, see [DescribeProjectMeta](/intl.en-US/Classic Load Balancer/User Guide/Monitoring/Monitoring/View monitoring data by calling API operations.md).

The following figure shows the procedure to set alert rules by calling Cloud Monitor API operations.

![Flowchart](https://static-aliyun-doc.oss-accelerate.aliyuncs.com/assets/img/en-US/9317031161/p230746.png)

The following section describes the process:

1.  Call the DescribeMetricMetaList operation to query the descriptions of SLB time series metrics that are supported in Cloud Monitor. For more information, see [Monitoring and alerting metrics](/intl.en-US/Classic Load Balancer/User Guide/Monitoring/Monitoring and alerting metrics.md).
2.  Call the PutContact operation to create or modify an alert contact.
3.  Call the PutContactGroup operation to create or modify an alert contact group.
4.  Call the PutResourceMetricRule operation to set an alert rule for a performance metric of a resource.
5.  Call the DescribeMetricRuleList operation to query a list of alert rules.

## Python

For example, assume that a TCP listener has been configured for the lb-bp13hithhod4aoxc\*\*\*\*\* instance. The following section describes how to set rules to trigger Critical, Warn, and Info alerts when the number of unhealthy ECS instances exceeds the specified thresholds.

```
from aliyunsdkcms.request.v20190101 import DescribeMetricMetaListRequest, PutContactRequest, PutContactGroupRequest, \
    PutResourceMetricRuleRequest, DescribeMetricRuleListRequest
from aliyunsdkcore.client import AcsClient
import json, uuid

if __name__ == '__main__':
    # 1. Initialize the SDK.
    ACS_CLIENT = AcsClient(
        'LTAI4FicM86BTPDyP*****',  # your-access-key-id
        'VRj7d6LOl2ZyFyfYTWYzGk0e*****',  # your-access-key-secret
        'cn-hangzhou',  # your-region-id
    )

    # The namespace.
    namespace = "acs_slb_dashboard"

    # 2. Query the descriptions of time series metrics that are supported in Cloud Monitor.
    describeMetricMetaListRequest = DescribeMetricMetaListRequest.DescribeMetricMetaListRequest()
    # Set the namespace.
    describeMetricMetaListRequest.set_Namespace(namespace)
    # The number of records on each page. Default value: 30.
    describeMetricMetaListRequest.set_PageSize(100)
    describeMetricMetaListResponse = ACS_CLIENT.do_action_with_exception(describeMetricMetaListRequest)
    print(json.loads(describeMetricMetaListResponse))

    # 3. Create an alert contact.
    putContactRequest = PutContactRequest.PutContactRequest()
    # The name of the alert contact.
    putContactRequest.set_ContactName("doctest")
    # The description of the alert contact.
    putContactRequest.set_Describe("doctest")
    # The email address of the alert contact.
    putContactRequest.set_ChannelsMail("test@example.com")
    putContactResponse = ACS_CLIENT.do_action_with_exception(putContactRequest)
    print(json.loads(putContactResponse))

    # 4. Create an alert contact group.
    putContactGroupRequest = PutContactGroupRequest.PutContactGroupRequest()
    # The name of the alert contact group.
    putContactGroupRequest.set_ContactGroupName("the default alert contact group")
    # The description of the alert contact group.
    putContactGroupRequest.set_Describe("the default alert contact group")
    putContactGroupRequest.set_ContactNamess(["doctest"])
    putContactGroupResponse = ACS_CLIENT.do_action_with_exception(putContactGroupRequest)
    print(json.loads(putContactGroupResponse))

    # 5. Set an alert rule for a performance metric of a resource.
    putResourceMetricRuleRequest = PutResourceMetricRuleRequest.PutResourceMetricRuleRequest()
    # The ID of the alert rule.
    putResourceMetricRuleRequest.set_RuleId(uuid.uuid1())
    # The name of the alert rule.
    putResourceMetricRuleRequest.set_RuleName("alert rule for unhealthy SLB backend servers")
    # The alert contact group. Separate multiple groups with commas (,).
    putResourceMetricRuleRequest.set_ContactGroups("the default alert contact group")
    # Set the namespace of SLB to acs_slb_dashboard.
    putResourceMetricRuleRequest.set_Namespace(namespace)
    # The metric name, which is UnhealthyServerCount in this example. UnhealthyServerCount measures the number of unhealthy ECS instances.
    putResourceMetricRuleRequest.set_MetricName("UnhealthyServerCount")
    # The resources to be associated with the alert rule.
    putResourceMetricRuleRequest.set_Resources("[{'instanceId':'lb-bp13hithhod*******'}]")

    # Set Critical alerts.
    # The method that is used to collect statistics about Critical alerts. Average: average value.
    putResourceMetricRuleRequest.set_EscalationsCriticalStatistics("Average")
    # The comparison operator of the threshold for Critical alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
    putResourceMetricRuleRequest.set_EscalationsCriticalComparisonOperator("GreaterThanOrEqualToThreshold")
    # The threshold for triggering Critical alerts.
    putResourceMetricRuleRequest.set_EscalationsCriticalThreshold("2")
    # The number of times that the metric value consecutively exceeds the threshold before a Critical alert is triggered.
    putResourceMetricRuleRequest.set_EscalationsCriticalTimes(5)

    # Set Info alerts.
    # The method that is used to collect statistics about Info alerts. Average: average value.
    putResourceMetricRuleRequest.set_EscalationsInfoStatistics("Average")
    # The comparison operator of the threshold for Info alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
    putResourceMetricRuleRequest.set_EscalationsInfoComparisonOperator("GreaterThanOrEqualToThreshold")
    # The threshold for triggering Info alerts.
    putResourceMetricRuleRequest.set_EscalationsInfoThreshold("1")
    # The number of times that the metric value consecutively exceeds the threshold before an Info alert is triggered.
    putResourceMetricRuleRequest.set_EscalationsInfoTimes(5)

    # Set Warn alerts.
    # The method that is used to collect statistics about Warn alerts. Average: average value.
    putResourceMetricRuleRequest.set_EscalationsWarnStatistics("Average")
    # The comparison operator of the threshold for Warn alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
    putResourceMetricRuleRequest.set_EscalationsWarnComparisonOperator("GreaterThanOrEqualToThreshold")
    # The threshold for triggering Warn alerts.
    putResourceMetricRuleRequest.set_EscalationsWarnThreshold("1")
    # The number of times that the metric value consecutively exceeds the threshold before a Warn alert is triggered.
    putResourceMetricRuleRequest.set_EscalationsWarnTimes(5)

    putResourceMetricRuleResponse = ACS_CLIENT.do_action_with_exception(putResourceMetricRuleRequest)
    print(json.loads(putResourceMetricRuleResponse))

    # 6. Query the alert rules.
    describeMetricRuleListRequest = DescribeMetricRuleListRequest.DescribeMetricRuleListRequest()
    # Set the namespace of SLB to acs_slb_dashboard.
    describeMetricRuleListRequest.set_Namespace(namespace)
    # Set the alert metrics that you want to query.
    describeMetricRuleListRequest.set_MetricName("UnhealthyServerCount")
    describeMetricRuleListResponse = ACS_CLIENT.do_action_with_exception(describeMetricRuleListRequest)
    print(json.loads(describeMetricRuleListResponse))
            
```

## Java

For example, assume that a TCP listener has been configured for the lb-bp13hithhod4aoxc\*\*\*\*\* instance. The following section describes how to set rules to trigger Critical, Warn, and Info alerts when the number of unhealthy ECS instances exceeds the specified thresholds.

```
package com.aliyun.cms;

import com.aliyun.CommonConfig;
import com.aliyuncs.DefaultAcsClient;
import com.aliyuncs.IAcsClient;
import com.aliyuncs.cms.model.v20190101.*;
import com.aliyuncs.exceptions.ClientException;
import com.aliyuncs.profile.DefaultProfile;
import com.google.gson.Gson;

import java.util.ArrayList;
import java.util.List;
import java.util.UUID;

public class CreateMetricRuleDemo {

    public static void main(String[] args) throws ClientException {
        // 1. Initialize the SDK.
        DefaultProfile profile = DefaultProfile.getProfile(
                "cn-hangzhou", // The ID of the region.
                CommonConfig.ACCESSKEY_ID,// Your AccessKey ID.
                CommonConfig.ACCESSKEY_SECRET);// Your AccessKey secret.
        IAcsClient client = new DefaultAcsClient(profile);

        // The namespace.
        String namespace = "acs_slb_dashboard";
        Gson gson = new Gson();


        // 2. Query the descriptions of time series metrics that are supported in Cloud Monitor.
        DescribeMetricMetaListRequest describeMetricMetaListRequest = new DescribeMetricMetaListRequest();
        // Set the namespace.
        describeMetricMetaListRequest.setNamespace(namespace);
        // The number of records on each page. Default value: 30.
        describeMetricMetaListRequest.setPageSize(100);
        DescribeMetricMetaListResponse describeMetricMetaListResponse = client.getAcsResponse(describeMetricMetaListRequest);
        System.out.println(gson.toJson(describeMetricMetaListResponse));


        // 3. Create an alert contact.
        PutContactRequest putContactRequest = new PutContactRequest();
        // The name of the alert contact.
        putContactRequest.setContactName("doctest");
        // The description of the alert contact.
        putContactRequest.setDescribe("doctest");
        // The email address of the alert contact.
        putContactRequest.setChannelsMail("test@example.com");
        PutContactResponse putContactResponse = client.getAcsResponse(putContactRequest);
        System.out.println(gson.toJson(putContactResponse));


        // 4. Create an alert contact group.
        PutContactGroupRequest putContactGroupRequest = new PutContactGroupRequest();
        // The name of the alert contact group.
        putContactGroupRequest.setContactGroupName("the default alert contact group");
        // The description of the alert contact group.
        putContactGroupRequest.setDescribe("the default alert contact group");
        // The contacts in the alert contact group.
        List<String> contactNames = new ArrayList<>();
        contactNames.add("doctest");
        putContactGroupRequest.setContactNamess(contactNames);
        PutContactGroupResponse putContactGroupResponse = client.getAcsResponse(putContactGroupRequest);
        System.out.println(gson.toJson(putContactGroupResponse));


        // 5. Set an alert rule for a performance metric of a resource.
        PutResourceMetricRuleRequest putResourceMetricRuleRequest = new PutResourceMetricRuleRequest();
        // Generate a UUID that is in all lowercase letters and contains no hyphens (-) as the unique ID of the alert rule.
        String uuid = UUID.randomUUID().toString().replace("-", "").toLowerCase();
        // The ID of the alert rule.
        putResourceMetricRuleRequest.setRuleId(uuid);
        // The name of the alert rule.
        putResourceMetricRuleRequest.setRuleName("alert rule for unhealthy SLB backend servers");
        // The alert contact group. Separate multiple groups with commas (,).
        putResourceMetricRuleRequest.setContactGroups("the default alert contact group");
        // Set the namespace of SLB to acs_slb_dashboard.
        putResourceMetricRuleRequest.setNamespace(namespace);
        // The metric name, which is UnhealthyServerCount in this example. UnhealthyServerCount measures the number of unhealthy ECS instances.
        putResourceMetricRuleRequest.setMetricName("UnhealthyServerCount");
        // The resources to be associated with the alert rule.
        putResourceMetricRuleRequest.setResources("[{\"instanceId\":\"lb-bp13hithhod4aoxc*****\"}]");

        // Set Critical alerts.
        // The method used to collect statistics about Critical alerts. Average: average value.
        putResourceMetricRuleRequest.setEscalationsCriticalStatistics("Average");
        // The comparison operator of the threshold for Critical alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
        putResourceMetricRuleRequest.setEscalationsCriticalComparisonOperator("GreaterThanOrEqualToThreshold");
        // The threshold for triggering Critical alerts.
        putResourceMetricRuleRequest.setEscalationsCriticalThreshold("2");
        // The number of times that the metric value consecutively exceeds the threshold before a Critical alert is triggered.
        putResourceMetricRuleRequest.setEscalationsCriticalTimes(5);

        // Set Info alerts.
        // The method that is used to collect statistics about Info alerts. Average: average value.
        putResourceMetricRuleRequest.setEscalationsInfoStatistics("Average");
        // The comparison operator of the threshold for Info alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
        putResourceMetricRuleRequest.setEscalationsInfoComparisonOperator("GreaterThanOrEqualToThreshold");
        // The threshold for triggering Info alerts.
        putResourceMetricRuleRequest.setEscalationsInfoThreshold("1");
        // The number of times that the metric value consecutively exceeds the threshold before an Info alert is triggered.
        putResourceMetricRuleRequest.setEscalationsInfoTimes(5);

        // Set Warn alerts.
        // The method that is used to collect statistics about Warn alerts. Average: average value.
        putResourceMetricRuleRequest.setEscalationsWarnStatistics("Average");
        // The comparison operator of the threshold for Warn alerts. GreaterThanOrEqualToThreshold: greater than or equal to the threshold.
        putResourceMetricRuleRequest.setEscalationsWarnComparisonOperator("GreaterThanOrEqualToThreshold");
        // The threshold for triggering Warn alerts.
        putResourceMetricRuleRequest.setEscalationsWarnThreshold("1");
        // The number of times that the metric value consecutively exceeds the threshold before a Warn alert is triggered.
        putResourceMetricRuleRequest.setEscalationsWarnTimes(5);
        PutResourceMetricRuleResponse putResourceMetricRuleResponse = client.getAcsResponse(putResourceMetricRuleRequest);
        System.out.println(gson.toJson(putResourceMetricRuleResponse));


        // 6. Query the alert rules.
        DescribeMetricRuleListRequest describeMetricRuleListRequest = new DescribeMetricRuleListRequest();
        // Set the namespace of SLB to acs_slb_dashboard.
        describeMetricRuleListRequest.setNamespace(namespace);
        // Set the alert metrics that you want to query.
        describeMetricRuleListRequest.setMetricName("UnhealthyServerCount");
        DescribeMetricRuleListResponse describeMetricRuleListResponse = client.getAcsResponse(describeMetricRuleListRequest);
        System.out.println(gson.toJson(describeMetricRuleListResponse));
    }
}
            
```

## Responses

The following responses are returned:

```
{'TotalCount': 53, 'RequestId': '96E7FB37-8BD5-48C3-AE0C-CBC03F8B7FD7', 'Resources': {'Resource': [{'MetricName': 'ActiveConnection', 'Periods': '60,300', 'Description': 'the number of active connections on a port', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'DropConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'DropPacketRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'DropPacketTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'DropTrafficRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'DropTrafficTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'GroupTrafficRX', 'Periods': '60', 'Description': '', 'Dimensions': 'groupId', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"groupId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum,Sum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'GroupTrafficTX', 'Periods': '60', 'Description': '', 'Dimensions': 'groupId', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"groupId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum,Sum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'HeathyServerCount', 'Periods': '60,300', 'Description': 'the number of healthy ECS instances', 'Dimensions': 'userId,instanceId,port,vip', 'Labels': '[{"name":"alertUnit","value":"Count"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InactiveConnection', 'Periods': '60,300', 'Description': 'the number of inactive connections on a port', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceActiveConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceDropConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceDropPacketRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceDropPacketTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceDropTrafficRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceDropTrafficTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"bits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceInactiveConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceMaxConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceMaxConnectionUtilization', 'Periods': '60,300', 'Description': 'the maximum connection usage', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"%"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': '%', 'Statistics': 'Average,Maximum,Minimum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceNewConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceNewConnectionUtilization', 'Periods': '60,300', 'Description': 'the usage of new connections', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"%"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': '%', 'Statistics': 'Average,Maximum,Minimum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstancePacketRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstancePacketTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceQps', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceQpsUtilization', 'Periods': '60,300', 'Description': 'QPS usage', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"%"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': '%', 'Statistics': 'Average,Maximum,Minimum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceRt', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"ms"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'ms', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceStatusCode2xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceStatusCode3xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceStatusCode4xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceStatusCode5xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceStatusCodeOther', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceTrafficRX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Mbits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"unitFactor","value":"1048576"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceTrafficTX', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Mbits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"unitFactor","value":"1048576"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceUpstreamCode4xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceUpstreamCode5xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'InstanceUpstreamRt', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId', 'Labels': '[{"name":"alertUnit","value":"ms"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"instanceId"},{"name":"is_alarm","value":"true"}]', 'Unit': 'ms', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'MaxConnection', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Maximum,Minimum,Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'NewConnection', 'Periods': '60,300', 'Description': 'the number of new connections on a port', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'PacketRX', 'Periods': '60,300', 'Description': 'the number of inbound packets over a port per second', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'PacketTX', 'Periods': '60,300', 'Description': 'the number of outbound packets over a port per second', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'Qps', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'Rt', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"ms"},{"name":"alertDefault","value":"ms"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': '', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'StatusCode2xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'StatusCode3xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'StatusCode4xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'StatusCode5xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'StatusCodeOther', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/Second"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/Second', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'TrafficRXNew', 'Periods': '60,300', 'Description': 'the amount of data received over a port per second', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Mbits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"unitFactor","value":"1048576"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'TrafficTXNew', 'Periods': '60,300', 'Description': 'the amount of data sent over a port per second', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Mbits/s"},{"name":"minAlertPeriod","value":"60"},{"name":"unitFactor","value":"1048576"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'bits/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'UnhealthyServerCount', 'Periods': '60,300', 'Description': 'the current number of unhealthy ECS instances', 'Dimensions': 'userId,instanceId,port,vip', 'Labels': '[{"name":"alertUnit","value":"Count"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'UpstreamCode4xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'UpstreamCode5xx', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"Count/s"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'Count/s', 'Statistics': 'Average,Minimum,Maximum', 'Namespace': 'acs_slb_dashboard'}, {'MetricName': 'UpstreamRt', 'Periods': '60,300', 'Description': '', 'Dimensions': 'userId,instanceId,port,protocol', 'Labels': '[{"name":"alertUnit","value":"ms"},{"name":"minAlertPeriod","value":"60"},{"name":"metricCategory","value":"port"},{"name":"is_alarm","value":"true"}]', 'Unit': 'ms', 'Statistics': 'Average', 'Namespace': 'acs_slb_dashboard'}]}, 'Code': 200, 'Success': True}
{'RequestId': '653C4634-C32B-4858-B2BA-BAFC22DAF8FF', 'Code': '200', 'Success': True}
{'RequestId': '088D3BFF-DCED-4892-AE1D-468120BB6D74', 'Code': '200', 'Success': True}
{'Message': '', 'RequestId': '149A6CBC-1182-4749-8AD6-F55C563B9020', 'Code': 200, 'Success': True}
{'RequestId': '3E6ED37E-F5F3-472D-AF4D-8117329EAEC5', 'Total': 1, 'Alarms': {'Alarm': [{'GroupName': '', 'SilenceTime': 86400, 'ContactGroups': 'the default alert contact group', 'NoEffectiveInterval': '', 'MailSubject': '${serviceType}-${metricName}-${levelDescription}notification(${dimensions})', 'RuleId': 'edc0e1ae-7ef8-11ea-bf2d-54ee75d07c7c', 'SourceType': 'METRIC', 'Period': 300, 'Dimensions': '', 'EffectiveInterval': '', 'Namespace': 'acs_slb_dashboard', 'AlertState': 'OK', 'GroupId': '', 'MetricName': 'UnhealthyServerCount', 'EnableState': True, 'Escalations': {'Critical': {'ComparisonOperator': 'GreaterThanOrEqualToThreshold', 'Times': 5, 'Statistics': 'Average', 'Threshold': '2'}, 'Info': {'ComparisonOperator': 'GreaterThanOrEqualToThreshold', 'Times': 5, 'Statistics': 'Average', 'Threshold': '1'}, 'Warn': {'ComparisonOperator': 'GreaterThanOrEqualToThreshold', 'Times': 5, 'Statistics': 'Average', 'Threshold': '1'}}, 'Webhook': '', 'Resources': '[{"instanceId":"lb-bp13hithhod4aoxc*****"}]', 'RuleName': 'alert rule for unhealthy SLB backend servers'}]}, 'Code': '200', 'Success': True}
            
```

