# http

* zaprojektowany do przesyłania html
* obecnie równierz do przesyłania olbrzymich danych


### URL
* identyfikuje dan zasób
* postać: `protokół:część-zależna-od-protokołu`


## http 1.0
* każde zapytanie http w osobnym połączeniu tcp
* domyslnie polaczenie tcp jest zamykana po otrzymaniu odpowiedzi
## http 1.1
* połączenia domyślnie otwarte 
* a zatem tcp moze sie rozpedzic
>[!NOTE]
> `if modified since` client header option. przeglądarka cachuje pewne infomacje (np. zdjęcia) jeżeli nie zmieniły się od tego czasu a klient znów o nie poprosi to odesle 304 not modified
> `expires` - header servera - client nie bedzie ponownie pytal sie o zosób do pewnego czasu
> `Cache-Control: no-cache` - po stronie servera  - nie ma sesnu trzymać w pamięci podręcznej 

## co robią servery proxy?
* wykorzystywane przez ISP (internet sdetrvice provider) w celu cachowania dla wszystkich
* wykorzystywane przez CDN (condent delivery network), żeby np FAME MMA nie musiało kupować serverów proxy tylko mogły je wynając na dzien gali
* dodaje dodatkowe pola do żądania HTTP
* `X-Forwarded-For: <client>, <proxy1>, <proxy2>`

> [!NOTE]
> obecnie http jest również wykorzystywany podczas wysyłania wideo
> np DASH (dynamic adaptive streaming over HTTP)


## http/2
* binarne kodowanie tcp
* server push
* obowiazkowe szyforwanie

# http/3
* http over QUIC ( nie trzeba czekać na głupstwa TCP )

> [!NOTE]
> TCP działa w jądrze, quiq w przestrzeni użytkownika