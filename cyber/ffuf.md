# ffuf

`-w` - wordlist

`-u` - target url

`-c` - colors

`-fx` - depending on `x` filters an output

## examples
`ffuf -w SecLists/Discovery/Web-Content/common.txt -u https://site.com/FUZZ  -c -fs 3748`

`ffuf -w SecLists/Passwords/probable-v2-top1575.txt --request request.http --request-proto https -mc 200`