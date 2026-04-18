# Realizacja projektu

---

## 1. Analiza wymagań

### 1.1 Aktorzy systemu i ich problemy

| Aktor | Rola w systemie | Główne problemy / oczekiwania |
|---|---|---|
| **Pacjent** | Użytkownik systemu korzystający z usług medycznych | Brak wglądu we własną dokumentację medyczną; konieczność osobistego umawiania wizyt; brak możliwości konsultacji lekarskich bez wychodzenia z domu |
| **Lekarz** | Użytkownik systemu zajmujący się leczeniem pacjentów | Brak dostępu do historii leczenia pacjenta z innych placówek; konieczność ręcznego prowadzenia dokumentacji medycznej; brak bezpośredniego dostępu do wyników badań pacjentów, w tym badań obrazowych; brak możliwości udzielania teleporad |
| **Laboratorium** | Dostarczyciel wyników badań | Brak zautomatyzowanego przekazywania wyników badań (papierowe lub mailowe); brak integracji z EDM pacjenta; brak możliwości przeglądania statystyk dotyczących wykonanych badań |
| **Administrator przychodni** | Użytkownik systemu posiadający wgląd operacyjny w funkcjonowanie placówki (wizyty, pacjenci, harmonogram) | Brak centralnego wglądu w harmonogram wizyt; trudności w zarządzaniu rejestracją pacjentów; brak możliwości generowania raportów dotyczących funkcjonowania placówki |
| **Administrator IT systemu** | Użytkownik odpowiedzialny za monitorowanie działania systemu w środowisku produkcyjnym oraz utrzymanie jego bezpieczeństwa | Brak możliwości monitorowania działania systemu w czasie rzeczywistym; brak narzędzi do szybkiego wykrywania i diagnozowania błędów; brak automatycznych powiadomień o awariach; brak mechanizmów wspierających zapewnienie ciągłości działania systemu |
| **Specjalista ds. zgodności** | Osoba odpowiedzialna za nadzór nad zgodnością systemu z przepisami i politykami bezpieczeństwa | Brak możliwości weryfikacji zgodności działania systemu z obowiązującymi przepisami prawa; brak narzędzi do wykazania spełnienia wymogów regulacyjnych |

### 1.2 Zewnętrzne systemy publiczne

| System zewnętrzny | Cel integracji |
|---|---|
| **Centrum e-Zdrowia** | Obsługa e-recept oraz e-skierowań |
| **eWUŚ** | Możliwość weryfikacji ubezpieczenia pacjenta |

---

### 1.3 Wymagania funkcjonalne

#### F1 – Zarządzanie wizytami

| ID | Wymaganie |
|---|---|
| F1.1 | System powinien umożliwiać pacjentowi umawianie i odwoływanie wizyt przez portal internetowy lub aplikację mobilną |
| F1.2 | System powinien umożliwiać pacjentowi podgląd dostępnych terminów wizyt dla wybranych lekarzy i przychodni |
| F1.3 | System powinien wysyłać pacjentowi automatyczne przypomnienia o nadchodzącej wizycie za pomocą wiadomości SMS |
| F1.4 | System powinien umożliwiać użytkownikom posiadającym odpowiednie uprawnienia podgląd szczegółów wizyty (data, godzina, gabinet, dane pacjenta) |
| F1.5 | System powinien umożliwiać lekarzowi podgląd dziennego harmonogramu wizyt |
| F1.6 | System powinien umożliwiać lekarzowi zmianę statusu wizyty |
| F1.7 | System powinien umożliwiać lekarzowi definiowanie dostępnych terminów wizyt |

#### F2 – Telemedycyna

| ID | Wymaganie |
|---|---|
| F2.1 | System powinien umożliwiać pacjentowi kontakt z lekarzem poprzez czat tekstowy za pośrednictwem portalu internetowego lub aplikacji mobilnej |
| F2.2 | System powinien umożliwiać przesyłanie załączników w ramach komunikacji czatowej między pacjentem a lekarzem |
| F2.3 | System powinien umożliwiać pacjentowi umawianie wizyt w formie teleporad |
| F2.4 | System powinien umożliwiać lekarzowi dostęp do EDM pacjenta |
| F2.5 | System powinien umożliwiać lekarzowi wystawianie e-recept oraz e-skierowań w ramach konsultacji |

#### F3 – Elektroniczna Dokumentacja Medyczna (EDM)

