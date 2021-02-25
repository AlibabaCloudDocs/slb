# API概览

负载均衡提供以下相关API接口。

## 负载均衡实例

|API|描述|
|---|--|
|[CreateLoadBalancer](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/CreateLoadBalancer.md)|调用CreateLoadBalancer创建负载均衡实例。|
|[ModifyLoadBalancerInternetSpec](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/ModifyLoadBalancerInternetSpec.md)|调用ModifyLoadBalancerInternetSpec修改公网负载均衡实例的计费方式。|
|[DeleteLoadBalancer](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/DeleteLoadBalancer.md)|调用DeleteLoadBalancer删除后付费的负载均衡实例。|
|[SetLoadBalancerStatus](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/SetLoadBalancerStatus.md)|调用SetLoadBalancerStatus设置负载均衡实例的状态。|
|[SetLoadBalancerName](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/SetLoadBalancerName.md)|调用SetLoadBalancerName修改负载均衡实例的名称。|
|[DescribeLoadBalancers](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/DescribeLoadBalancers.md)|调用DescribeLoadBalancers查询已创建的负载均衡实例。|
|[DescribeLoadBalancerAttribute](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/DescribeLoadBalancerAttribute.md)|调用DescribeLoadBalancerAttribute查询指定负载均衡实例的详细信息。|
|[DescribeRegions](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/DescribeRegions.md)|调用DescribeRegions查询可用地域。|
|[DescribeZones](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/DescribeZones.md)|调用DescribeZones查询指定地域的可用区信息。|
|[ModifyLoadBalancerInstanceSpec](/intl.zh-CN/CLB开发指南/API参考/负载均衡实例/ModifyLoadBalancerInstanceSpec.md)|调用ModifyLoadBalancerInstanceSpec修改负载均衡的实例规格。|

## 服务器证书

|API|描述|
|---|--|
|[UploadServerCertificate](/intl.zh-CN/CLB开发指南/API参考/服务器证书/UploadServerCertificate.md)|调用UploadServerCertificate上传服务器证书。|
|[DeleteServerCertificate](/intl.zh-CN/CLB开发指南/API参考/服务器证书/DeleteServerCertificate.md)|调用DeleteServerCertificate删除服务器证书。|
|[DescribeServerCertificates](/intl.zh-CN/CLB开发指南/API参考/服务器证书/DescribeServerCertificates.md)|调用DescribeServerCertificates查询指定地域的服务器证书列表。|
|[SetServerCertificateName](/intl.zh-CN/CLB开发指南/API参考/服务器证书/SetServerCertificateName.md)|调用SetServerCertificateName设置服务器证书名称。|
|[UploadCACertificate](/intl.zh-CN/CLB开发指南/API参考/服务器证书/UploadCACertificate.md)|调用UploadCACertificate上传CA证书。|
|[DeleteCACertificate](/intl.zh-CN/CLB开发指南/API参考/服务器证书/DeleteCACertificate.md)|调用DeleteCACertificate删除CA证书。|
|[DescribeCACertificates](/intl.zh-CN/CLB开发指南/API参考/服务器证书/DescribeCACertificates.md)|调用DescribeCACertificates查询CA证书列表。|
|[SetCACertificateName](/intl.zh-CN/CLB开发指南/API参考/服务器证书/SetCACertificateName.md)|调用SetCACertificateName设置CA证书名称。|

## 监听

|API|描述|
|---|--|
|[DeleteLoadBalancerListener](/intl.zh-CN/CLB开发指南/API参考/监听/DeleteLoadBalancerListener.md)|调用DeleteLoadBalancerListener删除监听。|
|[StartLoadBalancerListener](/intl.zh-CN/CLB开发指南/API参考/监听/StartLoadBalancerListener.md)|调用StartLoadBalancerListener启动监听。|
|[StopLoadBalancerListener](/intl.zh-CN/CLB开发指南/API参考/监听/StopLoadBalancerListener.md)|调用StopLoadBalancerListener停止监听。|

## 后端服务器

|API|描述|
|---|--|
|[AddBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器/AddBackendServers.md)|调用AddBackendServers添加后端服务器。|
|[RemoveBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器/RemoveBackendServers.md)|调用RemoveBackendServers移除后端服务器。|
|[SetBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器/SetBackendServers.md)|调用SetBackendServers设置后端服务器权重。|
|[DescribeHealthStatus](/intl.zh-CN/CLB开发指南/API参考/后端服务器/DescribeHealthStatus.md)|调用DescribeHealthStatus查询后端服务器的健康状态。|

## 主备服务器组

