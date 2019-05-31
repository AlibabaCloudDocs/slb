# API概览 {#doc_api_overview .concept}

负载均衡提供以下相关API接口。

## 负载均衡实例 { .section}

|API|描述|
|---|--|
| [CreateLoadBalancer](~~4182#Slb_CreateLoadBalancer~~)

 |调用CreateLoadBalancer创建负载均衡实例。|
| [DeleteLoadBalancer](~~4184#Slb_DeleteLoadBalancer~~)

 |使用DeleteLoadBalancer删除后付费的负载均衡实例。|
| [DescribeLoadBalancerAttribute](~~4188#Slb_DescribeLoadBalancerAttribute~~)

 |使用DescribeLoadBalancerAttribute查询指定负载均衡实例的详细信息。|
| [DescribeLoadBalancers](~~4187#Slb_DescribeLoadBalancers~~)

 |调用DescribeLoadBalancers查询已创建的负载均衡实例。|
| [DescribeRegions](~~4189#Slb_DescribeRegions~~)

 |使用DescribeRegions查询可用地域。|
| [DescribeZones](~~4190#Slb_DescribeZones~~)

 |使用DescribeZones查询指定地域的可用区信息。|
| [ModifyLoadBalancerInstanceSpec](~~4191#Slb_ModifyLoadBalancerInstanceSpec~~)

 |使用ModifyLoadBalancerInstanceSpec修改负载均衡的实例规格。|
| [ModifyLoadBalancerInternetSpec](~~4183#Slb_ModifyLoadBalancerInternetSpec~~)

 |使用ModifyLoadBalancerInternetSpec修改公网负载均衡实例的计费方式。|
| [ModifyLoadBalancerPayType](~~4192#Slb_ModifyLoadBalancerPayType~~)

 |使用ModifyLoadBalancerPayType将后付费实例转换为预付费实例。|
| [SetLoadBalancerName](~~4186#Slb_SetLoadBalancerName~~)

 |使用SetLoadBalancerName修改负载均衡实例的名称。|
| [SetLoadBalancerStatus](~~4185#Slb_SetLoadBalancerStatus~~)

 |使用SetLoadBalancerStatus设置负载均衡实例的状态。|

## UDP监听 { .section}

|API|描述|
|---|--|
| [CreateLoadBalancerUDPListener](~~4206#Slb_CreateLoadBalancerUDPListener~~)

 |使用CreateLoadBalancerUDPListener创建UDP监听。|
| [DescribeLoadBalancerUDPListenerAttribute](~~4220#Slb_DescribeLoadBalancerUDPListenerAttribute~~)

 |调用DescribeLoadBalancerUDPListenerAttribute查询UDP监听的配置。|
| [SetLoadBalancerUDPListenerAttribute](~~4216#Slb_SetLoadBalancerUDPListenerAttribute~~)

 |使用SetLoadBalancerUDPListenerAttribute修改UDP协议监听的配置。|

## HTTPS监听 { .section}

|API|描述|
|---|--|
| [DescribeLoadBalancerHTTPSListenerAttribute](~~4218#Slb_DescribeLoadBalancerHTTPSListenerAttribute~~)

 |使用DescribeLoadBalancerHTTPSListenerAttribute查询HTTPS监听配置。|
| [SetLoadBalancerHTTPSListenerAttribute](~~4214#Slb_SetLoadBalancerHTTPSListenerAttribute~~)

 |使用SetLoadBalancerHTTPSListenerAttribute修改HTTPS监听的配置。|
| [CreateLoadBalancerHTTPSListener](~~4204#Slb_CreateLoadBalancerHTTPSListener~~)

 |使用CreateLoadBalancerHTTPSListener创建HTTPS监听。|

## 后端服务器组 { .section}

|API|描述|
|---|--|
| [AddVServerGroupBackendServers](~~4235#Slb_AddVServerGroupBackendServers~~)

 |调用AddVServerGroupBackendServers向指定的后端服务器组中添加后端服务器。|
| [CreateVServerGroup](~~4233#Slb_CreateVServerGroup~~)

 |使用CreateVServerGroup向指定的后端服务器组中添加后端服务器。|
| [SetVServerGroupAttribute](~~4234#Slb_SetVServerGroupAttribute~~)

 |调用SetVServerGroupAttribute修改虚拟服务器组的配置。|
| [RemoveVServerGroupBackendServers](~~4236#Slb_RemoveVServerGroupBackendServers~~)

 |调用RemoveVServerGroupBackendServers从指定的后端服务器组中移除后端服务器。|
| [ModifyVServerGroupBackendServers](~~4237#Slb_ModifyVServerGroupBackendServers~~)

 |使用ModifyVServerGroupBackendServers替换服务器组中的后端服务器。|
| [DeleteVServerGroup](~~4238#Slb_DeleteVServerGroup~~)

 |调用DeleteVServerGroup删除服务器组。|
| [DescribeVServerGroups](~~4239#Slb_DescribeVServerGroups~~)

 |调用DescribeVServerGroups查询服务器组列表。|
| [DescribeVServerGroupAttribute](~~4240#Slb_DescribeVServerGroupAttribute~~)

 |使用DescribeVServerGroupAttribute查询服务器组的详细信息。|

## 监听 { .section}

|API|描述|
|---|--|
| [StartLoadBalancerListener](~~4208#Slb_StartLoadBalancerListener~~)

 |使用StartLoadBalancerListener启动监听。|
| [StopLoadBalancerListener](~~4209#Slb_StopLoadBalancerListener~~)

 |使用StopLoadBalancerListener停止监听。|
| [DeleteLoadBalancerListener](~~4207#Slb_DeleteLoadBalancerListener~~)

 |使用DeleteLoadBalancerListener删除监听。|

## 标签 { .section}

|API|描述|
|---|--|
| [AddTags](~~22728#Slb_AddTags~~)

 |使用AddTags为指定的负载均衡实例添加标签。|
| [DescribeTags](~~4257#Slb_DescribeTags~~)

 |使用DescribeTags查询标签列表。|
| [RemoveTags](~~4258#Slb_RemoveTags~~)

 |使用RemoveTags解绑指定负载均衡实例下的标签。|

## 域名扩展（Beta） { .section}

|API|描述|
|---|--|
| [CreateDomainExtension](~~15373#Slb_CreateDomainExtension~~)

 |使用CreateDomainExtension创建扩展域名。|
| [SetDomainExtensionAttribute](~~16112#Slb_SetDomainExtensionAttribute~~)

 |使用SetDomainExtensionAttribute修改扩展域名的证书。|
| [DescribeDomainExtensions](~~16113#Slb_DescribeDomainExtensions~~)

 |使用DescribeDomainExtensions查询已添加的扩展域名。|
| [DeleteDomainExtension](~~16129#Slb_DeleteDomainExtension~~)

 |使用DeleteDomainExtension删除扩展域名。|

## 主备服务器组 { .section}

|API|描述|
|---|--|
| [CreateMasterSlaveServerGroup](~~4228#Slb_CreateMasterSlaveServerGroup~~)

 |使用CreateMasterSlaveServerGroup创建主备服务器组。一组主备服务器组只能包含两个ECS实例，一个为主服务器，另一个为备服务器。|
| [DeleteMasterSlaveServerGroup](~~4229#Slb_DeleteMasterSlaveServerGroup~~)

 |使用DeleteMasterSlaveServerGroup删除指定的主备服务器组。|
| [DescribeMasterSlaveServerGroupAttribute](~~4230#Slb_DescribeMasterSlaveServerGroupAttribute~~)

 |使用DescribeMasterSlaveServerGroupAttribute查询指定主备服务器组的详细信息。|
| [DescribeMasterSlaveServerGroups](~~4231#Slb_DescribeMasterSlaveServerGroups~~)

 |使用DescribeMasterSlaveServerGroups查询主备服务器组列表。|

## 转发规则 { .section}

|API|描述|
|---|--|
| [CreateRules](~~4250#Slb_CreateRules~~)

 |调用CreateRules为指定的HTTP或HTTPS监听添加转发规则。|
| [DeleteRules](~~4251#Slb_DeleteRules~~)

 |删除转发规则。|
| [SetRule](~~4252#Slb_SetRule~~)

 |调用SetRule更改转发规则的目标虚拟服务器组。|
| [DescribeRuleAttribute](~~4253#Slb_DescribeRuleAttribute~~)

 |使用DescribeRuleAttribute查询指定转发规则的配置详情。|
| [DescribeRules](~~4254#Slb_DescribeRules~~)

 |使用DescribeRules查询指定监听已配置的转发规则。|

## 访问控制 { .section}

|API|描述|
|---|--|
| [AddAccessControlListEntry](~~4247#Slb_AddAccessControlListEntry~~)

 |使用AddAccessControlListEntry在访问控制策略组中添加IP条目。|
| [CreateAccessControlList](~~4242#Slb_CreateAccessControlList~~)

 |使用CreateAccessControlList创建访问控制策略组。|
| [DeleteAccessControlList](~~4243#Slb_DeleteAccessControlList~~)

 |使用DeleteAccessControlList删除访问控制策略组。|
| [DescribeAccessControlListAttribute](~~4245#Slb_DescribeAccessControlListAttribute~~)

 |使用DescribeAccessControlListAttribute查询访问控制策略组的配置。|
| [DescribeAccessControlLists](~~4244#Slb_DescribeAccessControlLists~~)

 |使用DescribeAccessControlLists查询已创建的访问控制策略组。|
| [RemoveAccessControlListEntry](~~4248#Slb_RemoveAccessControlListEntry~~)

 |使用RemoveAccessControlListEntry删除访问控制策略组中的IP条目。|
| [SetAccessControlListAttribute](~~4246#Slb_SetAccessControlListAttribute~~)

 |使用SetAccessControlListAttribute修改访问控制策略组的名称。|

## 访问控制（旧版） { .section}

|API|描述|
|---|--|
| [AddListenerWhiteListItem](~~21218#Slb_AddListenerWhiteListItem~~)

 |调用AddListenerWhiteListItem添加监听访问控制白名单。|
| [DescribeListenerAccessControlAttribute](~~4221#Slb_DescribeListenerAccessControlAttribute~~)

 |使用DescribeListenerAccessControlAttribute查询监听的白名单配置。|
| [SetListenerAccessControlStatus](~~4210#Slb_SetListenerAccessControlStatus~~)

 |使用SetListenerAccessControlStatus是否开启指定监听的白名单访问控制。|
| [RemoveListenerWhiteListItem](~~4212#Slb_RemoveListenerWhiteListItem~~)

 |使用RemoveListenerWhiteListItem删除监听白名单中的IP。|

## 服务器证书 { .section}

|API|描述|
|---|--|
| [UploadServerCertificate](~~4194#Slb_UploadServerCertificate~~)

 |使用UploadServerCertificate上传服务器证书。|
| [DeleteServerCertificate](~~4195#Slb_DeleteServerCertificate~~)

 |删除服务器证书。|
| [DescribeServerCertificates](~~4196#Slb_DescribeServerCertificates~~)

 |使用DescribeServerCertificates查询指定地域的服务器证书列表。|
| [SetServerCertificateName](~~4197#Slb_SetServerCertificateName~~)

 |使用SetServerCertificateName设置服务器证书名称。|
| [UploadCACertificate](~~4198#Slb_UploadCACertificate~~)

 |使用UploadCACertificate上传CA证书。|
| [DeleteCACertificate](~~4199#Slb_DeleteCACertificate~~)

 |使用DeleteCACertificate删除CA证书。|
| [DescribeCACertificates](~~4200#Slb_DescribeCACertificates~~)

 |使用DescribeCACertificates查询CA证书列表。|
| [SetCACertificateName](~~4201#Slb_SetCACertificateName~~)

 |使用SetCACertificateName设置CA证书名称。|

