# Wymagania

## Aktorzy

- Niezalogowany użytkownik - przegląda strone i może założyć konto
- Student (zalogowany użytkownik) - sprzedający lub kupujący
- Administrator - zajmuje się stroną

## Priorytety MoSCoW

- Must - musi być
- Should - powinno być
- Could - może być
- Won't - nie będzie w tej wersji

## User Stories, czyli wymagania funkcjonalne

### 1 - Rejestracja i logowanie
Jako student chcę założyć konto i móc się zalogować

Priorytet: Must

Kryteria akceptacji:
- można się zarejestrować tylko mailem uczelnianym
- hasło musi mieć co najmniej 8 znaków
- przy złym haśle pokazuje się komunikat o błędzie

### 2 - Dodanie ogłoszenia
Jako sprzedający chcę dodać ogłoszenie z podręcznikiem, aby ktoś mógł go ode mnie kupić

Priorytet: Must

Kryteria akceptacji:
- trzeba podać tytuł, autora, przedmiot, stan książki i cenę
- opis nie jest obowiązkowy
- jak czegoś brakuje, ogłoszenie się nie zapisze, pokaże się, czego brakuje
- nowe ogłoszenie ma status "Dostępne" i widać je w wyszukiwarce

### 3 - Wyszukiwanie podręcznika
Jako kupujący chcę wyszukać podręcznik po tytule, autorze albo nazwie przedmiotu, aby szybko znaleźć potrzebną książkę

Priorytet: Must

Kryteria akceptacji:
- wystarczy wpisać fragment tytułu, autora albo przedmiotu
- wielkość liter nie ma znaczenia
- jak nic nie ma, pokazuje się napis "Brak ogłoszeń"

### 4 - Rezerwacja podręcznika
Jako kupujący chcę zarezerwować podręcznik, aby mieć pewność, że będzie dostępny

Priorytet: Must

Kryteria akceptacji:
- można zarezerwować tylko książkę ze statusem "Dostępne"
- po rezerwacji status zmienia się na "Zarezerwowane"
- jeśli książka jest już zarezerwowana albo sprzedana, rezerwacja się nie uda

### 5 - Anulowanie rezerwacji
Jako sprzedający chcę, żeby rezerwacja sama wygasała, aby moja książka nie była zablokowana na zawsze

Priorytet: Must

Kryteria akceptacji:
- jeśli rezerwacja nie zostanie potwierdzona w ciągu 50 godzin, książka wraca do statusu "Dostępne"
- kupujący może sam zrezygnować z rezerwacji

### 6 - Potwierdzenie sprzedaży
Jako sprzedający chcę oznaczyć książkę jako sprzedaną, aby zakończyć transakcję

Priorytet: Must

Kryteria akceptacji:
- przycisk "Sprzedane" widzi tylko sprzedający
- sprzedana książka znika z wyszukiwarki
- sprzedana książka zostaje w historii kupującego i sprzedającego

### 7 - Edycja i usuwanie ogłoszenia
Jako sprzedający chcę edytować albo usunąć swoje ogłoszenie, aby zmienić cenę albo wycofać książkę

Priorytet: Must

Kryteria akceptacji:
- edytować i usuwać może tylko autor ogłoszenia albo administrator
- sprzedanego ogłoszenia nie da się już edytować

### 8 - Moderacja
Jako administrator chcę ukrywać niepoprawne ogłoszenia i blokować użytkowników, aby strona działała jak należy

Priorytet: Should

Kryteria akceptacji:
- administrator widzi listę zgłoszonych ogłoszeń
- może ukryć albo przywrócić ogłoszenie
- zablokowany użytkownik nie może się zalogować, dopóki nie zostanie odblokowany

### 9 - Ulubione ogłoszenia
Jako kupujący chcę dodać ogłoszenie do ulubionych, aby łatwo do niego wrócić

Priorytet: Could

Kryteria akceptacji:
- przy każdym ogłoszeniu jest przycisk "Dodaj do ulubionych"
- ulubione ogłoszenia widać w osobnej zakładce na profilu

### 10 - Płatność online
Jako kupujący chcę zapłacić przez stronę, aby nie płacić gotówką

Priorytet: Won't

Płatności online to zbyt zaawansowana technologia na poziom tego projektu

## Wymagania niefunkcjonalne

- wydajność - wyszukiwanie ma działać w mniej niż 2 sekundy przy 200 użytkownikach naraz
- bezpieczeństwo - hasła są zapisane w bazie jako hash, a nie zwykłym tekstem
- bezpieczeństwo - strona działa przez HTTPS
- responsywność - strona działa na telefonie i na komputerze
- dostępność - strona działa przez co najmniej 99% czasu w miesiącu
