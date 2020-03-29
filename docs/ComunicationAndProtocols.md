# Komunikacja z klientem
Klientem aplikacji jest aplikacja mobilna na system Android oraz iOS. Klient porozumiewa się z aplikacją za pomocą komunikacji REST korzystając z protokołu HTTP oraz portu 80. Używa jej do otrzymywania danych przy pomocy Zuul Gateway. Zuul Gateway jest serwisem pozwalającym na routing zapytań HTTP. Dba również o bezpieczeństwo oraz monitorowanie ruchu.    
# Komunikacja między serwisami
Serwisy działające w aplikacji rejestrują się w systemie identyfikacji serwisów - Eurece. Zuul Gateway odpytuje Eurekę o dane niezbędne do komunikacji z serwisami - takie jak IP oraz port. Następnie brama komunikuje się za pomocą komunikacji REST  korzystając z protokołu HTTP oraz portu 80 z odpowiednimi serwisami. Każdy z serwisów jest odpowiedzialny za możliwie małą funkcjonalność i posiada możliwie jak najbardziej ograniczony dostęp do bazy danych.

<img src="https://exampledriven.files.wordpress.com/2016/07/zuul-api-gateway.jpg?w=561" />
