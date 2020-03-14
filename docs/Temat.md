# Wybór tematu
### Psinder - Tinder dla jamników
Psinder to aplikacja mobilna bazująca na popularnej koncepcji zapoczątkowanej przez aplikacje Tinder. Grupą docelową aplikacji są ludzie szukających jamników do adopcji, bądź jamniki szukające innych jamników. Aplikacja oparta będzie o zestaw mikroserwisów komunikujących się ze sobą jak i z aplikacją ze pomocą API. Interfejs aplikacji będzie oparty o przesuwane karty. System będzie posiadał konta użytkowników wraz z możliwym do wykupienia statusem premium umożliwiającym przeglądanie jamników bez limitów. Płatności będą realizowane wewnątrz aplikacji.

## Technologia

### Backend
Backend zaimplementowany zostanie przy użyciu Spring Cloud i Spring Boot. Za język programowania posłuży Java.

### Baza danych
Dla każdego mikroserwisu uruchomiona będzie osobna, dedykowana baza danych PostgreSQL.

### ORM 
Do realizacji warstwy dostępu do danych posłuży Hibernate. Jest to Javowy framework, ktory pozwala na mapowanie obiektowo-relacyjne.

#### Mikroserwisy
Backend podzielony będzie na kilka mikroserwisów pełniących odrębne, ale uzupełniające się funkcje.
Planowane mikroserwisy:
* Mikroserwis do osbsługi płatności
* Mikroserwis do autoryzacji i autentykacji
* Mikroserwis do obsługi kart
* Mikroserwis do obsługi użytkowników
* Mikroserwis do obsługi map


#### Serwer

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

#### PayU

#### Google Maps