|API|描述|
|---|--|
|[CreateMasterSlaveServerGroup](/intl.zh-CN/CLB开发指南/API参考/主备服务器组/CreateMasterSlaveServerGroup.md)|调用CreateMasterSlaveServerGroup创建主备服务器组。一组主备服务器组只能包含两个ECS实例，一个为主服务器，另一个为备服务器。|
|[DeleteMasterSlaveServerGroup](/intl.zh-CN/CLB开发指南/API参考/主备服务器组/DeleteMasterSlaveServerGroup.md)|调用DeleteMasterSlaveServerGroup删除指定的主备服务器组。|
|[DescribeMasterSlaveServerGroupAttribute](/intl.zh-CN/CLB开发指南/API参考/主备服务器组/DescribeMasterSlaveServerGroupAttribute.md)|调用DescribeMasterSlaveServerGroupAttribute查询指定主备服务器组的详细信息。|
|[DescribeMasterSlaveServerGroups](/intl.zh-CN/CLB开发指南/API参考/主备服务器组/DescribeMasterSlaveServerGroups.md)|调用DescribeMasterSlaveServerGroups查询主备服务器组列表。|

## 后端服务器组

|API|描述|
|---|--|
|[CreateVServerGroup](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/CreateVServerGroup.md)|调用CreateVServerGroup向指定的后端服务器组中添加后端服务器。|
|[SetVServerGroupAttribute](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/SetVServerGroupAttribute.md)|调用SetVServerGroupAttribute修改虚拟服务器组的配置。|
|[AddVServerGroupBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/AddVServerGroupBackendServers.md)|调用AddVServerGroupBackendServers向指定的后端服务器组中添加后端服务器。|
|[RemoveVServerGroupBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/RemoveVServerGroupBackendServers.md)|调用RemoveVServerGroupBackendServers从指定的后端服务器组中移除后端服务器。|
|[ModifyVServerGroupBackendServers](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/ModifyVServerGroupBackendServers.md)|调用ModifyVServerGroupBackendServers替换服务器组中的后端服务器。|
|[DeleteVServerGroup](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/DeleteVServerGroup.md)|调用DeleteVServerGroup删除服务器组。|
|[DescribeVServerGroups](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/DescribeVServerGroups.md)|调用DescribeVServerGroups查询服务器组列表。|
|[DescribeVServerGroupAttribute](/intl.zh-CN/CLB开发指南/API参考/后端服务器组/DescribeVServerGroupAttribute.md)|调用DescribeVServerGroupAttribute查询服务器组的详细信息。|

## 访问控制

|API|描述|
|---|--|
|[CreateAccessControlList](/intl.zh-CN/CLB开发指南/API参考/访问控制/CreateAccessControlList.md)|调用CreateAccessControlList创建访问控制策略组。|
|[DeleteAccessControlList](/intl.zh-CN/CLB开发指南/API参考/访问控制/DeleteAccessControlList.md)|调用DeleteAccessControlList删除访问控制策略组。|
|[DescribeAccessControlLists](/intl.zh-CN/CLB开发指南/API参考/访问控制/DescribeAccessControlLists.md)|调用DescribeAccessControlLists查询已创建的访问控制策略组。|
|[DescribeAccessControlListAttribute](/intl.zh-CN/CLB开发指南/API参考/访问控制/DescribeAccessControlListAttribute.md)|调用DescribeAccessControlListAttribute查询访问控制策略组的配置。|
|[SetAccessControlListAttribute](/intl.zh-CN/CLB开发指南/API参考/访问控制/SetAccessControlListAttribute.md)|调用SetAccessControlListAttribute修改访问控制策略组的名称。|
|[AddAccessControlListEntry](/intl.zh-CN/CLB开发指南/API参考/访问控制/AddAccessControlListEntry.md)|调用AddAccessControlListEntry在访问控制策略组中添加IP条目。|
|[RemoveAccessControlListEntry](/intl.zh-CN/CLB开发指南/API参考/访问控制/RemoveAccessControlListEntry.md)|调用RemoveAccessControlListEntry删除访问控制策略组中的IP条目。|

## 转发规则

|API|描述|
|---|--|
|[CreateRules](/intl.zh-CN/CLB开发指南/API参考/转发规则/CreateRules.md)|调用CreateRules为指定的HTTP或HTTPS监听添加转发规则。|
|[DeleteRules](/intl.zh-CN/CLB开发指南/API参考/转发规则/DeleteRules.md)|调用DeleteRules删除转发规则。|
|[SetRule](/intl.zh-CN/CLB开发指南/API参考/转发规则/SetRule.md)|调用SetRule更改转发规则的目标虚拟服务器组。|
|[DescribeRuleAttribute](/intl.zh-CN/CLB开发指南/API参考/转发规则/DescribeRuleAttribute.md)|调用DescribeRuleAttribute查询指定转发规则的配置详情。|
|[DescribeRules](/intl.zh-CN/CLB开发指南/API参考/转发规则/DescribeRules.md)|调用DescribeRules查询指定监听已配置的转发规则。|

## 标签

|API|描述|
|---|--|
|[TagResources](/intl.zh-CN/CLB开发指南/API参考/标签/TagResources.md)|调用TagResources为指定的资源列表统一创建并绑定标签。|
|[UntagResources](/intl.zh-CN/CLB开发指南/API参考/标签/UntagResources.md)|调用UntagResources为指定的资源列表统一解绑标签。|
|[ListTagResources](/intl.zh-CN/CLB开发指南/API参考/标签/ListTagResources.md)|调用ListTagResources查询实例已经绑定的标签列表。|

## TCP监听

