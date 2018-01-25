# Monitoring RocketChat with Zabbix

RocketChat is a team chat software (like Slack). Zabbix is a monitoring tools.

This repository contains some file to monitor RocketChat with Zabbix.

This template was tested on Zabbix 3.4.

# Monitoring spectre
This template will track :
  * RocketChat Active Users (all users)
  * RocketChat Online Users (connected users, online or aways)
  * Rocket Total Channel Messages (Number of messages since instance creation)
  * Rocket Total Private Group Messages (Number of messages since instance creation)
  * Rocket Total Channels (Number of channels)
  * Rocket Total Private Groups (Number of channels)

# Installation
  * Zabbix server should have Python3
  * Copy **rocketchat-stats** from  **server/externalscripts/** to your Zabbix server to **ExternalScripts** location (ie. /var/lib/zabbix/externals-scripts/)
  * Import RocketChat-Stats.xml from **templates/** into your Zabbix server
  * Add Template to host which run RocketChat 

# Configuration

On RocketChat, add an user with a role which contains permissions **view-statistics**. Yes, admin role had this permission, but is it really suitable ?

Edit **rocketchat-stats** on your Zabbix server and configure :

```
### Define RocketChat user !
url = "https://rocket_chat.fqdn/chat/api"
user = "zabbix_stats_user"
password = "passw0rd" 
```

# TODO

These checks are on our roadmap.

 * Per channels/groups statistics
 * Dead channels/groups detection (less than X message by since y days)
 * Hot channels/groups detection (more than X message by since y days)
 * Orphaned channels/groups detection (0 members)
 * Dead users detection (no login since X days)
 * Create some triggers on items
  
Feel free create issues for new features.
  
# License
GNU General Public License v3
