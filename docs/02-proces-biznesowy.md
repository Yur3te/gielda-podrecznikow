\#Opis głównego procesu biznesowego

\## 1.Co tu jest i jak to działa
W tym pliku jest opisany główny proces naszej aplikacji "Giełda używanych podręczników", czyli co się dzieje po kolei od momentu jak ktoś wejdzie na stronę, doda ogłoszenie, aż ktoś inny tę książkę kupi ,albo coś pójdzie nie tak.



Diagram zrobiliśmy w BPMN 2.0 w draw.io. Jest podzielony na 5 torów, żeby było wiadomo kto co robi:
\*\*Niezalogowany użytkownik \*\* – przegląda stronę i zakłada konto na maila z uczelni (hasło min. 8 znaków).
\*\*Sprzedający\*\* – wrzuca ogłoszenie, spotyka się na przekazanie książki i klika, że sprzedane.
\*\*System\*\* – sprawdza czy wszystko w formularzu jest wpisane, zmienia statusy książki 'Dostępne', 'Zarezerwowane', 'Sprzedane', pilnuje żeby rezerwacja nie wisiała dłużej niż 50h i zapisuje historię.
\*\*Kupujący\*\* – szuka książki, rezerwuje ją, odbiera na żywo i płaci gotówką.
\*\*Administrator\*\* – ogarnia zgłoszenia i ukrywa jakieś dziwne albo błędne ogłoszenia.

\## 2. Diagram BPMN 2.0

!\[Model głównego procesu biznesowego – BPMN 2.0](diagrams/proces-bpmn.png)

\*Plik źródłowy diagramu: \[`diagrams/proces-bpmn.drawio`](diagrams/proces-bpmn.drawio)

\## 3. Jak idzie główna ścieżka (krok po kroku)

1. \*\*Rejestracja i logowanie:\*\* Ktoś bez konta zakłada je na maila i się loguje.

2\. \*\*Dodanie ogłoszenia:\*\* Sprzedający wypełnia formularz – musi podać tytuł, autora, przedmiot, stan książki i cenę (opis może sobie darować, bo nie jest obowiązkowy).

3\. \*\*Sprawdzenie i wrzucenie:\*\* System patrzy czy są wszystkie obowiązkowe pola. Jak są, to zapisuje ze statusem 'Dostępne' i ogłoszenie widać w wyszukiwarce.

4\. \*\*Szukanie i rezerwacja:\*\* Kupujący wpisuje w wyszukiwarkę tytuł, autora albo przedmiot, znajduje książkę i klika rezerwację.

5\. \*\*Zmiana statusu:\*\* System upewnia się, że książka dalej ma status 'Dostępne' i zmienia go na 'Zarezerwowane'.

6\. \*\*Odbiór i kasa:\*\* Kupujący spotyka się ze Sprzedającym, bierze podręcznik i daje gotówkę .

7\. \*\*Potwierdzenie sprzedaży:\*\* Sprzedający klika przycisk 'Sprzedane' ten przycisk widzi tylko on, nikt inny.

8\. \*\*Koniec:\*\* System ustawia status na 'Sprzedane', usuwa ogłoszenie z wyszukiwarki i zostawia je w historii u kupującego i sprzedającego.

\## 4.Bramki decyzyjne i wyjątki

|Bramka na diagramie|Jak jest OK|Wyjątek|
|-|-|-|
|Czy podano wszystkie wymagane pola?  |System wrzuca ogłoszenie na stronę ze statusem 'Dostępne'.| Czegoś brakuje – System daje komunikat czego nie ma i nic nie zapisuje.|
|Czy status książki to 'Dostępne'? |System blokuje książkę i ustawia status 'Zarezerwowane'.| Ktoś ją już wcześniej zarezerwował albo kupił – wyskakuje błąd rezerwacji i koniec.|
|Przebieg rezerwacji limit 50h | Dochodzi do spotkania, zapłaty gotówką i Sprzedający klika 'Sprzedane'.|Minęło 50 godzin i nikt tego nie potwierdził albo Kupujący się rozmyślił – książka wraca do statusu<br />'Dostępne'. Sprzedający sam usunął ogłoszenie albo Admin je ukrył po zgłoszeniu – ogłoszenie znika i proces się kończy.|