|API|描述|
|---|--|
|[CreateLoadBalancerTCPListener](/intl.zh-CN/CLB开发指南/API参考/TCP监听/CreateLoadBalancerTCPListener.md)|调用CreateLoadBalancerTCPListener创建TCP监听。|
|[SetLoadBalancerTCPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/TCP监听/SetLoadBalancerTCPListenerAttribute.md)|调用SetLoadBalancerTCPListenerAttribute修改TCP监听的配置。|
|[DescribeLoadBalancerTCPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/TCP监听/DescribeLoadBalancerTCPListenerAttribute.md)|调用DescribeLoadBalancerTCPListenerAttribute查询TCP监听配置。|

## HTTP监听

|API|描述|
|---|--|
|[CreateLoadBalancerHTTPListener](/intl.zh-CN/CLB开发指南/API参考/HTTP监听/CreateLoadBalancerHTTPListener.md)|调用CreateLoadBalancerHTTPListener创建HTTP监听。|
|[SetLoadBalancerHTTPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/HTTP监听/SetLoadBalancerHTTPListenerAttribute.md)|调用SetLoadBalancerHTTPListenerAttribute修改HTTP监听的配置。|
|[DescribeLoadBalancerHTTPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/HTTP监听/DescribeLoadBalancerHTTPListenerAttribute.md)|调用DescribeLoadBalancerHTTPListenerAttribute查询HTTP监听配置。|

## HTTPS监听

|API|描述|
|---|--|
|[CreateLoadBalancerHTTPSListener](/intl.zh-CN/CLB开发指南/API参考/HTTPS监听/CreateLoadBalancerHTTPSListener.md)|调用CreateLoadBalancerHTTPSListener创建HTTPS监听。|
|[SetLoadBalancerHTTPSListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/HTTPS监听/SetLoadBalancerHTTPSListenerAttribute.md)|调用SetLoadBalancerHTTPSListenerAttribute修改HTTPS监听的配置。|
|[DescribeLoadBalancerHTTPSListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/HTTPS监听/DescribeLoadBalancerHTTPSListenerAttribute.md)|调用DescribeLoadBalancerHTTPSListenerAttribute查询HTTPS监听配置。|

## UDP监听

|API|描述|
|---|--|
|[CreateLoadBalancerUDPListener](/intl.zh-CN/CLB开发指南/API参考/UDP监听/CreateLoadBalancerUDPListener.md)|调用CreateLoadBalancerUDPListener创建UDP监听。|
|[SetLoadBalancerUDPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/UDP监听/SetLoadBalancerUDPListenerAttribute.md)|调用SetLoadBalancerUDPListenerAttribute修改UDP协议监听的配置。|
|[DescribeLoadBalancerUDPListenerAttribute](/intl.zh-CN/CLB开发指南/API参考/UDP监听/DescribeLoadBalancerUDPListenerAttribute.md)|调用DescribeLoadBalancerUDPListenerAttribute查询UDP监听的配置。|

## 访问控制（旧版）

|API|描述|
|---|--|
|[SetListenerAccessControlStatus](/intl.zh-CN/CLB开发指南/API参考/访问控制（旧版）/SetListenerAccessControlStatus.md)|调用SetListenerAccessControlStatus是否开启指定监听的白名单访问控制。|
|[RemoveListenerWhiteListItem](/intl.zh-CN/CLB开发指南/API参考/访问控制（旧版）/RemoveListenerWhiteListItem.md)|调用RemoveListenerWhiteListItem删除监听白名单中的IP。|
|[DescribeListenerAccessControlAttribute](/intl.zh-CN/CLB开发指南/API参考/访问控制（旧版）/DescribeListenerAccessControlAttribute.md)|调用DescribeListenerAccessControlAttribute查询监听的白名单配置。|
|[AddListenerWhiteListItem](/intl.zh-CN/CLB开发指南/API参考/访问控制（旧版）/AddListenerWhiteListItem.md)|调用AddListenerWhiteListItem添加监听访问控制白名单。|

## 域名扩展（Beta）

|API|描述|
|---|--|
|[CreateDomainExtension](/intl.zh-CN/CLB开发指南/API参考/域名扩展（Beta）/CreateDomainExtension.md)|调用CreateDomainExtension创建扩展域名。|
|[SetDomainExtensionAttribute](/intl.zh-CN/CLB开发指南/API参考/域名扩展（Beta）/SetDomainExtensionAttribute.md)|调用SetDomainExtensionAttribute修改扩展域名的证书。|
|[DescribeDomainExtensions](/intl.zh-CN/CLB开发指南/API参考/域名扩展（Beta）/DescribeDomainExtensions.md)|调用DescribeDomainExtensions查询已添加的扩展域名。|
|[DeleteDomainExtension](/intl.zh-CN/CLB开发指南/API参考/域名扩展（Beta）/DeleteDomainExtension.md)|调用DeleteDomainExtension删除扩展域名。|

## 查询资源

|API|描述|
|---|--|
|[DescribeAvailableResource](/intl.zh-CN/CLB开发指南/API参考/查询资源/DescribeAvailableResource.md)|调用DescribeAvailableResource查询某个Region的可用区支持的资源售卖情况。|

