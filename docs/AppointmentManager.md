# Dokumentacja komponentu `AppointmentManager`

Krótki opis
---
`AppointmentManager` to wielofunkcyjny komponent React odpowiedzialny za rezerwację i zarządzanie wizytami. Zawiera formularz do dodawania nowych wizyt oraz listę istniejących rezerwacji z filtrami, wyszukiwaniem i podstawowymi akcjami (anuluj, usuń).

Lokalizacja pliku źródłowego
---
- `src/components/AppointmentManager.tsx`

Typy i props
---
- `type AppointmentManagerProps = { view?: 'form' | 'list' | 'full' }`
  - `view` (opcjonalne) — kontroluje, która część UI jest wyświetlana:
    - `'form'` — tylko formularz rezerwacji,
    - `'list'` — tylko lista wizyt,
    - `'full'` (domyślnie) — formularz + lista.

Stan komponentu (wybrane pola)
---
- `appointments: Appointment[]` — lista wizyt pobierana z `storageService`.
- `form: AppointmentFormData` — dane formularza (patientName, doctorId, serviceId, date, time).
- `statusFilter: AppointmentStatus | 'All'` — filtr statusu wizyt.
- `search: string` — fraza wyszukiwania (pacjent, lekarz, usługa).
- `message: string` — komunikaty informacyjne dla użytkownika.
- `showCancelled: boolean` — czy pokazywać anulowane wizyty.

Zależności i powiązane pliki
---
- `src/data/doctors.ts` — lista lekarzy używana w select.
- `src/data/services.ts` — lista usług (nazwa, cena, czas trwania).
- `src/services/storageService.ts` — funkcje `getAppointmentsFromStorage`, `saveAppointmentsToStorage`.
- `src/types/appointment.ts` — typy `Appointment`, `AppointmentFormData`, `AppointmentStatus`.
- `src/utils/date.ts` — pomocnicze formatery daty i wartości inputów.

Główne funkcje / zachowanie
---
- Pobieranie danych: w `useEffect` komponent pobiera zapisane wizyty z localStorage przez `getAppointmentsFromStorage`.
- Dodawanie wizyty: formularz waliduje dane (`isFormValid`) i dodaje nową wizytę na początek listy, zapisując w storage.
- Anulowanie wizyty: zmienia `status` na `Cancelled` i zapisuje zmiany.
- Usuwanie wizyty: usuwa wpis z listy i zapisuje zmienioną listę.
- Filtrowanie: możliwe filtrowanie po statusie (`Scheduled`, `Completed`, `Cancelled`, `All`), ukrywanie anulowanych przez `showCancelled` oraz wyszukiwanie po pacjencie, lekarzu i usłudze.
- Sortowanie: wizyty są sortowane po dacie i godzinie rosnąco (funkcja `sortAppointments`).

Elementy interfejsu
---
- Formularz rezerwacji:
  - pola: `Patient` (tekst), `Doctor` (select), `Service` (select), `Date` (date), `Time` (time)
  - przycisk: `Book appointment`
- Lista wizyt:
  - nagłówek ze statystykami (scheduled, completed, cancelled)
  - filtry: wyszukiwanie, select statusu, toggle `Show cancelled`
  - karta wizyty: status, imię pacjenta, data/godzina, lekarz, usługa, akcje (Cancel, Remove)

Przykład użycia
---
Import i osadzenie w aplikacji:

```tsx
import { AppointmentManager } from '../components/AppointmentManager';

// pełny widok (formularz + lista)
<AppointmentManager />

// tylko lista
<AppointmentManager view="list" />

// tylko formularz
<AppointmentManager view="form" />
```

Uwagi dotyczące rozszerzeń
---
- Walidacja: obecna walidacja jest prosta (długość imienia pacjenta > 2). Można dodać bardziej zaawansowaną walidację (np. walidacja kolizji terminów).
- Synchronizacja: teraz dane są lokalne (localStorage). Można wymienić `storageService` na serwis HTTP, aby zapisywać dane na serwerze.
- Testy: warto dodać jednostkowe testy dla funkcji pomocniczych (sortowanie, filtrowanie) i testy integracyjne komponentu.

FAQ / Tipy deweloperskie
---
- Jeśli domyślne `doctorId` lub `serviceId` są puste, `emptyForm` używa pierwszego elementu z `doctors` i `services`.
- Wiadomości użytkownika (np. potwierdzenie rezerwacji) są chwilowe — można rozszerzyć je o automatyczne ukrywanie po kilku sekundach.

Chcesz, żebym dodał:
- JSDoc w pliku `AppointmentManager.tsx`?
- oddzielne testy jednostkowe i integracyjne?
