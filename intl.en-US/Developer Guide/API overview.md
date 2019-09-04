# API overview {#doc_17814 .concept}

This topic lists available Server Load Balancer \(SLB\) APIs.

## SLB instances {#section_dck_d8e_9ge .section}

|API|Description|
|---|-----------|
|[CreateLoadBalancer](~~27577~~)|Creates an SLB instance.|
|[ModifyLoadBalancerInternetSpec](~~27578~~)|Modifies the billing method of an Internet SLB instance.|
|[DeleteLoadBalancer](~~27579~~)|Deletes a Pay-As-You-Go SLB instance.|
|[SetLoadBalancerStatus](~~27580~~)|Sets the status of an SLB instance.|
|[SetLoadBalancerName](~~27581~~)|Modifies the name of an SLB instance.|
|[DescribeLoadBalancers](~~27582~~)|Queries created SLB instances.|
|[DescribeLoadBalancerAttribute](~~27583~~)|Queries the details of an SLB instance.|
|[DescribeRegions](~~27584~~)|Queries available regions.|
|[DescribeZones](~~27585~~)|Queries the zones in a region.|
|[ModifyLoadBalancerInstanceSpec](~~53360~~)|Modifies the specification of an SLB instance.|

## UDP listeners {#section_ibq_apv_ked .section}

|API|Description|
|---|-----------|
|[CreateLoadBalancerUDPListener](~~27595~~)|Creates a UDP listener.|
|[SetLoadBalancerUDPListenerAttribute](~~27605~~)|Modifies the configurations of a UDP listener.|
|[DescribeLoadBalancerUDPListenerAttribute](~~27609~~)|Queries the configurations of a UDP listener.|

## TCP listeners {#section_vys_j7b_xu3 .section}

|API|Description|
|---|-----------|
|[CreateLoadBalancerTCPListener](~~27594~~)|Creates a TCP listener.|
|[SetLoadBalancerTCPListenerAttribute](~~27604~~)|Modifies the configurations of a TCP listener.|
|[DescribeLoadBalancerTCPListenerAttribute](~~27608~~)|Queries the configurations of a TCP listener.|

## HTTP listeners {#section_mn5_obu_jsr .section}

|API|Description|
|---|-----------|
|[SetLoadBalancerHTTPListenerAttribute](~~27602~~)|Modifies the configurations of an HTTP listener.|
|[CreateLoadBalancerHTTPListener](~~27592~~)|Creates an HTTP listener.|
|[DescribeLoadBalancerHTTPListenerAttribute](~~27606~~)|Queries the configurations of an HTTP listener.|

## HTTPS listeners {#section_vnz_fwp_a5o .section}

|API|Description|
|---|-----------|
|[SetLoadBalancerHTTPSListenerAttribute](~~27603~~)|Modifies the configurations of an HTTPS listener.|
|[DescribeLoadBalancerHTTPSListenerAttribute](~~27607~~)|Queries the configurations of an HTTPS listener.|
|[CreateLoadBalancerHTTPSListener](~~27593~~)|Creates an HTTPS listener.|

## Listeners {#section_68i_swd_m8c .section}

|API|Description|
|---|-----------|
|[StartLoadBalancerListener](~~27597~~)|Starts a listener.|
|[StopLoadBalancerListener](~~27598~~)|Stops a listener.|
|[DeleteLoadBalancerListener](~~27596~~)|Deletes a listener.|

## Backend servers {#section_hhv_ttq_4h5 .section}

|API|Description|
|---|-----------|
|[SetBackendServers](~~27634~~)|Sets the weights of backend severs.|
|[AddBackendServers](~~27632~~)|Adds backend servers.|
|[RemoveBackendServers](~~27633~~)|Removes backend servers.|
|[DescribeHealthStatus](~~27635~~)|Queries the health status of a backend server.|

## VServer groups {#section_ras_dsw_cz8 .section}

|API|Description|
|---|-----------|
|[DescribeVServerGroupAttribute](~~35224~~)|Queries the details of a VServer group.|
|[CreateVServerGroup](~~35215~~)|Creates a VServer group.|
|[AddVServerGroupBackendServers](~~35218~~)|Adds backend servers to a VServer group.|
|[SetVServerGroupAttribute](~~35217~~)|Modifies the configurations of a VServer group.|
|[RemoveVServerGroupBackendServers](~~35219~~)|Removes backend servers from a VServer group.|
|[ModifyVServerGroupBackendServers](~~35220~~)|Replaces backend servers in a VServer group.|
|[DeleteVServerGroup](~~35221~~)|Deletes a VServer group.|
|[DescribeVServerGroups](~~35222~~)|Queries the list of VServer groups.|

