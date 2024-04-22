# credentialed enumeration

usage of `crackmapexec`

common usage:
* `crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --users` - prints every domain user with tag `badPwdCount` and `baddpwdtime`
* `crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --groups`
* `crackmapexec smb 172.16.5.130 -u forend -p Klmcargo2 --loggedon-users`
* `crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 --shares`
> [!NOTE]
> common shares content: (`$`  means hidden)
> * `ADMIN$`- This is a resource that is used during remote administration of a computer for example to install software on remote computers. Only administrators have access to it.
> * `C$` - This share is mapped to C:\ location on the disk so you can have access to shared files on the server or with administrator permissions to the entire filesystem.
> * `IPC$` - This is a resource that shares the named pipes that is being used for communicating between programs — Inter Process Communication
> * `NETLOGON`
> * `SYSVOL`
> 
> ```
> Purpose of the SYSVOL folder is to hold two things. Scripts and Policies.
>
> All group policies applied to a particular domain exist in the SYSVOL<domain_name>\Policies. The NETLOGON folder has been changed (Windows 2000) to point to the SYSVOL folder called Scripts.
> 
> Any changes to the %systemroot%\SYSVOL folder on any DC is replicated to the other DCs in the domain.
> 
> The NETLOGON folder is still there, but it resides in the SYSVOL\Scripts. You can still search for that folder by typing in NETLOGON. BUt it actually is %systemroot%\WINDOWS\SYSVOL\domain\Scripts.
> ```
* `crackmapexec smb 172.16.5.5 -u forend -p Klmcargo2 -M spider_plus --share 'Department Shares'` - output is located in `/tmp/cme_spider_plus/<ip of host>`
* `smbmap -u forend -p Klmcargo2 -d INLANEFREIGHT.LOCAL -H 172.16.5.5 -R 'Department Shares' --dir-only`
### rpcclient
`rpcclient -U "" -N 172.16.5.5` - SMB null
