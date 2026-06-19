# Projekt: Menedżer Wizyt (Vite + React + TypeScript)

Krótki opis
---
To jest prosty frontendowy projekt zbudowany z użyciem Vite, React i TypeScript, służący do zarządzania wizytami lekarskimi. Aplikacja zawiera strony takie jak dashboard, lista lekarzy, lista usług oraz moduł dodawania i przeglądania terminów.

Wymagania
---
- Node.js 16+ (zalecane 18+)
- npm lub pnpm / yarn
- Połączenie z internetem do pobrania zależności

Instalacja
---
1. Sklonuj repozytorium lub pobierz pliki projektu.
2. W katalogu projektu uruchom instalację zależności:

```bash
npm install
# lub
pnpm install
# lub
yarn
```

Uruchomienie (deweloperskie)
---
- Uruchom serwer deweloperski:

```bash
npm run dev
# lub pnpm run dev
```

- Otwórz w przeglądarce pod adresem podanym przez Vite (domyślnie http://localhost:5173).

Budowanie i podgląd produkcyjny
---
- Zbuduj aplikację:

```bash
npm run build
```

- Podejrzyj wynik produkcyjny:

```bash
npm run preview
```

Główne funkcjonalności
---
- Dashboard: podsumowanie statystyk i szybkiego dostępu do sekcji.
- Lista wizyt: przegląd wszystkich terminów (komponenty i hooki w `src/hooks` i `src/data`).
- Dodawanie nowej wizyty: formularz tworzenia terminu (strona `NewAppointment`).
- Zarządzanie lekarzami: lista i karty lekarzy (`DoctorCard`, `Doctors` page).
- Zarządzanie usługami: lista i karty usług (`ServiceCard`, `Services` page).
- Komponenty interfejsu: karty statystyk (`StatCard`) i menedżer wizyt (`AppointmentManager`).
- Proste przechowywanie danych: plik `src/services/storageService.ts` do lokalnej persystencji (LocalStorage).

Struktura projektu (wybrane pliki)
---
- `src/` – kod źródłowy aplikacji
  - `main.tsx` – punkt wejścia
  - `App.tsx` – główny komponent aplikacji
  - `components/` – komponenty UI (`AppointmentManager.tsx`, `DoctorCard.tsx`, `ServiceCard.tsx`, `StatCard.tsx`)
  - `pages/` – strony aplikacji (`Appointments.tsx`, `Dashboard.tsx`, `Doctors.tsx`, `NewAppointment.tsx`, `Services.tsx`)
  - `data/` – przykładowe dane (`appointments.ts`, `doctors.ts`, `services.ts`)
  - `services/` – serwisy pomocnicze (`storageService.ts`)
  - `hooks/` – hooki React (`useAppointments.ts`)

Uwagi dodatkowe
---
- Brak testów automatycznych w repozytorium (jeśli chcesz, mogę dodać podstawowe testy jednostkowe).
- Dostosuj wersję Node w zależności od środowiska CI/CD.

Kontakt / Kolejne kroki
---
Jeśli chcesz, mogę:
- dodać sekcję z przykładami API lub mockami,
- napisać skrypt seedujący przykładowe dane,
- dodać konfigurację CI (GitHub Actions) do automatycznego budowania.
