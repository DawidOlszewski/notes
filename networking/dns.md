# DNS
### Po co?
* rozproszone zarządzanie nazwami domen oraz ich propagacją


strefa 

włascicel strefy dNS 

### strefa główna (.) i serwery
* serwerów zarządzających strefą główną jest 13 i ich adresy ip bardzo rzadko się zmieniją

* wie kto zarządza strefą `.pl`


> [!NOTE]
> typy adresów ip:
> `unicast` - weysła jedna osoba do drugiej
> `broadcast` - jedna osoba wysła do wszystkich
> `multicast` - wysyłamy coś do jakiejś podgruy serverów
> `anycast` - czyli wiele serwerów ma ten sam adress ip

> [!WARNING]
> istnieje szansa ze podczas zmiany pozycji (np. korzystania z telefonu w samochodzie) zmieni się najbliższy server `anycastowy`. Zatem podczas korzystania z protokołu stanowego możemy bezporotnie stracić bierzącą sesję. Wniosek: adresy `anycastowe` nadają się wyłącznie do komunikacji bezstanowej.


## sposoby korzystania z DNS

* resolving iteracyjny - z placa
* resolving rekurencyjny - wysyłamy zapytanie do resolvera dns który wykona za nas pracę iteracyjnie
  np pytając `8.8.8.8` o pewną domenę odrazu dostaniemy odpowiedź

> [!NOTE]
> wpisując w komputerze inforacje o serverze dns - podajemy adress ip resolvera dns (który jest odpowiedzilany za odpowiadanie na takie zapytania)


### Rekordy DNS:
* `A` - nazwa domney ipv4
* `AAAA` - nazwa domeny ipv6 (4*dłuższe niż `A`)
* `NS` - ip nameservera daną strefę (`rekordem sklającym` nazywa się rekord który poza `ns` zawiera jeszcze jego address (`A`), w np TLD)
* `CNAME` - alias
* `MX` - kto obsługuję pocztę dla danej domny
* `PTR` - reverse dns

> [!NOTE]
> `CNAME` jest przydatny gdy mamy wiele usług na jednym serwerze i zeminiając adres ip wtedy wyttarczy zmienic tylko jedne `A`





