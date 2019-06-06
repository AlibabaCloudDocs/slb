# API概览 {#doc_17814 .concept}

负载均衡提供以下相关API接口。

## 负载均衡实例 {#section_hvb_us8_v5i .section}

|API|描述|
|---|--|
|[CreateLoadBalancer](~~27577~~)|调用CreateLoadBalancer创建负载均衡实例。|
|[ModifyLoadBalancerInternetSpec](~~27578~~)|使用ModifyLoadBalancerInternetSpec修改公网负载均衡实例的计费方式。|
|[DeleteLoadBalancer](~~27579~~)|使用DeleteLoadBalancer删除后付费的负载均衡实例。|
|[SetLoadBalancerStatus](~~27580~~)|使用SetLoadBalancerStatus设置负载均衡实例的状态。|
|[SetLoadBalancerName](~~27581~~)|使用SetLoadBalancerName修改负载均衡实例的名称。|
|[DescribeLoadBalancers](~~27582~~)|调用DescribeLoadBalancers查询已创建的负载均衡实例。|
|[DescribeLoadBalancerAttribute](~~27583~~)|使用DescribeLoadBalancerAttribute查询指定负载均衡实例的详细信息。|
|[DescribeRegions](~~27584~~)|使用DescribeRegions查询可用地域。|
|[DescribeZones](~~27585~~)|使用DescribeZones查询指定地域的可用区信息。|
|[ModifyLoadBalancerInstanceSpec](~~53360~~)|使用ModifyLoadBalancerInstanceSpec修改负载均衡的实例规格。|
|[ModifyLoadBalancerPayType](~~59589~~)|使用ModifyLoadBalancerPayType将后付费实例转换为预付费实例。|

## UDP监听 {#section_yn7_ren_wu1 .section}

|API|描述|
|---|--|
|[CreateLoadBalancerUDPListener](~~27595~~)|使用CreateLoadBalancerUDPListener创建UDP监听。|
|[SetLoadBalancerUDPListenerAttribute](~~27605~~)|使用SetLoadBalancerUDPListenerAttribute修改UDP协议监听的配置。|
|[DescribeLoadBalancerUDPListenerAttribute](~~27609~~)|调用DescribeLoadBalancerUDPListenerAttribute查询UDP监听的配置。|

## TCP监听 {#section_lx9_zqg_p00 .section}

|API|描述|
|---|--|
|[CreateLoadBalancerTCPListener](~~27594~~)|调用CreateLoadBalancerTCPListener创建TCP监听。|
|[SetLoadBalancerTCPListenerAttribute](~~27604~~)|调用SetLoadBalancerTCPListenerAttribute修改TCP监听的配置。|
|[DescribeLoadBalancerTCPListenerAttribute](~~27608~~)|使用DescribeLoadBalancerTCPListenerAttribute查询TCP监听配置。|

## HTTP监听 {#section_fzq_y2i_4ow .section}

|API|描述|
|---|--|
|[SetLoadBalancerHTTPListenerAttribute](~~27602~~)|使用SetLoadBalancerHTTPListenerAttribute修改HTTP监听的配置。|
|[CreateLoadBalancerHTTPListener](~~27592~~)|使用CreateLoadBalancerHTTPListener创建HTTP监听。|
|[DescribeLoadBalancerHTTPListenerAttribute](~~27606~~)|使用DescribeLoadBalancerHTTPListenerAttribute查询HTTP监听配置。|

## HTTPS监听 {#section_v6z_5cc_id6 .section}

|API|描述|
|---|--|
|[SetLoadBalancerHTTPSListenerAttribute](~~27603~~)|使用SetLoadBalancerHTTPSListenerAttribute修改HTTPS监听的配置|
|[DescribeLoadBalancerHTTPSListenerAttribute](~~27607~~)|使用DescribeLoadBalancerHTTPSListenerAttribute查询HTTPS监听配置。|
|[CreateLoadBalancerHTTPSListener](~~27593~~)|使用CreateLoadBalancerHTTPSListener创建HTTPS监听。|

## 监听 {#section_knb_owq_vdf .section}

|API|描述|
|---|--|
|[StartLoadBalancerListener](~~27597~~)|使用StartLoadBalancerListener启动监听。|
|[StopLoadBalancerListener](~~27598~~)|使用StopLoadBalancerListener停止监听。|
|[DeleteLoadBalancerListener](~~27596~~)|使用DeleteLoadBalancerListener删除监听。|

## 后端服务器 {#section_y9q_bdh_chw .section}

|API|描述|
|---|--|
|[SetBackendServers](~~27634~~)|使用SetBackendServers设置后端服务器权重。|
|[AddBackendServers](~~27632~~)|调用AddBackendServers添加后端服务器。|
|[RemoveBackendServers](~~27633~~)|使用RemoveBackendServers移除后端服务器。|
|[DescribeHealthStatus](~~27635~~)|使用DescribeHealthStatus查询后端服务器的健康状态。|

## 后端服务器组 {#section_r1g_fq9_xlq .section}

|API|描述|
|---|--|
|[DescribeVServerGroupAttribute](~~35224~~)|使用DescribeVServerGroupAttribute查询服务器组的详细信息。|
|[CreateVServerGroup](~~35215~~)|使用CreateVServerGroup向指定的后端服务器组中添加后端服务器。|
|[AddVServerGroupBackendServers](~~35218~~)|调用AddVServerGroupBackendServers向指定的后端服务器组中添加后端服务器。|
|[SetVServerGroupAttribute](~~35217~~)|调用SetVServerGroupAttribute修改虚拟服务器组的配置。|
|[RemoveVServerGroupBackendServers](~~35219~~)|调用RemoveVServerGroupBackendServers从指定的后端服务器组中移除后端服务器。|
|[ModifyVServerGroupBackendServers](~~35220~~)|使用ModifyVServerGroupBackendServers替换服务器组中的后端服务器。|
|[DeleteVServerGroup](~~35221~~)|调用DeleteVServerGroup删除服务器组。|
|[DescribeVServerGroups](~~35222~~)|调用DescribeVServerGroups查询服务器组列表。|

