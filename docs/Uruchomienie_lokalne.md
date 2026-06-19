# Uruchomienie lokalne — Szybki start

Poniższe kroki pomogą nowemu programiście uruchomić projekt lokalnie.

**Wymagania**
- Node.js 16+ (zalecane 18+)
- `npm`, `pnpm` lub `yarn`
- Połączenie z internetem do pobrania zależności

**Szybki start**
1. Sklonuj repozytorium lub pobierz pliki projektu i przejdź do katalogu projektu:

```bash
git clone <repo_url>
cd projekt
```

2. Zainstaluj zależności (wybierz menedżera pakietów):

```bash
npm install
# lub
pnpm install
# lub
yarn
```

3. Uruchom serwer deweloperski:

```bash
npm run dev
# lub pnpm run dev
```

Otwórz przeglądarkę pod adresem podanym przez Vite (domyślnie http://localhost:5173).

**Budowanie i podgląd produkcyjny**

```bash
npm run build
npm run preview
```

**Skrypty (z `package.json`)**
- `dev`: uruchamia Vite (serwer deweloperski)
- `build`: kompiluje TypeScript (`tsc -b`) i buduje aplikację (`vite build`)
- `preview`: serwuje zbudowaną aplikację lokalnie

**Wskazówki / Rozwiązywanie problemów**
- Jeśli pojawi się błąd związany z wersją Node, zaktualizuj Node do zalecanej wersji (18+).
- Jeśli port 5173 jest zajęty, Vite zaproponuje inny port — sprawdź wyjście w terminalu.
- W przypadku błędów TypeScript uruchom `npm run build`, aby zobaczyć szczegóły kompilacji.
- Aplikacja używa `src/services/storageService.ts` (LocalStorage) do prostego przechowywania danych — dane są lokalne w przeglądarce.

**Dekompozycja projektu**
- Kod źródłowy: `src/`
- Punkt wejścia: `src/main.tsx` i `src/App.tsx`
- Główne strony: `src/pages/` (Dashboard, Appointments, Doctors, Services, NewAppointment)
- Komponenty: `src/components/` (np. `AppointmentManager.tsx`, `DoctorCard.tsx`)

**Brak testów**
- Repozytorium nie zawiera testów automatycznych. Jeśli chcesz, mogę dodać podstawowy zestaw testów.

**Edytor i rozszerzenia**
- Zalecany edytor: Visual Studio Code
- Przydatne rozszerzenia: ESLint, Prettier, TypeScript

Jeśli chcesz, mogę dodać instrukcję uruchomienia z przykładowymi danymi (seed), konfigurację CI lub skrypt uruchamiający lint/format.
