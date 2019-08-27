# Overdue payments {#concept_lb1_w3n_22b .concept}

The load balancing service will not be stopped immediately after a Server Load Balancer \(SLB\) bill is overdue. We recommend that you renew SLB instances in time to avoid service interruptions.

The following will happen when a Pay-As-You-Go instance is overdue:

-   After a bill is overdue, the instance will keep running for 15 days. Then, the instance will be locked and the service stops.

    After the instance stops running, billing is also stopped.

-   If the SLB bill is still overdue 15 days after the instance is locked, the instance will be automatically released.

    The account owner will receive an email notification one day before the instance is released. The instance configuration and related data will be deleted and cannot be restored after the instance is released.


