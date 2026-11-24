# Kontekst projektu – Giełda używanych podręczników

## 1. Wizja i cel systemu
System **Giełda używanych podręczników** to aplikacja webowa dedykowana społeczności akademickiej, umożliwiająca studentom szybkie wystawianie, wyszukiwanie oraz bezpośredni zakup używanych materiałów dydaktycznych.

Głównym celem systemu jest uproszczenie obiegu książek między rocznikami na uczelni bez konieczności angażowania zewnętrznych platform sprzedażowych, prowizji oraz przesyłek kurierskich. Transakcje odbywają się w modelu bezpośrednim (odbiór osobisty na terenie kampusu po wcześniejszym kontakcie przez system).

## 2. Zakres systemu
* Zarządzanie kontami użytkowników (rejestracja i logowanie studentów).
* Publikacja, edycja i archiwizacja ogłoszeń sprzedaży podręczników (wraz ze zdjęciem, ceną, stanem zużycia oraz przypisaniem do kierunku i przedmiotu).
* Wyszukiwarka z filtrowaniem po nazwie przedmiotu, kierunku studiów, roku oraz cenie.
* Moduł rezerwacji i wymiany wiadomości między kupującym a sprzedającym w celu ustalenia szczegółów odbioru.
* Panel administracyjny do moderacji zgłoszonych ogłoszeń oraz zarządzania słownikiem kierunków i przedmiotów.

## 3. Lista aktorów

| Aktor | Opis roli w systemie |
| :--- | :--- |
| **Niezalogowany użytkownik (Gość)** | Może przeglądać katalog dostępnych podręczników, korzystać z wyszukiwarki i filtrów oraz założyć konto w systemie. Nie ma możliwości dodawania ogłoszeń ani kontaktu ze sprzedającymi. |
| **Student (Zalogowany użytkownik)** | Główny aktor systemu. Może pełnić rolę **Sprzedającego** (wystawia, edytuje i zamyka własne ogłoszenia) oraz **Kupującego** (rezerwuje podręczniki, kontaktuje się ze sprzedającymi, zgłasza nieodpowiednie oferty). |
| **Administrator** | Odpowiada za utrzymanie porządku w systemie. Moderuje zgłoszone ogłoszenia (ma prawo je ukryć lub usunąć), zarządza kontami użytkowników oraz aktualizuje listę kierunków studiów i przedmiotów. |