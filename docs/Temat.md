# Wybór tematu
### Psinder - Tinder dla jamników
Psinder to aplikacja mobilna bazująca na popularnej koncepcji zapoczątkowanej przez aplikacje Tinder. Grupą docelową aplikacji są ludzie szukających jamników do adopcji, bądź jamniki szukające innych jamników. Aplikacja oparta będzie o zestaw mikroserwisów komunikujących się ze sobą jak i z aplikacją ze pomocą API. Interfejs aplikacji będzie oparty o przesuwane karty. System będzie posiadał konta użytkowników wraz z możliwym do wykupienia statusem premium umożliwiającym przeglądanie jamników bez limitów. Płatności będą realizowane wewnątrz aplikacji.

![](https://i.imgur.com/eCLlyay.png)

## Technologia

### Backend
Backend zaimplementowany zostanie przy użyciu Spring Cloud i Spring Boot. Za język programowania posłuży Java.

### Baza danych
Dla każdego mikroserwisu uruchomiona będzie osobna, dedykowana baza danych PostgreSQL.

### ORM 
Do realizacji warstwy dostępu do danych posłuży Hibernate. Jest to Javowy framework, ktory pozwala na mapowanie obiektowo-relacyjne.

#### Mikroserwisy
Backend podzielony będzie na kilka mikroserwisów pełniących odrębne, ale uzupełniające się funkcje.

Planowany wstępny podział:
* Mikroserwis do osbsługi płatności,
* Mikroserwis do autoryzacji i autentykacji,
* Mikroserwis do obsługi kart,
* Mikroserwis do obsługi użytkowników,
* Mikroserwis do obsługi map.

#### Serwer
Aplikacja będzie hostowana na dedykowanym serwerze opartym o system operacyjny Linux o co najmniej wymienionych parametrach:
* System operacyjny Linux wspierający platformę Docker w wersji 17+,
* Dwurdzeniowy procesor o architekturze x86_64 i taktowaniu co najmniej 2.0 GHz,
* 2 GB pamięci operacyjnej RAM,
* 10 GB wolnego miejsca na dysku,
  * Preferowany jest dysk SSD.

Aplikacja będzie korzystała z konteneryzacji za pomoca platformy Docker. Każdy mikroserwis będzie skonteneryzowany i niezależny od reszty. Do bazowego obrazu będą zaliczały się następujące komponenty:
* Baza oparta na systemie Ubuntu Cloud bądź Alpine,
* Reguły komunikacji ze światem zewnętrznym,
* System zarządzania bazą danych PostgreSQL,
* Bazę danych stworzoną z domyślnego schematu,
* Skompilowany mikroserwis,
* Serwer Tomcat.

Tak opisane obrazy powstaną dla każdego mikroserwisu. Taki podział umożliwia teoretyczny podział mikroserwisów na różne serwery. W miarę możliwości wdrożony zostanie również system continuous integration and deployment

### Frontend
Za aplikację kliencką systemu posłuży aplikacja mobilna na wiodące platformy mobilne. Aplikacja będzie łączyć się z backendem za pomocą REST API. Dzięki wykorzystanej technologii możliwe będzie rozszerzenie aplikacji również na platformę webową.

Wybór formy frontendu jako aplikacji mobilnej jest podyktowany zaplanowaną formą systemu przeznaczoną głównie dla użytkowników mobilnych.

* Technologia
  * Flutter
* Platformy
  * iOS
  * Android
  * Web (potencjalnie w przyszłości)
* Architektura
  * Bloc
* Język programowania
  * Dart
    * Logika biznesowa
    * Interfejs użytkownika
    * Komunikacja z backendem
  * Swift
    * Fragmenty kodu natywnego integrujące z platformą iOS
  * Kotlin
    * Fragmenty kodu natywnego integrujące z platformą Android
    
### Integracja z systemami zewnętrznymi
System komunikować się będzie z dwoma zewnętrznymi serwisami - PayU w celu obsługi płatności oraz Google Maps Platform do obsługi geolokacji i nawigacji.

#### PayU
PayU jest firmą oferującą system do obsługi płatności internetowych dla osób posiadających adres e-mail. Posiada dwie możliwości płacenia - kartą kredytową oraz przelewem bankowym. PayU posiada testowy system do płatności nazywany Sandbox, który posiada wszystkie potrzebne nam funkcjonalności:
* Apple Pay,
* BLIK, 
* Przelew tradycyjny,
* PayU|Mobile,
* Wypłaty,
* Zwroty.

#### Google Maps Platform
Google Maps Platform jest platformą firmy Google, która pozwala na integrację aplikacji z mapami i usługami lokalizacyjnymi. W aplikacji Psinder użyte zostaną trzy komponenty:
* Maps,
* Routes,
* Places.
