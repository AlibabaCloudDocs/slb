# Monitoring data and billing data

SLB monitors such metrics as the inbound and outbound traffic and the number of connections in real time. Billing data is also collected to calculate fees. Monitoring data and billing data differ in the items listed in the following table.

|Item|Monitoring data|Billing data|
|:---|:--------------|:-----------|
|Calculation method|SLB collects monitoring data at one minute intervals and reports the data to Cloud Monitor, which then calculates the average value at every 15 minute intervals.

 The monitoring data displayed in the SLB console is average values.

|SLB collects traffic data at one minute intervals, and reports the accumulated values at every one hour intervals to the billing system.

 The billing data reported to the billing system is accumulated values calculated at one hour intervals, whereas the monitoring data displayed in the console is of average values calculated at every 15 minute interval. |
|Latency|SLB provides real-time monitoring data. However, a short delay may occur during data collection, calculation, and display. Such a delay can cause a discrepancy between monitoring and billing data.|Billing data can be recorded after a maximum delay of three hours. For example, billing data generated between 01:00-02:00 is normally reported to the billing system before 03:00, but due to a delay, may be reported to the billing system at 05:00. This results in a discrepancy between billing data and monitoring data.|
|Purpose|The purpose of monitoring is to help you observe if instances are running normally. If the instances are running abnormally, you can take measures to resolve problems in a timely manner.|The purpose of billing data is to generate bills based on the actual usage of resources by your account.|

