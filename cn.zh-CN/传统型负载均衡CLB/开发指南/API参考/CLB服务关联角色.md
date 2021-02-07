# CLB服务关联角色

本文为您介绍CLB服务关联角色的应用场景以及如何删除服务关联角色。

## AliyunServiceRoleForSlbLogDelivery

|项目|说明|
|--|--|
|服务名称|logdelivery.slb.aliyuncs.com|
|角色权限策略|AliyunServiceRolePolicyForSlbLogDelivery|
|权限说明|允许阿里云负载均衡服务访问您的日志服务（SLS）和OSS服务。|
|使用场景|用户启用实例的日志投递功能，负载均衡服务会将用户日志投递到用户的SLS或者OSS服务。|
|创建时机|-   用户通过控制台开启健康检查日志、访问日志、秒级监控功能。
-   用户调用OpenAPI：SetLogsDownloadAttribute或SetAccessLogsDownloadAttribute。 |
|授权策略|```
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
|角色删除SPI|当您在该地域下没有CLB实例时，该角色可以被删除。|

## AliyunServiceRoleForSlbHealthDiagnose

|项目|说明|
|--|--|
|服务名称|healthdiagnose.slb.aliyuncs.com|
|角色权限策略|AliyunServiceRolePolicyForSlbHealthDiagnose|
|权限说明|允许阿里云负载均衡服务访问您的ECS服务。|
|使用场景|CLB健康检查诊断功能的主要原理是根据CLB监听上的健康检查配置生成诊断脚本，通过ECS云助手在您的ECS上执行脚本得到健康诊断结果，并提供异常的产生原因和常见处理方法。|
|创建时机|-   用户使用控制台的实例体检功能。
-   用户调用OpenAPI：DiagnoseHealthCheckStatus或DetectHealthCheckStatus。 |
|授权策略|```
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
|角色删除SPI|当用户在该区域下没有CLB实例时，该角色可以被删除。|

