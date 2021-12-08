# Mikrotik Failover Script
## Features:
- Main/backup failover with 2 dhcp-client interfaces
- Rely on multiple remote test hosts to decide if the main link is working properly
- Automaticaly add/remove required routes to remote test hosts
- Adjust testHosts routes if the gateway change
- Configurable "ping success rate expected"
- Stop pinging testHosts as soon as the expected rate is reached to avoid unnecessary traffic
- Release DHCP lease in mainInterface on link failure to trigger a renew.
(This is usefull if the provider change the subnet on its side but our DHCP lease is not expired yet)
- Doesn't need :global variable
- Doesn't need specific configuration other than using dhcp-client on both main/backup interfaces

## Limitations:
- Hosts in testHosts array can't be reach through backupInterface if mainInterface have an active DHCP lease
- MainInterface and backupInterface must be configured in dhcp-client
- Only work with IPv4

## How to use it
- Set the mainInterface and the backupInterface variable (dhcp client configuration must exist)
- Set the testHosts you want to use as reliable remote host to test connectivity
- Upload the script to your router
- Schedule it to run every minutes  

*Special thanks to author of this [thread](https://forum.mikrotik.com/viewtopic.php?p=875199&hilit=renew+ip#p875199) @Halesk2k*
