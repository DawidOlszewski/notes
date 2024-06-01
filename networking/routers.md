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

```bash
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

> [!NOTE] 
> ### fun facts:
>* there exists something call `DF flag` (don't fragment) in ip header, which is used to find **MTU** (maximal transmission unit) in some path.
>
>* It works like `TTL` on traceroute. If some packet is too big ---> it has to be fragmenented, and this inforamtion is send back to the sender. And he changes the fragmentation. 
>
>* This process is called `PATH MTU`

## IPv4

`IANA` organization was responsible for managing ipv4 adresses. But it ocurred that demand is higher that that upper limit of supply

## IPv6

* 128 bit long: 8 blocks with 4 hex digits. Where delimeter is eq to: `:`
* you can stripe out leading zeros
* one consequtive subsequance of zeros can be replaced with `::` (e.g. `0000:0000:0000:0000:0000:0000:0000:0001/128` -> `::1/128` - localhost)
* default mask is equal to 64 bits. Its convinitent, beacuse other 64 bits can be equal MAC address

### ip6 to ip4 tunneling

Cental layers of internet are able to uses ipv6, but routers near our home devices are not. Therefore there exists `ip tunneling 6in4`.
Which means sending ipv6 inside ipv4. On the routing path exists a device called `tunnel broker` which decapsulates ipv4 and resend its content which is packet ipv6. 

##

> [!WARNING]
> why sending has to last at least 2*RTT


## ARP - Address Resolution Protocol

its design to recover `MAC addresses` and map them to `ip addresses`

it's flow looks like this:
* computer `A` wants to send package to some computer `B` with ipv4 address `x`;
* from forwarding table, takes specific interface that would be used to send this message
* it occuress that `A` doesn't know mac address of `B`. It utilizes ARP to get this info.
* By Data-link broadcast (`FF:FF:FF:FF:FF:FF` mac addr) sends `ARP frame` whos address is `x`.
* Few computers get this message, but only `B` will anwser with msg: "My mac address is `y`"
* `A` saves response in its `ARP cache`

### arp in linux

`ip neigh` - prints `arp cache`

`ip neigh flush all`

> [!NOTE]
> not every computer responds to `icmp` echo msgs (in `ping`), because it doesn't need to. But every computer that wants to be an active participant of internet has to reply to `arp requests`, in order to recive any external packets.

`arp-scan --interface=. subnetaddr` - arp mapping. Gives information about devices and its origins, because three first bytes in mac address correspons to `manufacturer company`.

### RARP - reverse arp TODO: and APIPA

## switch vs router

### switch:
* doesn't understad ip protocol
* so dosn't know what to do if resends some frame from ethernet to wifi, when `MTU` is too big
* `broadcast-storm` can happend when there is a cycle in switch topology. It can be avoided by usage of `spanning tree protocol`
  ![broadcast-storm](broadcast-storm.png)

### router:
* understands ip protocol


### icmp redirect TODO:


### domains TODO:
domena kolizyjna 
domena rozgłoszeniowa

## VAN - virtual lan

* do kazdego portu przełącznika ustalamy do jakich vlanó należy 
* w wysyłanych ramnkach pojawia się dodatkowe pole będąc enumber VLANu. ale jest przesyłane tylko w obrębie VLANu