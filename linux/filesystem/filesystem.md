# file system


## kernel interfaces in pseudo filesystems:

**procfs** - konfiguracja procesów i jądra

**sysfs** - pliki tekstowe z konfiugracją urządzeń

##  mount info

`findmnt -A` - prints mounted fs
`df` - print mounted fs with its stats
`lsblk` - prints blok devices (not only mounted). `-f` - format disk

## filesystem hierarchy standard

`/etc` - configuration files
`/bin` - binaries
`/sbin` - system binarys (for root)
`lib*` - librariues
`/run` - tmpfs - application temp variables
`/opt` - programs not split into bin and lib
`/var` - contains data that is changed when the system is running normally. It is specific for each system, i.e., not shared over the network with other computers.




`/usr` -second hierarchy (distribution mange)
`/usr/local` - third hier (user-manage file)


> [!NOTE]
> `/opt` vs `/usr/local`
> * Our application is a single binary, then we’ll copy or link it to `/usr/local`
> * We want to use an alternative of an existing system program build from source using make. In this case, we’ll install it under `/usr/local`
> * We’re going to deploy an application, and by design, all of its files are in the same directory. Then, we’ll deploy it by copying this directory into the `/opt/myapp` directory

# mounting 

`mount -t type -o options device dir`

## names of block devices

![blk-devices-names](./imgs/blk-devices-names.png)

## device mapper