## 主备服务器组 {#section_xuq_dcf_xzq .section}

|API|描述|
|---|--|
|[CreateMasterSlaveServerGroup](~~50506~~)|使用CreateMasterSlaveServerGroup创建主备服务器组。一组主备服务器组只能包含两个ECS实例，一个为主服务器，另一个为备服务器。|
|[DeleteMasterSlaveServerGroup](~~50507~~)|使用DeleteMasterSlaveServerGroup删除指定的主备服务器组。|
|[DescribeMasterSlaveServerGroupAttribute](~~50509~~)|使用DescribeMasterSlaveServerGroupAttribute查询指定主备服务器组的详细信息。|
|[DescribeMasterSlaveServerGroups](~~50508~~)|使用DescribeMasterSlaveServerGroups查询主备服务器组列表。|

## 服务器证书 {#section_rey_idv_5xt .section}

|API|描述|
|---|--|
|[UploadServerCertificate](~~34181~~)|使用UploadServerCertificate上传服务器证书。|
|[DeleteServerCertificate](~~34182~~)|删除服务器证书。|
|[DescribeServerCertificates](~~34183~~)|使用DescribeServerCertificates查询指定地域的服务器证书列表。|
|[SetServerCertificateName](~~34184~~)|使用SetServerCertificateName设置服务器证书名称。|
|[UploadCACertificate](~~34935~~)|使用UploadCACertificate上传CA证书。|
|[DeleteCACertificate](~~34937~~)|使用DeleteCACertificate删除CA证书。|
|[DescribeCACertificates](~~34938~~)|使用DescribeCACertificates查询CA证书列表。|
|[SetCACertificateName](~~34936~~)|使用SetCACertificateName设置CA证书名称。|

## 域名扩展（Beta） {#section_vwc_5kj_msl .section}

|API|描述|
|---|--|
|[CreateDomainExtension](~~85912~~)|使用CreateDomainExtension创建扩展域名。|
|[SetDomainExtensionAttribute](~~85913~~)|使用SetDomainExtensionAttribute修改扩展域名的证书。|
|[DescribeDomainExtensions](~~85914~~)|使用DescribeDomainExtensions查询已添加的扩展域名。|
|[DeleteDomainExtension](~~85915~~)|使用DeleteDomainExtension删除扩展域名。|

## 查询资源 {#section_tqw_5pu_twe .section}

|API|描述|
|---|--|
|[DescribeAvailableResource](~~117645~~)|调用DescribeAvailableResource查询某个地域的可用区支持的资源售卖情况。|

## 标签 {#section_evr_hg5_198 .section}

|API|描述|
|---|--|
|[RemoveTags](~~42872~~)|使用RemoveTags解绑指定负载均衡实例下的标签。|
|[AddTags](~~42871~~)|使用AddTags为指定的负载均衡实例添加标签。|
|[DescribeTags](~~42873~~)|调用DescribeTags查询标签列表。|

## 转发规则 {#section_dn2_b25_a4t .section}

|API|描述|
|---|--|
|[CreateRules](~~35226~~)|调用CreateRules为指定的HTTP或HTTPS监听添加转发规则。|
|[DeleteRules](~~35227~~)|删除转发规则。|
|[SetRule](~~35228~~)|调用SetRule更改转发规则的目标虚拟服务器组。|
|[DescribeRuleAttribute](~~35229~~)|使用DescribeRuleAttribute查询指定转发规则的配置详情。|
|[DescribeRules](~~35230~~)|使用DescribeRules查询指定监听已配置的转发规则。|

## 访问控制 {#section_hdk_23f_yjc .section}

|API|描述|
|---|--|
|[CreateAccessControlList](~~70015~~)|调用CreateAccessControlList创建访问控制策略组。|
|[DeleteAccessControlList](~~70056~~)|使用DeleteAccessControlList删除访问控制策略组。|
|[DescribeAccessControlLists](~~70052~~)|使用DescribeAccessControlLists查询已创建的访问控制策略组。|
|[DescribeAccessControlListAttribute](~~70051~~)|使用DescribeAccessControlListAttribute查询访问控制策略组的配置。|
|[SetAccessControlListAttribute](~~70022~~)|使用SetAccessControlListAttribute修改访问控制策略组的名称。|
|[AddAccessControlListEntry](~~70023~~)|使用AddAccessControlListEntry在访问控制策略组中添加IP条目。|
|[RemoveAccessControlListEntry](~~70055~~)|使用RemoveAccessControlListEntry删除访问控制策略组中的IP条目。|

## 访问控制（旧版） {#section_l4a_u7n_s8s .section}

|API|描述|
|---|--|
|[RemoveListenerWhiteListItem](~~27601~~)|使用RemoveListenerWhiteListItem删除监听白名单中的IP。|
|[AddListenerWhiteListItem](~~27600~~)|调用AddListenerWhiteListItem添加监听访问控制白名单。|
|[DescribeListenerAccessControlAttribute](~~27610~~)|使用DescribeListenerAccessControlAttribute查询监听的白名单配置。|
|[SetListenerAccessControlStatus](~~27599~~)|使用SetListenerAccessControlStatus是否开启指定监听的白名单访问控制。|

