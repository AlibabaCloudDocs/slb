# Shared instance bandwidth {#concept_jfw_skw_tdb .concept}

Load Balancing supports the total bandwidth of all listening shared instances under a load balancing instance that is priced by bandwidth. When you create a monitor, you can set the bandwidth peak or you can choose not to set it.

-   Configuration: You can limit the bandwidth of the listen, however, the sum of all listen bandwidth peaks cannot exceed the instance's bandwidth peaks.
-   No limit: if you do not limit bandwidth, listen for shared instance bandwidth under the instance.

    ![](images/2830_en-US.png)


## How do I share bandwidth? {#section_mgx_fkb_wdb .section}

If you purchased a load balancing instance with a bandwidth peak of 10 MB, and created three listeners under this instance \(Listening A, listening B, listening C\). The peak bandwidth of listen a is set 4 MB, two other listeners do not have the bandwidth peak set. The bandwidth usage of the three listeners can occur in the following situations:

-   If listening to a and listening to C has never been out of traffic, then listening B can run up to the remaining 6 MB bandwidth \(10 MB-4 MB\).
-   If listening for C has never been out of traffic, and listening for B has been very large, the remaining 6 MB bandwidth is exceeded. At this point, listening for B has generated drops, and listening for a only 4 MB The outflow of does not exceed the set bandwidth peak, so no drops are generated.
-   If listen a is always running at full speed \(Listening peak 4 MB \), then listening for B and listening for C also have traffic and both listen for very large amounts of traffic, so listening for B and listening for C will share the remaining 6 MB. Bandwidth. At this point, listening for a traffic will not be affected by listening for B and listening for C, always up to 4 MB Reserved Peak; if listening B is the same size as listening C out of traffic, the bandwidth used by the two listeners goes closer to the same point.

Therefore, the limit to listen bandwidth is Resource Reservation, this is to ensure that the core business always has enough bandwidth. Non-core business can not set listen bandwidth values, they compete for the remaining bandwidth resources of the instance.

