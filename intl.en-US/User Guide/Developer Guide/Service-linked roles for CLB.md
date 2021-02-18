# Service-linked roles for CLB

This topic describes the scenarios of service-linked roles for CLB and how to delete service-linked roles.

## AliyunServiceRoleForSlbLogDelivery

|Item|Description|
|----|-----------|
|Service name|logdelivery.slb.aliyuncs.com|
|Role policy|AliyunServiceRolePolicyForSlbLogDelivery|
|Permission description|Allow Classic Load Balancer \(CLB\) to access your Log Service instances and Object Storage Service \(OSS\) buckets.|
|Scenario|After you enable the log delivery feature, CLB delivers logs to your Log Service instances or OSS buckets.|
|How to enable this service-linked role|-   You can enable this service-linked role by enabling one of the following features: health check logs, access logs, or fine-grained monitoring.
-   You can enable this service-linked role by calling the SetLogsDownloadAttribute or SetAccessLogsDownloadAttribute operation. |
|Action|```
{
  "Version": "1",
  "Statement": [
    {
      "Action": [
        "log:PostLogStoreLogs",
        "oss:PutObject"
      ],
      "Resource": "*",
      "Effect": "Allow"
    },
    {
      "Action": "ram:DeleteServiceLinkedRole",
      "Resource": "*",
      "Effect": "Allow",
      "Condition": {
        "StringEquals": {
          "ram:ServiceName": "logdelivery.slb.aliyuncs.com"
        }
      }
    }
  ]
}
``` |
|Role deletion from service provider interface \(SPI\)|If no CLB instance is deployed in the current region, this role can be deleted.|

## AliyunServiceRoleForSlbHealthDiagnose

|Item|Description|
|----|-----------|
|Service name|healthdiagnose.slb.aliyuncs.com|
|Role policy|AliyunServiceRolePolicyForSlbHealthDiagnose|
|Permission description|Allow CLB to access your Elastic Compute Service \(ECS\) instances.|
|Scenario|Based on the diagnostic scripts that are generated on the listeners of CLB, CLB health checks can troubleshoot the causes of exceptions and provide solutions after ECS Cloud Assistant runs the scripts and generates health diagnostic results.|
|How to enable this service-linked role|-   You can enable this service-linked role by using the instance health check feature in the console.
-   You can enable this service-linked role by calling the DiagnoseHealthCheckStatus or DetectHealthCheckStatus operation. |
|Action|```
{
  "Version": "1",
  "Statement": [
    {
      "Action": [
        "ecs:CreateCommand",
        "ecs:InvokeCommand",
        "ecs:StopInvocation",
        "ecs:DeleteCommand",
        "ecs:DescribeCloudAssistantStatus",
        "ecs:DescribeCommands",
        "ecs:DescribeInvocations",
        "ecs:DescribeInvocationResults",
        "ecs:ModifyCommand"
      ],
      "Resource": "*",
      "Effect": "Allow"
    },
    {
      "Action": "ram:DeleteServiceLinkedRole",
      "Resource": "*",
      "Effect": "Allow",
      "Condition": {
        "StringEquals": {
          "ram:ServiceName": "healthdiagnose.slb.aliyuncs.com"
        }
      }
    }
  ]
}
``` |
|Role deletion from SPI|If no CLB instance is deployed in the current region, this role can be deleted.|

