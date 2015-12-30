# Backups
Taking periodic backups is very important. A good backup can save the day in many bad scenarios. There are several points that one should take care of while taking backups:
* Backups should be non-obtrusive. If you got to take down your application or system in order to take a backup, then you need to fix the way you take backups.
* Having offsite backups is very important. Ask [codespaces](http://www.infoworld.com/article/2608076/data-center/murder-in-the-amazon-cloud.html).
* Never slack off with the security of the backups. Ask [BrowserStack](https://www.browserstack.com/attack-and-downtime-on-9-November).

# Strategies
* Live backups are most up-to-date. So never underestimate the importance of read replicas. However, if master gets poisoned, replicas get poisoned. 
* Do not ignore cold backups as well. Poisoning them is difficult.
* LVM and dm-crypt are your friends when you plan to secure the backups. Encrypted disks protect your data like nothing else on this planet.
* 