# Monitoring data and billing data {#concept_dzd_4hs_wdb .concept}

Server Load Balancer \(SLB\) provides a monitoring function that monitors such metrics as the inbound and outbound traffic and the number of connections. You can view real-time monitoring data in the console. Besides monitoring data, billing data is also collected, but it is collected for the calculation of fees to be charged. Monitoring data and billing data differ given the factors described as follows.

|Factor|Monitoring Data|Billing data|
|:-----|:--------------|:-----------|
|Calculation method| The SLB system collects monitoring data every minute, and reports the data to CloudMonitor. After every 15 minutes, CloudMonitor calculates the average value of data collected in that time period.

 The network traffic data displayed in the console is the average value calculated.

 | Billing data is collected every minute, and the SLB system reports the accumulated value once each hour to the billing system.

 Monitoring data is the calculated average for a 15-minute time period, but the billing data is the accumulated value in a billing cycle.

 |
|Latency|SLB provides real-time monitoring data. However, a short delay may inevitably occur during the process of data collection, calculation, and display. Although this delay is nearly immeasurable, it can create a certain degree of discrepancy between the monitoring and billing data.|Billing data can allow up to a three-hour delay. For example, billing data generated between 01:00-02:00 is normally reported to the billing system before 03:00. However, data may be reported up to three hours later, with the last reporting time being 05:00. As a result, there may be a discrepancy between billing data and monitoring data.|
|Purpose|The purpose of monitoring is to help you observe if instances are running normally. If not, you can take measures to solve problems in a timely manner.|The purpose of billing is to generate bills. Monitoring data cannot be used as billing data.|

