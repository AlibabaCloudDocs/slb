# List of operations by function

The following tables list the API operations available for use in Server Load Balancer \(SLB\).

## SLB instances

|API|Description|
|---|-----------|
|[CreateLoadBalancer](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/CreateLoadBalancer.md)|Creates an SLB instance.|
|[ModifyLoadBalancerInternetSpec](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/ModifyLoadBalancerInternetSpec.md)|Changes the billing method of a public-facing SLB instance.|
|[DeleteLoadBalancer](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DeleteLoadBalancer.md)|Deletes a pay-as-you-go SLB instance.|
|[SetLoadBalancerStatus](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/SetLoadBalancerStatus.md)|Changes the state of an SLB instance.|
|[SetLoadBalancerName](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/SetLoadBalancerName.md)|Modifies the name of an SLB instance.|
|[DescribeLoadBalancers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DescribeLoadBalancers.md)|Queries SLB instances.|
|[DescribeLoadBalancerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DescribeLoadBalancerAttribute.md)|Queries detailed information about an SLB instance.|
|[DescribeRegions](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DescribeRegions.md)|Queries available regions.|
|[DescribeZones](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/DescribeZones.md)|Queries the zone information of a specified region.|
|[ModifyLoadBalancerInstanceSpec](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server Load Balancer (SLB) instances/ModifyLoadBalancerInstanceSpec.md)|Changes the type of an SLB instance.|

## Server certificates

|API|Description|
|---|-----------|
|[UploadServerCertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/UploadServerCertificate.md)|Uploads a server certificate.|
|[DeleteServerCertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/DeleteServerCertificate.md)|Deletes a server certificate.|
|[DescribeServerCertificates](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/DescribeServerCertificates.md)|Queries server certificates in a specified region.|
|[SetServerCertificateName](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/SetServerCertificateName.md)|Sets the name of a server certificate.|
|[UploadCACertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/UploadCACertificate.md)|Uploads a server certificate that is issued by a certificate authority \(CA\).|
|[DeleteCACertificate](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/DeleteCACertificate.md)|Deletes a server certificate that is issued by a CA.|
|[DescribeCACertificates](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/DescribeCACertificates.md)|Queries server certificates that are issued by CAs.|
|[SetCACertificateName](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Server certificates/SetCACertificateName.md)|Sets the name of a server certificate that is issued by a CA.|

## Listeners

|API|Description|
|---|-----------|
|[DeleteLoadBalancerListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Listeners/DeleteLoadBalancerListener.md)|Deletes a listener.|
|[StartLoadBalancerListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Listeners/StartLoadBalancerListener.md)|Enables a listener.|
|[StopLoadBalancerListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Listeners/StopLoadBalancerListener.md)|Disables a listener.|

## Backend servers

|API|Description|
|---|-----------|
|[AddBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Backend servers/AddBackendServers.md)|Adds backend servers.|
|[RemoveBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Backend servers/RemoveBackendServers.md)|Removes backend servers.|
|[SetBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Backend servers/SetBackendServers.md)|Sets the weights of backend servers.|
|[DescribeHealthStatus](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Backend servers/DescribeHealthStatus.md)|Queries the health status of backend servers.|

## Primary/secondary server groups

|API|Description|
|---|-----------|
|[CreateMasterSlaveServerGroup](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Active/standby server groups/CreateMasterSlaveServerGroup.md)|Creates a primary/secondary server group. A primary/secondary server group contains only two Elastic Compute Service \(ECS\) instances: one functions as the primary server and the other one functions as the secondary server.|
|[DeleteMasterSlaveServerGroup](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Active/standby server groups/DeleteMasterSlaveServerGroup.md)|Deletes a specified primary/secondary server group.|
|[DescribeMasterSlaveServerGroupAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Active/standby server groups/DescribeMasterSlaveServerGroupAttribute.md)|Queries detailed information about a specified primary/secondary server group.|
|[DescribeMasterSlaveServerGroups](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Active/standby server groups/DescribeMasterSlaveServerGroups.md)|Queries the list of backend servers in the primary/secondary server group.|

## VServer groups

|API|Description|
|---|-----------|
|[CreateVServerGroup](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/CreateVServerGroup.md)|Creates a VServer group and adds backend servers to the VServer group.|
|[SetVServerGroupAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/SetVServerGroupAttribute.md)|Modifies a VServer group.|
|[AddVServerGroupBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/AddVServerGroupBackendServers.md)|Adds backend servers to a specified VServer group.|
|[RemoveVServerGroupBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/RemoveVServerGroupBackendServers.md)|Deletes backend servers from a specified VServer group.|
|[ModifyVServerGroupBackendServers](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/ModifyVServerGroupBackendServers.md)|Replaces a backend server in a specified VServer group.|
|[DeleteVServerGroup](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/DeleteVServerGroup.md)|Deletes a VServer group.|
|[DescribeVServerGroups](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/DescribeVServerGroups.md)|Queries VServer groups.|
|[DescribeVServerGroupAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/VServer groups/DescribeVServerGroupAttribute.md)|Queries detailed information about a VServer group.|

## Access control

