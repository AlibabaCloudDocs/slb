# Limits  {#concept_mfm_mp4_tdb .concept}

This topic lists the resource quotas of Server Load Balancer \(SLB\).

SLB provides an API to query the default limits of an SLB instance.

|Resource|Default limit|
|:-------|:------------|
|**Limits on SLB instances**|
|The number of SLB instances per account|30|
|The number of times that an ECS instance can be added to SLB instances|50|
|The number of backend servers that can be added to an SLB instance|200|
|The number of listeners that can be added to an SLB instance|50|
|The number of domain name-based and URL-based forwarding rules that can be added to a Layer-7 listener|40|
|The number of domain name extensions that an HTTPS listener can create|3|
|The frequency of API calls per AccessKey|5,000 times/day|
|The frontend and backend port range used by a listener \(public cloud\)|1-65535|
|The frontend and backend port range used by a listener \(Ant Financial Cloud\)|80, 443, 2800-3300, 5000-10000, 13000-14000|
|**Limits on certificates**|
|The number of server certificates that can be uploaded in a region|100|
|The number of CA certificates that can be uploaded in a region|100|
|**Limits on access control lists**|
|The number of access control lists that can be created in a region|50|
|The number of IP entries that can be added to an access control list|300|
|The number of IP entries that can be added to an access control list in an API call|50|
|The number of times that an access control list can be added to listeners|50|

