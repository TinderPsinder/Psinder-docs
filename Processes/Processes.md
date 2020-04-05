# Model procesów biznesowych

## Aktorzy i charakterystyka użytkowników

**ID:** AKT_ADM  
**Nazwa:** Administrator
**Opis:** Administrator systemu jest osobą posiadającą kwalifikacje wymagane do zarządzania systemem informatycznym. Ma możliwość zarządzania kontami użytkowników. Może dokonywać modyfikacji systemu takich jak wprowadzanie przerwy technicznej czy modyfikację profilu panelu płatności.  

**ID:** AKT_JAM  
**Nazwa:** Użytkownik (Jamnik)  
**Opis:** Administrator systemu jest osobą posiadającą kwalifikacje wymagane do zarządzania systemem informatycznym. Ma możliwość zarządzania kontami użytkowników. Może dokonywać modyfikacji systemu takich jak wprowadzanie przerwy technicznej czy modyfikację profilu panelu płatności.

## Słownik biznesowy

#### Profil użytkownika
Zbiór informacji o użytkowniku. Zawiera dane użytkownika, takie jak imię, wiek oraz płeć. Dodatkowo w profilu znajdują się wgrane zdjęcia użytkownika oraz jego połączone profile ze stron takich jak Instagram czy Tinder.

#### Polubienie
Wyrażenie zainteresowania drugim użytkownikiem przez pierwszego użytkownika.

#### Match (para)
Match to połączenie pomiędzy dwoma użytkownikami. Następuje wtedy, gdy obaj użytkownicy wyrażą swoje zainteresowanie sobą poprzez polubienie swoich profili.

#### Czat
Czat to zbiór wiadomości wymienianych pomiędzy dwoma użytkownikami. Aby użytkownicy mogli czatować niezbędny jest match pomiędzy nimi.

#### Limit polubień
Każdy z użytkowników posiada ograniczoną liczbę polubień którą może w wykorzystać w ciągu jednego dnia. Po osiągnięciu limitu nie może dalej lubić profili użytkowników. Może za to skorzystać z czatu z użytkownikami, z którymi osiągnął match.

#### Konto premium
Premium to ulepszenie konta zwykłego polegające na zniesieniu limitu polubień oraz możliwość zobaczenia profili które dodały polubienia do właściciela konta premium.

### Ban
Ban wiąże się z usunięciem konta użytkownika, wylogowaniem go z aplikacji oraz brakiem możliwości założenia konta na podanego maila w przyszłości.

### Nieodpowiednie zachowanie
Są to działania, które są niezgodne z regulaminem użytkowania aplikacji. Takie jak np. wrzucanie niecenzuralnych zdjęć, używanie wulgaryzmów czy podszywanie się pod kogoś innego.

## Procesy biznesowe
### Użytkownicy dopasowują się (match)
**Aktorzy:** Dwaj użytkownicy  
**Opis**: Użytkownik znajduje dopasowanie z drugim użytkownikiem  
**Warunki początkowe:** Obaj użytkownicy mają założone konto w serwisie. Drugi użytkownik polubił wcześniej profil użytkownika pierwszego. Użytkownicy znajdują się w tej samej lokalizacji.  
**Scenariusz główny:**  
1. Użytkownik otwiera ekran główny.
2. Użytkownik natrafia na drugiego użytkownika.
3. Użytkownik zaznacza polubienie konta drugiego użytkownika
4. Użytkownik jest dopasowany z drugim użytkownikiem (match)

**Scenariusz alternatywny:** 
A3. Użytkownik nie zaznacza polubienia drugiego użytkownika
A4. Użytkownik nie jest dopasowany z drugim użytkownikiem

### Użytkownik wysyła wiadomość do drugiego użytkownika 
**Aktorzy:** Dwaj użytkownicy  
**Opis**: Użytkownik przy pomocy czatu wysyła wiadomość do drugiego użytkownika, z którym uzyskał Match.  
**Warunki początkowe:** Obaj użytkownicy mają założone konto w serwisie. Pierwszy użytkownik polubił wcześniej profil drugiego użytkownika, a drugi pierwszego.  
**Scenariusz główny:**  
1. Użytkownik otwiera zakładkę ze swoimi dopasowaniami (matchami)
2. Użytkownik wybiera drugiego użytkownika na liście dostępnych dopasowań.
3. Użytkownik wysyła wiadomość.

**Scenariusz alternatywny:**  brak

### Użytkownik kupuje konto premium
**Aktorzy:** Użytkownik  
**Opis**: Użytkownik kupuje kupuje konto premium w aplikacji.    
**Warunki początkowe:** Użytkownik ma założone konto w serwisie.  
**Scenariusz główny:**  
1. Użytkownik otwiera zakładkę dotyczącą konta premium
2. Użytkownik przechodzi do płatności PayU
3. Użytkownik potwierdza płatność
4. Użytkownik otrzymuje konto premium.

**Scenariusz alternatywny:**  
A3. Płatność nie przechodzi  
A4. Użytkownik widzi komunikat o błędzie

### Użytkownik zgłasza drugiego użytkownika
**Aktorzy:** Użytkownik  
**Opis**: Użytkownik zgłasza drugiego użytkownika, po zauważeniu jego niewłaściwego zachowania  
**Warunki początkowe:** Użytkownik ma założone konto w serwisie. Drugi użytkownik też ma założone konto oraz zachował się w sposób niezgodny z zasadami (np. niewłaciwy wiek).  
**Scenariusz główny:**  
1. Użytkownik otwiera profil drugiego użytkownika
2. Użytkownik klika przycisk zgłoś.
3. Drugi użytkownik zostaje zgłoszony

**Scenariusz alternatywny:** brak

### Administrator blokuje konto krnąbrnego użytkownika
**Aktorzy:** Użytkownik  
**Opis**: Administrator usuwa konto krnąbrnego użytkownika oraz blokuje dalsze zakładanie konta  
**Warunki początkowe:** Użytkownik ma założone konto w serwisie i był krnąbrny  
**Scenariusz główny:**  
1. Administrator otwiera panel administratora
2. Administrator nakłada blokadę na użytkownika

**Scenariusz alternatywny:** brak
