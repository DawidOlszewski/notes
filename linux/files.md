# everything is a file

* file api  utilizes the fact that every 
* pliki binarene pozwalalją ukryć developerą pewne infroacje, gdy pliki txt działajaą jak open source vs zamknięte formaty binarne, w których można ukrywać infrmację o użytkownikach
* plik tekstowy i jednolite narzędzia dla tysiąca różnych programów
* TODO: inode vs vnode
* istnieje demon udev któy odpowiada za tworzenie 
* jedno wielkie drzewo i punkty montażowe
  

## types of communicatoion btw prcoess in linux

* files
* pipes
* sockets
* ipc
* rpc 
* D-bus jest połączony z udevem, który dostaje informacje od udeva

## file systems

procfs - konifuracja procesow i jądra
sysfs - konfiguracja urząrzeń
udevfs - urządzenia jako pliki

ipv4 często ma dobrego firewalla ipv6 nie jest


## file system hierarchy
nie idealny z barokową architekturą, ale ludzie sie przyzwyczaili  wiec ze wzgledu na wsteczna kompatybilnosśc

/etc/ - miało być tam gdzie nic innego nie pasuje, ale trzyma się tu pliki konfiguracyjne

(etcetera)
/usr - debian zabronił wrzucenia na inną partycje ze względu na mnogość zależności



zfs co to?


/usr

nfs - network file system


three levels of hierarchy:
root - musi mieć zawsze homa nawt gdy home nie jest potępieety dlatego musi być na rootfs

bin - dla użytkowanika
sbin - dla roota

lib - istatnne biblioteki współdzilone

opt - oprogramowanie opcjonalne, nie jest czescia sytemu operacyjny

media - punkty montżowe urządznń wymiennych

/usr - czesc stała plikow systemowych - moduły kerne;a

var/tmp nie był czyszczony w pracowni 109 a w tamtymi miejscu była zapisowna odpowiednio przesalowana tapeta

.**prog**rc - plik konfiguracyjny dla programu `prog`




