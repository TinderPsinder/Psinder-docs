# Architektura aplikacji z użyciem mikroserwisów
<img src="https://i.imgur.com/anfORKF.png" />

# Komunikacja z klientem
Klientem aplikacji jest aplikacja mobilna na system Android oraz iOS. Klient porozumiewa się z serwerem aplikacji za pomocą komunikacji REST korzystając z protokołu HTTP oraz portu 80. Zapytania klienta są przetwrzane przez serwer przy użyciu Zuul Gateway.

## Zuul Gateway
Zuul jest implementacją wzorca API Gateway stworzoną przez firmę Netflix. Dzięki zastosowaniu tego wzorca klient aplikacji będzie komunikował się wyłącznie z jednym endpointem. To pozwala na odpowiednie zabezpieczenie endpointa, bo jest jedynym wejściem do systemu (np. przez Basic Auth czy usługę CloudFlare). W aplikacji Psinder Hulu będzie odpowiedzialne za routing, czyli zarządzanie zamienianiem zapytań HTTP na dane możliwe do przetworzenia przez aplikację. Odpowiednie adresy URL (Uri) będą odpowiadać za konretne akcje po stronie systemu. W przypadku gdy w projekcie będzie potrzeba przetestowania nowych serwisów, Hulu może przekierować testowy ruch (np. alpha) na nowe serwisy. Hulu jest też odpowiedzialne za monitorowanie ruchu, co pozwoli na ewentualną analizę i zmiany w architekturze. Dzięki integracji Hulu z Eurteką, Hulu nie posiada informacji na temat serwisów, a za wiedza na temat serwisów jest odpowiedzialnością  Eureki. 

# Komunikacja między serwisami
Serwisy działające w aplikacji rejestrują się w systemie identyfikacji serwisów - Eurece. Zuul Gateway odpytuje Eurekę o dane niezbędne do komunikacji z serwisami - takie jak IP oraz port. Następnie brama komunikuje się za pomocą komunikacji REST  korzystając z protokołu HTTP oraz portu 80 z odpowiednimi serwisami. Każdy z serwisów jest odpowiedzialny za możliwie małą funkcjonalność i posiada swoją bazę danych. Serwisy mogą się komunikowac między sobą przy pomocy zapytań REST. O dane niezbędne do komunikacji również odpytują Eurekę.

## Eureka
Eureka jest narządziem odkrywania serwisów (ang. _service discovery_), które pozwala na wyizolowanie informacji na temat danych serwisów. Dzięki temu Gateway, ani żaden z serwisów nie posiada wiedzy na temat innych serwisów. Dzięki zastosowania mechanizmu rejestrowania, zmiany w systemie mogą być wprowadzane dynamiczne, a co najważniejsze dokonywane bez aktualizacji kodu w poszczególnych, wcześniej stworzonych serwisów.