| ID | Wymaganie |
|---|---|
| F3.1 | System powinien umożliwiać przechowywanie ujednoliconej dokumentacji medycznej pacjenta w ramach EDM |
| F3.2 | System powinien umożliwiać lekarzowi tworzenie, edytowanie i przeglądanie EDM pacjenta |
| F3.3 | System powinien umożliwiać pacjentowi przeglądanie i pobieranie fragmentów EDM przypisanej do niego |
| F3.4 | System powinien rejestrować historię zmian oraz dostępów do EDM, wraz z informacją o użytkowniku i czasie wykonania operacji oraz jej typie |
| F3.5 | System powinien umożliwiać przechowywanie i przeglądanie załączników z wynikami badań w ramach EDM w formatach PDF oraz DICOM |

#### F4 – Integracja laboratoryjna

| ID | Wymaganie |
|---|---|
| F4.1 | System powinien umożliwiać laboratorium przesyłanie wyników badań bezpośrednio do EDM pacjenta w formatach PDF oraz DICOM |
| F4.2 | System powinien powiadamiać pacjenta o dostępności wyników badań za pomocą wiadomości SMS |
| F4.3 | System powinien umożliwiać lekarzowi wystawianie zleceń badań laboratoryjnych dla pacjenta |
| F4.4 | System powinien umożliwiać wyszukiwanie zleceń badań laboratoryjnych na podstawie ich identyfikatora |
| F4.5 | System powinien umożliwiać pacjentowi podgląd i pobieranie wyników badań laboratoryjnych na podstawie numeru PESEL oraz identyfikatora badania |

#### F5 – Analityka i raportowanie

| ID | Wymaganie |
|---|---|
| F5.1 | System powinien umożliwiać generowanie statystyk dotyczących liczby i rodzaju wykonanych badań laboratoryjnych |
| F5.2 | System powinien umożliwiać administratorowi przychodni generowanie statystyk dotyczących liczby wizyt |
| F5.3 | System powinien umożliwiać administratorowi przychodni wizualizację zajętości gabinetów |
| F5.4 | System powinien umożliwiać administratorowi przychodni podgląd zaplanowanych wizyt w konkretnych placówkach |

#### F6 – Bezpieczeństwo

| ID | Wymaganie |
|---|---|
| F6.1 | System powinien dostosowywać dostęp do funkcji i widoków w zależności od przypisanej użytkownikowi roli |
| F6.2 | System powinien wymagać uwierzytelniania dwuskładnikowego (MFA) dla użytkowników innych niż pacjent |
| F6.3 | System powinien automatycznie wylogowywać użytkownika po określonym czasie bezczynności |

---

### 1.3 Wymagania niefunkcjonalne

TODO: niefunkcjonalne poprawić

| F7.4 | Wszystkie operacje na danych wrażliwych są logowane do niemodyfikowalnego logu audytu |

#### Dostępność i niezawodność

| ID | Wymaganie | Wartość docelowa |
|---|---|---|
| NF1.1 | Dostępność systemu (SLA) | ≥ 99.9% (max ~8.7h przestoju/rok) |
| NF1.2 | RTO (Recovery Time Objective) – czas odtworzenia po awarii | ≤ 4 godziny |
| NF1.3 | RPO (Recovery Point Objective) – maksymalna utrata danych | ≤ 1 godzina |
| NF1.4 | Awaria pojedynczej strefy/węzła nie powoduje niedostępności systemu | Brak SPOF (Single Point of Failure) |

#### Wydajność i skalowalność

| ID | Wymaganie | Wartość docelowa |
|---|---|---|
| NF2.1 | Czas odpowiedzi API (operacje odczytu) | ≤ 200 ms (p95) |
| NF2.2 | Czas ładowania strony portalu pacjenta | ≤ 3 s (łącze 10 Mbps) |
| NF2.3 | Przepustowość systemu w godzinach szczytu | ≥ 2 000 req/s |
| NF2.4 | Czas przesyłu badania obrazowego (DICOM ~100 MB) | ≤ 30 s |
| NF2.5 | System skaluje się horyzontalnie bez przestoju | Auto-skalowanie w chmurze |

#### Bezpieczeństwo i zgodność

| ID | Wymaganie |
|---|---|
| NF3.1 | Wszystkie dane w spoczynku szyfrowane algorytmem AES-256 |
| NF3.2 | Komunikacja sieciowa wyłącznie przez TLS 1.3 |
| NF3.3 | Zgodność z RODO: prawo dostępu, sprostowania, usunięcia, przenoszenia danych |
| NF3.4 | Pseudonimizacja danych pacjentów w środowiskach analitycznych |
| NF3.5 | Logowanie audytu dla każdego dostępu do danych wrażliwych (kto, kiedy, co) |
| NF3.6 | Certyfikacja ISO 27001 dla procesów zarządzania bezpieczeństwem |

#### Interoperacyjność

| ID | Wymaganie |
|---|---|
| NF4.1 | API zgodne ze standardem HL7 FHIR R4 |
| NF4.2 | Obsługa formatu DICOM dla danych obrazowych |
| NF4.3 | Możliwość integracji z systemami zewnętrznymi (NFZ, ZUS, inne szpitale) przez otwarte API |