|API|Description|
|---|-----------|
|[CreateAccessControlList](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/CreateAccessControlList.md)|Creates an access control list \(ACL\).|
|[DeleteAccessControlList](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/DeleteAccessControlList.md)|Deletes an ACL.|
|[DescribeAccessControlLists](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/DescribeAccessControlLists.md)|Queries ACLs.|
|[DescribeAccessControlListAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/DescribeAccessControlListAttribute.md)|Queries the configurations of an ACL.|
|[SetAccessControlListAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/SetAccessControlListAttribute.md)|Changes the name of an ACL.|
|[AddAccessControlListEntry](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/AddAccessControlListEntry.md)|Adds IP address entries to an ACL.|
|[RemoveAccessControlListEntry](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control/RemoveAccessControlListEntry.md)|Deletes IP address entries from an ACL.|

## Forwarding rules

|API|Description|
|---|-----------|
|[CreateRules](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Forwarding rules/CreateRules.md)|Adds forwarding rules to a specified HTTP or HTTPS listener.|
|[DeleteRules](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Forwarding rules/DeleteRules.md)|Deletes a forwarding rule.|
|[SetRule](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Forwarding rules/SetRule.md)|Changes the destination VServer group in a forwarding rule.|
|[DescribeRuleAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Forwarding rules/DescribeRuleAttribute.md)|Queries the configurations of a specified forwarding rule.|
|[DescribeRules](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Forwarding rules/DescribeRules.md)|Queries forwarding rules that are configured for a specified listener.|

## Tags

|API|Description|
|---|-----------|
|[TagResources](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Tags/TagResources.md)|Creates tags and adds the tags to specified resources at a time.|
|[UntagResources](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Tags/UntagResources.md)|Removes tags from specified resources at a time.|
|[ListTagResources](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Tags/ListTagResources.md)|Queries tags that are added to one or more instances.|

## TCP listeners

|API|Description|
|---|-----------|
|[CreateLoadBalancerTCPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/TCP listeners/CreateLoadBalancerTCPListener.md)|Creates a TCP listener.|
|[SetLoadBalancerTCPListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/TCP listeners/SetLoadBalancerTCPListenerAttribute.md)|Modifies the configurations of a TCP listener.|
|[DescribeLoadBalancerTCPListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/TCP listeners/DescribeLoadBalancerTCPListenerAttribute.md)|Queries the configurations of a TCP listener.|

## HTTP listeners

|API|Description|
|---|-----------|
|[CreateLoadBalancerHTTPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP listeners/CreateLoadBalancerHTTPListener.md)|Creates an HTTP listener.|
|[SetLoadBalancerHTTPListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP listeners/SetLoadBalancerHTTPListenerAttribute.md)|Modifies the configurations of an HTTP listener.|
|[DescribeLoadBalancerHTTPListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTP listeners/DescribeLoadBalancerHTTPListenerAttribute.md)|Queries the configurations of an HTTP listener.|

## HTTPS listeners

|API|Description|
|---|-----------|
|[CreateLoadBalancerHTTPSListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTPS listeners/CreateLoadBalancerHTTPSListener.md)|Creates an HTTPS listener.|
|[SetLoadBalancerHTTPSListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTPS listeners/SetLoadBalancerHTTPSListenerAttribute.md)|Modifies the configurations of an HTTPS listener.|
|[DescribeLoadBalancerHTTPSListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/HTTPS listeners/DescribeLoadBalancerHTTPSListenerAttribute.md)|Queries the configurations of an HTTPS listener.|

## UDP listeners

|API|Description|
|---|-----------|
|[CreateLoadBalancerUDPListener](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/UDP listeners/CreateLoadBalancerUDPListener.md)|Creates a UDP listener.|
|[SetLoadBalancerUDPListenerAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/UDP listeners/SetLoadBalancerUDPListenerAttribute.md)|Modifies the configurations of a UDP listener.|
|[DescribeLoadBalancerUDPListenerAttribute]()|Queries the configurations of a UDP listener.|

## Access control \(earlier version\)

|API|Description|
|---|-----------|
|[SetListenerAccessControlStatus](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control (earlier version)/SetListenerAccessControlStatus.md)|Enables or disables the whitelist of a specified listener.|
|[RemoveListenerWhiteListItem](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control (earlier version)/RemoveListenerWhiteListItem.md)|Removes an IP address from the whitelist of a specified listener.|
|[DescribeListenerAccessControlAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control (earlier version)/DescribeListenerAccessControlAttribute.md)|Queries the whitelist configurations of a listener.|
|[AddListenerWhiteListItem](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Access control (earlier version)/AddListenerWhiteListItem.md)|Adds an IP address to the whitelist of a specified listener.|

## Additional certificates \(beta\)

|API|Description|
|---|-----------|
|[CreateDomainExtension](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Domain name extensions (Beta)/CreateDomainExtension.md)|Creates an additional certificate.|
|[SetDomainExtensionAttribute](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Domain name extensions (Beta)/SetDomainExtensionAttribute.md)|Replaces an additional certificate.|
|[DescribeDomainExtensions](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Domain name extensions (Beta)/DescribeDomainExtensions.md)|Queries additional certificates.|
|[DeleteDomainExtension](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Domain name extensions (Beta)/DeleteDomainExtension.md)|Deletes an additional certificate.|

## Resource queries

|API|Description|
|---|-----------|
|[DescribeAvailableResource](/intl.en-US/Classic Load Balancer/User Guide/Developer Guide/Quota query/DescribeAvailableResource.md)|Queries the resources that are available for purchase in a region.|

