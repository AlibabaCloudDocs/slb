Announcement on optimization for Cloud Monitor 
===================================================================

Cloud Monitor for Server Load Balancer (SLB) is scheduled to be optimized in different regions. The optimization improves user experience and allows you to monitor more specific resources.

Optimization details 
-----------------------------------------

You can set alert rules for the default listener and the URL of a forwarding rule.

Optimization impact 
----------------------------------------

If you have set alert rules for the metric "number of healthy ECS instances" or "number of unhealthy ECS instances", the health check data of the default listener no longer contains the health check data of forwarding rules after the optimization. If you want to monitor health checks of forwarding rules, you can set different alert rules for different forwarding rules. For more information, see [Set alert rules in the CloudMonitor console](https://www.alibabacloud.com/help/doc-detail/85933.htm?).
**Note**

The optimization only modifies the reporting logic of health checks and does not affect the forwarding of your business traffic. If false positives are generated due to the optimization, you can modify the alert settings based on the actual scenario. For more information, see [Set alert rules in the CloudMonitor console](https://www.alibabacloud.com/help/doc-detail/85933.htm?).