#### Utrzymywalność i monitorowanie

| ID | Wymaganie |
|---|---|
| NF5.1 | Scentralizowane logowanie i monitoring (metryki, alerty, tracing) |
| NF5.2 | Możliwość wdrażania aktualizacji bez przestoju (rolling deployment) |
| NF5.3 | Środowiska: produkcja, staging, testowe – izolowane od siebie |

---

### 1.4 Szacowanie skali systemu (Back of Envelope)

#### Założenia bazowe

| Parametr | Wartość | Uzasadnienie |
|---|---|---|
| Placówki | 25 (5 szpitali + 20 przychodni) | Dane z treści zadania |
| Łóżka szpitalne | 1 500 (5 × 300) | Typowy szpital regionalny |
| Personel medyczny | ~650 lekarzy, ~2 000 pielęgniarek/techników | Szacunek dla sieci tej skali |
| Personel administracyjny | ~500 osób | ~20 osób/placówka |
| Zarejestrowanych pacjentów | **500 000** | Obszar obsługi ~700 000 mieszkańców |

#### Ruch użytkowników

```
Dziennie aktywnych pacjentów:   ~10 000  (2% z 500 000)
Dziennie aktywnego personelu:   ~3 150   (personel medyczny + admin)
Łącznie DAU:                    ~13 000

Szczyt jednoczesnych sesji:     ~2 000   (15% DAU w godzinie szczytu)
Szczyt req/s (API):             ~2 000   (zakładając ~1 req/s/użytkownika)
Średnie req/s:                  ~200     (poza szczytem)
```

#### Dane – wizyty

```
Wizyt dziennie:                 5 000    (200/placówka/dzień)
Wizyt rocznie:                  ~1 500 000
Rozmiar rekordu wizyty:         ~5 KB
Roczny przyrost danych wizyt:   ~7.5 GB
```

#### Dane – wyniki laboratoryjne

```
Wyników dziennie:               10 000   (2 wyniki/wizyta)
Rozmiar jednego wyniku:         ~50 KB
Dzienny przyrost:               ~500 MB
Roczny przyrost:                ~180 GB
```

#### Dane – obrazowanie medyczne (DICOM)

```
Badań obrazowych dziennie:      500      (10% pacjentów ambulatoryjnych)
Rozmiar jednego badania:        ~100 MB  (TK/MRI; RTG ~10 MB, USG ~50 MB)
Dzienny przyrost:               ~50 GB
Roczny przyrost:                ~18 TB
```

#### Dane – EDM (dokumentacja kliniczna)

```
Rekordów pacjentów:             500 000
Rozmiar rekordu (bez obrazów):  ~5 MB
Łączna baza EDM:                ~2.5 TB
Roczny przyrost EDM:            ~500 GB  (nowe notatki, wyniki tekstowe)
```

#### Telemedycyna

```
Konsultacji wideo dziennie:     500      (10% wizyt)
Szczyt jednoczesnych połączeń:  ~200
Przepustowość na sesję wideo:   2 Mbps (720p, kodek VP8/H.264)
Szczytowe zapotrzebowanie:      ~400 Mbps
```

#### Całkowite zapotrzebowanie na przestrzeń dyskową (horyzont 3 lat)

| Kategoria danych | Rozmiar (3 lata) |
|---|---|
| Obrazowanie medyczne (DICOM) | ~54 TB |
| EDM (dokumentacja kliniczna) | ~4 TB |
| Wyniki laboratoryjne | ~0.5 TB |
| Nagrania wideo (opcjonalne) | ~10 TB |
| Logi, kopie zapasowe, metadane | ~2 TB |
| **Łącznie** | **~70 TB** |

#### Podsumowanie – kluczowe parametry projektowe

| Parametr | Wartość |
|---|---|
| Użytkownicy (łącznie) | ~503 000 |
| Szczyt jednoczesnych sesji | ~2 000 |
| Szczyt API req/s | ~2 000 |
| Dane do przechowania (3 lata) | ~70 TB |
| Roczny przyrost danych | ~19 TB/rok |
| Szczytowa przepustowość wideo | ~400 Mbps |
| Wymagana dostępność | 99.9% |

> Powyższe obliczenia wskazują, że system należy zaprojektować z myślą o przechowywaniu dziesiątek terabajtów danych (zdominowanych przez obrazowanie medyczne), obsłudze tysięcy jednoczesnych użytkowników oraz przepustowości rzędu setek Mbps dla strumieni wideo. Wymaga to architektury chmurowej z automatycznym skalowaniem, obiektowego magazynu danych dla plików DICOM oraz oddzielnej warstwy analitycznej izolowanej od systemu transakcyjnego.