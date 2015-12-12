# What is monitoring?
The art of measuring health of any system or applicaiton is called monitoring. Any business should be aware of the health of their systems. An unhealthy system is a potential disaster and can effect negatively on revenues. 

## How to monitor?
There are several tools out there to help you monitor your systems and applications. Below is a list of most common tools. Note that this list is not exhaustive. 
#### Self hosted
* Nagios
* Icinga

#### Hosted by third party
* Server density
* New Relic

We recommend using Nagios. It is a very mature monitoring tool with a great community and customization options.

##What should we monitor?
Honestly, there is no end to monitoring. It is an iterative process where one should identify the potential points of failure and keep on adding and improving the monitoring suites. We have a list of bare minimum things that should be monitored by a monitoring suite.
#### System resources
* Load average
* Free memory
* Disk
* NTP
* SSH
 
#### Application Resources
* Port checks
* Protocol specific checks like http(s)