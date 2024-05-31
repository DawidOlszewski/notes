chceck parameters yuou system was booted with `cat /proc/cmdline`

every filesystem is represented with `file_system_type` struct in kernel

globalbna zmienna w jądrze `file_system` zawierająca tablice fs jest startowana przez funkcje `init_rootfs` podczas rozruchu jądra (jej ostatnim elementem zawsze jest rootfs)

LVM - partycje wirtualne

bootloder ładuje do pamięci jądro oraz plik initrd.img oraz przekauzje strukturę boot_params




System plików `tmpfs` tworzony przez jądro w pamięci operacyjnej.
Funkcja `mount(2) `i polecenie `mount`(8) pozwalają zlecić jądru utworzenie tmpfs: 
`mkdir /var/mytmpfs`
m`ount -t tmpfs -o size=100M none /var/mytmpfs`
`mount -t tmpfs -o remount,size=200M none /var/mytmpfs`
``umount /var/mytmpfs`
Można umieścić odpowiedni wpis w `/etc/fstab`:
`none /var/mytmpfs tmpfs size=100M 0 0`
Można też np. size=40% (procent dostępnej pamięci RAM).
Domyślnie 50% RAM.
Uwaga: jednostki Ki, Mi, Gi opisane w mount(8) nie działają



UWAGA
/tmp nie jest w ramie