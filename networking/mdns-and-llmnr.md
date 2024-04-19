# mdns and llmnr

resolving hostnames to ips in a decentralized way using multicast addresses, but only in local netowrks

## differences
* funfact: `LLMNR` is younger than `mDNS`. Was created later. 

* `mDNS` sends responses to multicast, therefore anyone can see it 
* `LLMNR` sends responses to requestor


* `mDNS` uses differnet hostname to resolve `host.local` insted of `host`
* `LLMNR` uses standard hostname: `host`


> [!NOTE]
> `mDNS` and `LLMNR` are considered `zeroconf_technoliges`


## how service resolution protocol works (dns sd)
`