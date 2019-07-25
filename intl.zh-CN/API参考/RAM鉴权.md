# RAM鉴权 {#concept_slb_rjf_cz .concept}

在使用RAM账号调用SLB API前，需要主账号通过创建授权策略对RAM账号进行授权。在授权策略中，使用资源描述符（Alibaba Cloud Resource Name, ARN）指定授权资源。

## 可授权的负载均衡资源类型 {#section_vj2_fyf_cz .section}

在进行RAM子账号授权时，SLB资源的描述方式如下：

|资源类型|授权策略中的资源描述方法|
|----|------------|
|LoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:$regionid:$accountid:loadbalancer/\*|
|acs:slb:\*:$accountid:loadbalancer/\*|
|acs:slb:\*:\*:loadbalancer/\*|
|Certificate|acs:slb:$regionid:$accountid:certificate/$servercertificateId|
|acs:slb:$regionid:$accountid:certificate/\*|
|ACL|acs:slb:$regionid:$accountid:acl/\*|
|acs:slb:$regionid:$accountid:acl/$aclid|

其中`$regionid/accoutid/servercertificateId` 为具体的资源ID，`*`代表对应的所有资源。

## 可授权的SLB接口 {#section_ytz_qyf_cz .section}

下表列举了SLB中可授权的API及其描述方式：

|API|资源描述|
|---|----|
|CreateLoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/\*|
|ModifyLoadBalancerInternetSpec|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DeleteLoadBalancer|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerStatus|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerName|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancers|acs:slb:$regionid:$accountid:loadbalancer/\*|
|DescribeLoadBalancerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeRegions|acs:slb:\*:$accountid:\*|
|UploadServerCertificate|acs:slb:%s:%s:certificate/\*|
|DeleteServerCertificate|acs:slb:%s:%s:certificate/%|
|DescribeServerCertificate|acs:slb:%s:%s:certificate/%|
|SetServerCertificateName|acs:slb:%s:%s:certificate/%|
|DescribeServerCertificates|acs:slb:%s:%s:certificate/\*|
|CreateLoadBalancerHTTPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateLoadBalancerHTTPSListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:%s:%s:certificate/%|
|CreateLoadBalancerTCPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateLoadBalancerUDPListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DeleteLoadBalancerListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|StartLoadBalancerListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|StopLoadBalancerListener|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerHTTPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerHTTPSListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:slb:%s:%s:certificate/%|
|SetLoadBalancerTCPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|SetLoadBalancerUDPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerHTTPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerHTTPSListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerTCPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeLoadBalancerUDPListenerAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|AddBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|RemoveBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|SetBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|DescribeHealthStatus|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|CreateVServerGroup|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|SetVServerGroupAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DeleteVServerGroup|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeVServerGroups|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|DescribeVServerGroupAttribute|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|AddVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|RemoveVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|ModifyVServerGroupBackendServers|acs:slb:$regionid:$accountid:loadbalancer/$loadbalancerid|
|acs:ecs:$regionid:$accountid:instance/$instanceid|
|CreateAccessControlList|acs:slb:$regionid:$accountid:acl/\*|
|DeleteAccessControlList|acs:slb:$regionid:$accountid:acl/$aclid|
|DescribeAccessControlLists|acs:slb:$regionid:$accountid:acl/$aclid|
|DescribeAccessControlListAttribute|acs:slb:$regionid:$accountid:acl/$aclid|
|SetAccessControlListAttribute|acs:slb:$regionid:$accountid:acl/$aclid|
|AddAccessControlListEntry|acs:slb:$regionid:$accountid:acl/$aclid|
|RemoveAccessControlListEntry|acs:slb:$regionid:$accountid:acl/$aclid|

