# ifup, ifdown

## /etc/netowrk/interfaces

* `#` at the beggining of line ignores this line
* `\` - extends line to next line 
* list of keywords: 
  * `auto`
  * `iface`
  * `mapping`
  * `allow-*` 

Lines beginning with `allow-` are used to identify interfaces that should be brought up automatically by various subsystems. This may be done using a command such as `ifup --allow=hotplug eth0 eth1`, which will only bring up eth0 or eth1 if it is listed in an `allow-hotplug` line. Note that `allow-auto` and `auto` are synonyms. 


example:
```
auto lo eth0
allow-hotplug eth1
iface lo inet loopback
mapping eth0 
        script /usr/local/sbin/map-scheme
        map HOME eth0-home
        map WORK eth0-work
iface eth0-home inet static
        address 192.168.1.1
        netmask 255.255.255.0
        up flush-mail
iface eth0-work inet dhcp
iface eth1 inet dhcp
```
