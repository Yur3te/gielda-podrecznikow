# Architektura systemu i stos technologiczny

## 1. Architektura systemu
System został zaprojektowany w architekturze trójwarstwowej **Client-Server** z wyraźnym podziałem na niezależną warstwę prezentacji (Frontend), warstwę logiki biznesowej (Backend REST API) oraz warstwę przechowywania danych (relacyjna baza danych oraz magazyn plików graficznych).

Całość środowiska uruchomieniowego jest skonteneryzowana przy użyciu narzędzia **Docker**, co gwarantuje identyczne środowisko pracy dla każdego członka zespołu oraz ułatwia automatyzację testów i wdrożeń w potoku CI/CD (GitHub Actions).

### Główne komponenty:
1. **Aplikacja kliencka (SPA):** Interfejs użytkownika zbudowany w czystym React, uruchamiany w przeglądarce internetowej. Komunikuje się z serwerem wyłącznie za pomocą zapytań HTTP/HTTPS (JSON).
2. **Serwer aplikacji (REST API):** Aplikacja napisana w Pythonie (FastAPI), odpowiadająca za uwierzytelnianie (JWT), walidację danych, obsługę logiki biznesowej (zarządzanie ofertami, rezerwacjami i moderacją) oraz zapis przesyłanych zdjęć.
3. **Baza danych:** Relacyjna baza danych PostgreSQL przechowująca informacje o użytkownikach, ogłoszeniach, kategoriach przedmiotów oraz wiadomościach.
4. **Magazyn plików (Local File Storage):** Wydzielony wolumen dyskowy kontenera (Docker Volume) przechowujący zdjęcia okładek podręczników przesyłane przez użytkowników, serwowane jako pliki statyczne przez API.

*(Diagram architektury znajduje się w pliku `docs/diagrams/architektura.png`)*

---

## 2. Stos technologiczny i uzasadnienie

| Warstwa | Technologia | Uzasadnienie wyboru |
| :--- | :--- | :--- |
| **Frontend** | **React + Vite + Tailwind CSS** | Czysty React zapewnia komponentową budowę interfejsu. Vite gwarantuje błyskawiczne budowanie aplikacji i środowisko deweloperskie, a Tailwind CSS pozwala na szybkie stylowanie widoków bez konieczności utrzymywania rozbudowanych arkuszy stylów. |
| **Backend** | **Python + FastAPI** | Lekki i wydajny framework z automatyczną walidacją danych (Pydantic) i generowaną dokumentacją OpenAPI/Swagger. Pozwala na czytelną implementację wzorców projektowych (m.in. Strategy, Factory, Repository) oraz proste pisanie testów jednostkowych w `pytest` (TDD). |
| **Baza danych** | **PostgreSQL** | Sprawdzona, darmowa relacyjna baza danych zapewniająca spójność transakcyjną (ACID) przy rezerwacji podręczników oraz wygodne filtrowanie zapytań. |
| **Magazyn plików** | **Lokalny wolumen (Docker Volume)** | Umożliwia trwałe przechowywanie zdjęć okładek podręczników bez uzależniania projektu od płatnych usług chmurowych (np. AWS S3) i dodatkowych kluczy dostępowych. |
| **Konteneryzacja** | **Docker + Docker Compose** | Pozwala na uruchomienie całej aplikacji (Frontend, Backend, Baza danych) jedną komendą, eliminując problemy z różnicami w konfiguracji lokalnych środowisk zespołu. |
| **CI/CD** | **GitHub Actions** | Natywna integracja z repozytorium GitHub umożliwia automatyczne uruchamianie testów jednostkowych (`pytest`) oraz weryfikację budowania obrazów Dockerowych przy każdym Pull Requeście. |