## Active/standby server groups {#section_sob_fkb_hjv .section}

|API|Description|
|---|-----------|
|[CreateMasterSlaveServerGroup](~~50506~~)|Creates an active/standby server group. An active/standby server group can only contain two ECS instances. One is the active backend server and the other one is the standby backend server.|
|[DeleteMasterSlaveServerGroup](~~50507~~)|Deletes an active/standby server group.|
|[DescribeMasterSlaveServerGroupAttribute](~~50509~~)|Queries the details of an active/standby server group.|
|[DescribeMasterSlaveServerGroups](~~50508~~)|Queries created active/standby server groups.|

## Server certificates {#section_hqf_dew_bjo .section}

|API|Description|
|---|-----------|
|[UploadServerCertificate](~~34181~~)|Uploads a server certificate.|
|[DeleteServerCertificate](~~34182~~)|Deletes a server certificate.|
|[DescribeServerCertificates](~~34183~~)|Queries the server certificates of a region.|
|[SetServerCertificateName](~~34184~~)|Sets the name of a server certificate.|
|[UploadCACertificate](~~34935~~)|Uploads a CA certificate.|
|[DeleteCACertificate](~~34937~~)|Deletes a CA certificate.|
|[DescribeCACertificates](~~34938~~)|Queries the list of CA certificates.|
|[SetCACertificateName](~~34936~~)|Sets the name of a CA Certificate.|

## Domain name extensions \(Beta\) {#section_r5b_ksx_twd .section}

|API|Description|
|---|-----------|
|[CreateDomainExtension](~~85912~~)|Creates a domain name extension.|
|[SetDomainExtensionAttribute](~~85913~~)|Modifies the certificate of a domain name extension.|
|[DescribeDomainExtensions](~~85914~~)|Queries added domain name extensions.|
|[DeleteDomainExtension](~~85915~~)|Deletes a domain name extension.|

## Query resources {#section_x3p_b3w_pg7 .section}

|API|Description|
|---|-----------|
|[DescribeAvailableResource](~~117645~~)|Queries the resources available for purchase in a region.|

## Tags {#section_7f2_siz_w6c .section}

|API|Description|
|---|-----------|
|[RemoveTags](~~42872~~)|Remove tags that are associated with an SLB instance.|
|[AddTags](~~42871~~)|Adds tags to an SLB instance.|
|[DescribeTags](~~42873~~)|Queries details of specified tags.|

## Forwarding rules {#section_lnk_eaf_ro1 .section}

|API|Description|
|---|-----------|
|[CreateRules](~~35226~~)|Adds forwarding rules for an HTTP or HTTPS listener.|
|[DeleteRules](~~35227~~)|Deletes forwarding rules.|
|[SetRule](~~35228~~)|Changes the destination VServer group of a forwarding rule.|
|[DescribeRuleAttribute](~~35229~~)|Queries the settings of a forwarding rule.|
|[DescribeRules](~~35230~~)|Queries the forwarding rules that have been configured for a listener.|

## Access control {#section_hho_yy2_8l5 .section}

|API|Description|
|---|-----------|
|[CreateAccessControlList](~~70015~~)|Creates an access control list.|
|[DeleteAccessControlList](~~70056~~)|Deletes an access control list.|
|[DescribeAccessControlLists](~~70052~~)|Queries created access control lists.|
|[DescribeAccessControlListAttribute](~~70051~~)|Queries the settings of an access control list.|
|[SetAccessControlListAttribute](~~70022~~)|Modifies the name of an access control list.|
|[AddAccessControlListEntry](~~70023~~)|Adds IP entries to an access control list.|
|[RemoveAccessControlListEntry](~~70055~~)|Deletes IP entries from an access control list.|

## Access control \(earlier version\) {#section_e8u_i7e_nuq .section}

|API|Description|
|---|-----------|
|[RemoveListenerWhiteListItem](~~27601~~)|Deletes IP addresses from a listener whitelist.|
|[AddListenerWhiteListItem](~~27600~~)|Adds IP addresses to a listener whitelist.|
|[DescribeListenerAccessControlAttribute](~~27610~~)|Queries the whitelist settings of a listener.|
|[SetListenerAccessControlStatus](~~27599~~)|Enables or disables the access control whitelist function for a listener.|

