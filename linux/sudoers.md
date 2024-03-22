# sudoers

> [!NOTE]
> difference between `su` and `su -`
>
> `su -` invokes a login shell after switching the user. A login shell resets most environment variables, providing a clean base.
>
> `su` just switches the user, providing a normal shell with an environment nearly the same as with the old user.

> [!NOTE]
> `sudo -l` prints current users privileges in a format from below


`groups` - prints all users groups

# WTF? -  %groups ALL=(ALL:ALL) ALL

if the first symbol in a line is a `%groups` it's about group priviledges
in the other case it is about `specific-user`

### **ALL**=(ALL:ALL) ALL

the host (hostname) or the server that you are allowed to executes commands on


### ALL=**(ALL:ALL)** ALL

first - users that you can impersonate\
second - groups that you can impersonate

### ALL=(ALL:ALL) **ALL** (e.g. ALL=(ALL:ALL) /user/bin/apt,/usr/bin/rm)

commands that you can execute

> [!NOTE]
> sudoers file is not sensitvie to tab or spaces
> `ALL=(ALL:ALL) NOPASSWD: /user/bin/apt,/usr/bin/rm`


> [!NOTE]
> allows to use sudo as a user without providing a passwd
> `ALL=(ALL:ALL) NOPASSWD: /user/bin/apt,/usr/bin/rm`


# how and why not by hand change `/etc/sudoers`

if we made a mistake we could have lost the ablity to change this file in a server,

Therefore there exists a command that does syntax checking for us `visudo` (during error print `x`, which means invalidate changes)

# `/etc/sudoers.d` directory

`/etc/sudoers.d` is a directory that allows to addd sudo priviledges to some users as files