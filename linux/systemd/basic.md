# systemd

* init system - most important proces, very first started prcoess, that schedlue others (PID 1)

* unit - resources that `sysd` is able to manage  (services, timers, mounts, automount, ...)

## services - types of unit

service can be **active** or **inactive** (means is active currently)

service can be **disabled** or **enabled** (means will auto start during system startup)

`systemctl status service-name` - inspect services

`systemctl start service-name`

`systemctl enable service-name`

> [!NOTE]
> ![status-ctl](status-ctl.png)
> `preset` tells about default distro option

## how unitfiles are stored?

unit directory prio: 
* `/etc/systmd/system/`
* `/run/systemd/system`
* `/lib/systemd/system/httpd.service`

