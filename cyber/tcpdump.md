# tcpdump - wireshark for non-graphical interface

`tcpdump -i eth0 -v host ip `
`src` and `dst`

`and` and `or`  - concatenating filters

`tcpdump -i eth0 -v src port 443 and dst 192.168.1.107`

`-w` flag save traffic into pcap