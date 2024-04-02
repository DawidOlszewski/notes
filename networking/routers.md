# routers

## OSPF vs RIP - dynamic routing protocols

`OSPF` (open shortest path first) is a `link-state` protocol, which means that computers in the same network know the whole connection graph (neighbours of each computer), therefore they are able to locally find the best route to any computer

`RIP` (routing information protocol) is a `distance-vector` routing algorithm which means that each router knows only the **probable** distance to each computer connected to the network. Therefore, is more prone to chosing inefficent route

## How to use `frr` 

You have to start dameon called `frr` (free range routing)

* `vtysh` opens special `frr` terminal
  * `show interface`
  * `show ip route`
  * `configure terminal` command in `vtysh` changes terminal to `configuration mode`
  * `show running-config` *TODO: where are these file* 
  * `copy running-config startup-config` - saving temp configureation


## How to set RIP in `frr` 

you would have to change `/etc/frr/daemons` by setting `ripd=yes` 

```
virbian(config)# router rip
virbian(config-router)# version 2
virbian(config-router)# network 192.168.1.0/24
virbian(config-router)# network 192.168.2.0/24
```


## what happening inside a router

### cheap:

1. router receives packet and send msg to proc
2. proc copies pakcet to ram
3. if there is any unused port the processor gets informed
4. processor copis packet from ram to output port

### expensive:

* same, but:
* has optimalized swiching structure, that uses forwarding table (benes networks) that is memorized in every output port


## fun facts:
* there exists something call `DF flag` (don't fragment) in ip header, which is used to find **MTU** (maximal transmission unit) in some path.
 
* It works like `TTL` on traceroute. If some packet is too big ---> it has to be fragmenented, and this inforamtion is send back to the sender. And he changes the fragmentation. 

> [!NOTE]
> This process is called `PATH MTU`

## IPv4

`IANA` organization was responsible for managing ipv4 adresses. But it ocurred that demand is higher that that upper limit of supply

## IPv6

* 128 bit long: 8 blocks with 4 hex digits. Where delimeter is eq to: `:`
* you can stripe out leading zeros
* one consequtive subsequance of zeros can be replaced with `::` (e.g. `0000:0000:0000:0000:0000:0000:0000:0001/128` -> `::1/128` - localhost)
* default mask is equal to 64 bits. Its convinitent, beacuse other 64 bits can be equal MAC address

### ip6 to ip4 tunneling

Cental layers of internet are able to uses ipv6, but routers near our home devices are not. Therefore there exists `ip tunneling 6in4`.
Which means sending ipv6 inside ipv4. On the path exists a device called `tunnel broker` which decapsulates ipv4 and resend its content which is packet with ipv6. 


# ping
if intermediate router doesn't know where to send ping packet, it sends `Destination host unreachable` packet to sender
