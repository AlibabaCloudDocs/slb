# API overview {#doc_api_overview .concept}

This topic lists available Server Load Balancer \(SLB\) APIs.

## SLB instance { .section}

|API|Description|
|---|-----------|
| [CreateLoadBalancer](~~4182#Slb_CreateLoadBalancer~~)

 |Creates an SLB instance.|
| [DeleteLoadBalancer](~~4184#Slb_DeleteLoadBalancer~~)

 |Deletes a Pay-As-You-Go-billed SLB instance.|
| [DescribeLoadBalancerAttribute](~~4188#Slb_DescribeLoadBalancerAttribute~~)

 |Queries the details of an SLB instance.|
| [DescribeLoadBalancers](~~4187#Slb_DescribeLoadBalancers~~)

 |Queries created SLB instances.|
| [DescribeRegions](~~4189#Slb_DescribeRegions~~)

 |Queries available regions.|
| [DescribeZones](~~4190#Slb_DescribeZones~~)

 |Queries the zones in a region.|
| [ModifyLoadBalancerInstanceSpec](~~4191#Slb_ModifyLoadBalancerInstanceSpec~~)

 |Modifies the specification of an SLB instance.|
| [ModifyLoadBalancerInternetSpec](~~4183#Slb_ModifyLoadBalancerInternetSpec~~)

 |Modifies the billing method of an Internet SLB instance.|
| [ModifyLoadBalancerPayType](~~4192#Slb_ModifyLoadBalancerPayType~~)

 |Converts a Pay-As-You-Go-billed SLB instance to a Subscription-billed SLB instance.|
| [SetLoadBalancerName](~~4186#Slb_SetLoadBalancerName~~)

 |Modifies the name of an SLB instance.|
| [SetLoadBalancerStatus](~~4185#Slb_SetLoadBalancerStatus~~)

 |Sets the status of an SLB instance.|

## UDP listener { .section}

|API|Description|
|---|-----------|
| [CreateLoadBalancerUDPListener](~~4206#Slb_CreateLoadBalancerUDPListener~~)

 |Creates a UDP listener.|
| [DescribeLoadBalancerUDPListenerAttribute](~~4220#Slb_DescribeLoadBalancerUDPListenerAttribute~~)

 |Queries the configurations of a UDP listener.|
| [SetLoadBalancerUDPListenerAttribute](~~4216#Slb_SetLoadBalancerUDPListenerAttribute~~)

 |Modifies the configurations of a UDP listener.|

## HTTPS listener { .section}

|API|Description|
|---|-----------|
| [DescribeLoadBalancerHTTPSListenerAttribute](~~4218#Slb_DescribeLoadBalancerHTTPSListenerAttribute~~)

 |Queries the configurations of an HTTPS listener.|
| [SetLoadBalancerHTTPSListenerAttribute](~~4214#Slb_SetLoadBalancerHTTPSListenerAttribute~~)

 |Modifies the configurations of an HTTPS listener.|
| [CreateLoadBalancerHTTPSListener](~~4204#Slb_CreateLoadBalancerHTTPSListener~~)

 |Creates an HTTPS listener.|

## VServer group { .section}

|API|Description|
|---|-----------|
| [AddVServerGroupBackendServers](~~4235#Slb_AddVServerGroupBackendServers~~)

 |Adds backend servers to a specified VServer group.|
| [CreateVServerGroup](~~4233#Slb_CreateVServerGroup~~)

 |Creates a VServer group.|
| [SetVServerGroupAttribute](~~4234#Slb_SetVServerGroupAttribute~~)

 |Modifies the configurations of a VServer group.|
| [RemoveVServerGroupBackendServers](~~4236#Slb_RemoveVServerGroupBackendServers~~)

 |Removes backend servers from a specified VServer group.|
| [ModifyVServerGroupBackendServers](~~4237#Slb_ModifyVServerGroupBackendServers~~)

 |Replaces backend servers in a VServer group.|
| [DeleteVServerGroup](~~4238#Slb_DeleteVServerGroup~~)

 |Deletes a VServer group.|
| [DescribeVServerGroups](~~4239#Slb_DescribeVServerGroups~~)

 |Queries the list of VServer groups.|
| [DescribeVServerGroupAttribute](~~4240#Slb_DescribeVServerGroupAttribute~~)

 |Queries the details of a VServer group.|

## Listener { .section}

|API|Description|
|---|-----------|
| [StartLoadBalancerListener](~~4208#Slb_StartLoadBalancerListener~~)

 |Starts a listener.|
| [StopLoadBalancerListener](~~4209#Slb_StopLoadBalancerListener~~)

 |Stops a listener.|
| [DeleteLoadBalancerListener](~~4207#Slb_DeleteLoadBalancerListener~~)

 |Deletes a listener.|

## Tag { .section}

|API|Description|
|---|-----------|
| [AddTags](~~22728#Slb_AddTags~~)

 |Adds tags to a specified SLB instance.|
| [DescribeTags](~~4257#Slb_DescribeTags~~)

 |Queries details of specified tags.|
| [RemoveTags](~~4258#Slb_RemoveTags~~)

 |Remove tags that are associated with an SLB instance.|

## Domain name extension \(Beta\) { .section}

|API|Description|
|---|-----------|
| [CreateDomainExtension](~~15373#Slb_CreateDomainExtension~~)

 |Creates a domain name extension.|
| [SetDomainExtensionAttribute](~~16112#Slb_SetDomainExtensionAttribute~~)

 |Modifies the certificate of a domain name extension.|
| [DescribeDomainExtensions](~~16113#Slb_DescribeDomainExtensions~~)

 |Queries the added domain name extensions.|
| [DeleteDomainExtension](~~16129#Slb_DeleteDomainExtension~~)

 |Deletes a domain name extension.|

## Active/standby server group { .section}

|API|Description|
|---|-----------|
| [CreateMasterSlaveServerGroup](~~4228#Slb_CreateMasterSlaveServerGroup~~)

 |Creates an active/standby server group. An active/standby server group can only contain two ECS instances. One is the active backend server and the other one is the standby backend server.|
| [DeleteMasterSlaveServerGroup](~~4229#Slb_DeleteMasterSlaveServerGroup~~)

 |Deletes an active/standby server group.|
| [DescribeMasterSlaveServerGroupAttribute](~~4230#Slb_DescribeMasterSlaveServerGroupAttribute~~)

 |Queries the details of a specified active/standby server group.|
| [DescribeMasterSlaveServerGroups](~~4231#Slb_DescribeMasterSlaveServerGroups~~)

 |Queries the created active/standby server groups.|

## Forwarding rule { .section}

|API|Description|
|---|-----------|
| [CreateRules](~~4250#Slb_CreateRules~~)

 |Adds forwarding rules for a specified HTTP or HTTPS listener.|
| [DeleteRules](~~4251#Slb_DeleteRules~~)

 |Deletes forwarding rules.|
| [SetRule](~~4252#Slb_SetRule~~)

 |Changes the destination VServer group of a forwarding rule.|
| [DescribeRuleAttribute](~~4253#Slb_DescribeRuleAttribute~~)

 |Queries the settings of a specified forwarding rule.|
| [DescribeRules](~~4254#Slb_DescribeRules~~)

 |Queries the forwarding rules that have been configured for a specified listener.|

## Access control { .section}

|API|Description|
|---|-----------|
| [AddAccessControlListEntry](~~4247#Slb_AddAccessControlListEntry~~)

 |Adds IP addresses to an access control list.|
| [CreateAccessControlList](~~4242#Slb_CreateAccessControlList~~)

 |Creates an access control list.|
| [DeleteAccessControlList](~~4243#Slb_DeleteAccessControlList~~)

 |Deletes an access control list.|
| [DescribeAccessControlListAttribute](~~4245#Slb_DescribeAccessControlListAttribute~~)

 |Queries the settings of a specified access control list.|
| [DescribeAccessControlLists](~~4244#Slb_DescribeAccessControlLists~~)

 |Queries created access control lists.|
| [RemoveAccessControlListEntry](~~4248#Slb_RemoveAccessControlListEntry~~)

 |Deletes IP addresses from an access control list.|
| [SetAccessControlListAttribute](~~4246#Slb_SetAccessControlListAttribute~~)

 |Modifies the name of an access control list.|

## Access control \(earlier version\) { .section}

|API|Description|
|---|-----------|
| [AddListenerWhiteListItem](~~21218#Slb_AddListenerWhiteListItem~~)

 |Adds IP addresses to a listener whitelist.|
| [DescribeListenerAccessControlAttribute](~~4221#Slb_DescribeListenerAccessControlAttribute~~)

 |Queries the whitelist settings of a specified listener.|
| [SetListenerAccessControlStatus](~~4210#Slb_SetListenerAccessControlStatus~~)

 |Enables or disables the access control whitelist function for a specified listener.|
| [RemoveListenerWhiteListItem](~~4212#Slb_RemoveListenerWhiteListItem~~)

 |Deletes IP addresses from a listener whitelist.|

## Server certificate { .section}

|API|Description|
|---|-----------|
| [UploadServerCertificate](~~4194#Slb_UploadServerCertificate~~)

 |Uploads a server certificate.|
| [DeleteServerCertificate](~~4195#Slb_DeleteServerCertificate~~)

 |Deletes a server certificate.|
| [DescribeServerCertificates](~~4196#Slb_DescribeServerCertificates~~)

 |Queries the server certificates of a specified region.|
| [SetServerCertificateName](~~4197#Slb_SetServerCertificateName~~)

 |Sets the name of a server certificate.|
| [UploadCACertificate](~~4198#Slb_UploadCACertificate~~)

 |Uploads a CA certificate.|
| [DeleteCACertificate](~~4199#Slb_DeleteCACertificate~~)

 |Deletes a CA certificate.|
| [DescribeCACertificates](~~4200#Slb_DescribeCACertificates~~)

 |Queries the list of CA certificates.|
| [SetCACertificateName](~~4201#Slb_SetCACertificateName~~)

 |Sets the name of a CA Certificate.|

