# Realizacja projektu

---

## 1. Analiza wymagań

### 1.1 Interesariusze i ich problemy

| Interesariusz | Rola w systemie | Główne problemy / oczekiwania |
|---|---|---|
| **Pacjent** | Użytkownik końcowy korzystający z usług medycznych | Brak wglądu w własną dokumentację; konieczność osobistego umawiania wizyt; duplikacja badań przy zmianie placówki; brak możliwości zdalnej konsultacji |
| **Lekarz / specjalista** | Świadczeniodawca usług medycznych | Brak dostępu do historii pacjenta z innych placówek; czasochłonne ręczne prowadzenie dokumentacji; opóźnienia w otrzymywaniu wyników laboratoryjnych; brak narzędzi do pracy zdalnej |
| **Administracja szpitala / przychodni** | Zarządzanie operacyjne placówką | Brak centralnego wglądu w obłożenie i zasoby; trudności w rozliczeniach z NFZ; niemożność analizy trendów i planowania budżetu |
| **Laboratorium diagnostyczne** | Dostarczyciel wyników badań | Ręczne lub papierowe przekazywanie wyników; brak integracji z EDM pacjenta; ryzyko błędów przy przepisywaniu danych |
| **NFZ / płatnik** | Finansowanie i rozliczenia | Niejednolite formaty danych do rozliczeń; trudności w weryfikacji świadczeń; brak automatycznych raportów |
| **UODO / organ regulacyjny** | Nadzór nad ochroną danych osobowych | Trudności w egzekwowaniu praw podmiotów danych (RODO); brak spójnych logów audytu; ryzyko wycieku danych wrażliwych |
| **Administrator IT systemu** | Utrzymanie i bezpieczeństwo platformy | Zarządzanie wieloma izolowanymi systemami; brak centralnego monitoringu; trudności w zapewnieniu ciągłości działania |

---

### 1.2 Wymagania funkcjonalne

#### F1 – Zarządzanie wizytami

| ID | Wymaganie |
|---|---|
| F1.1 | Pacjent może samodzielnie umawiać, odwoływać i przenosić wizyty przez portal lub aplikację mobilną |
| F1.2 | System prezentuje dostępne terminy na podstawie kalendarza lekarza i zasobów placówki |
| F1.3 | System wysyła automatyczne przypomnienia o wizycie (SMS, e-mail, push) |
| F1.4 | Lekarz widzi dzienny harmonogram wizyt wraz z krótkim podsumowaniem historii pacjenta |

<!-- | ID | Wymaganie |
|---|---|
| F1.1 | Pacjent może wyszukiwać dostepne terminy wizyt
| F1.2 | Pacjent może umówić lub odwołać wizytę
| F1.3 | Pacjent otrzyma powiadomienie (SMS, e-mail, push) o zblizajacej się wizycie
| F1.4 | Lekarz może sprawdzić harmonogram wizyt z przypisanymi do niego pacjentami -->


#### F2 – Telemedycyna

| ID | Wymaganie |
|---|---|
| F2.1a | Pacjent może skontaktować się z lekarzem w ramach platformy |
| F2.1b | Lekarz może prowadzić wizytę wideo z pacjentem w ramach platformy (szyfrowane połączenie) |
| F2.2 | Podczas konsultacji online lekarz ma dostęp do EDM pacjenta |
| F2.3 | Lekarz może wystawić e-receptę i e-skierowanie w trakcie lub po konsultacji wideo |
| F2.4 | Nagrania konsultacji mogą być opcjonalnie przechowywane (za zgodą pacjenta) |
| F2.5 | System obsługuje czat tekstowy jako alternatywę dla połączenia wideo |

#### F3 – Elektroniczna Dokumentacja Medyczna (EDM)

| ID | Wymaganie |
|---|---|
| F3.1 | Każdy pacjent posiada ujednolicony rekord medyczny dostępny we wszystkich placówkach grupy |
| F3.2 | Lekarz może tworzyć, edytować i przeglądać notatki kliniczne, diagnozy i plany leczenia |
| F3.3 | System przechowuje i udostępnia wyniki badań obrazowych (DICOM) i laboratoryjnych |
| F3.4 | Pacjent może przeglądać własną dokumentację i pobierać jej fragmenty |
| F3.5 | Historia modyfikacji rekordów jest w pełni audytowalna (kto, kiedy, co zmienił) |
| F3.6 | EDM jest zgodna ze standardem HL7 FHIR R4 |

#### F4 – Integracja laboratoryjna

| ID | Wymaganie |
|---|---|
| F4.1 | Laboratorium przesyła wyniki elektronicznie bezpośrednio do EDM pacjenta |
| F4.2 | Lekarz otrzymuje powiadomienie o dostępności nowych wyników |
| F4.3 | Wyniki krytyczne (alarmowe) generują natychmiastowy alert dla lekarza prowadzącego |
| F4.4 | System obsługuje zlecenia badań laboratoryjnych wystawiane elektronicznie przez lekarza |

#### F5 – Rozliczenia i finanse

| ID | Wymaganie |
|---|---|
| F5.1 | System automatycznie generuje dokumenty rozliczeniowe dla NFZ na podstawie zrealizowanych świadczeń |
| F5.2 | Pacjent może przeglądać historię rozliczeń i opłat |
| F5.3 | System obsługuje płatności online za świadczenia komercyjne |
| F5.4 | Raporty finansowe dostępne są dla administracji w panelu analitycznym |

#### F6 – Analityka i raportowanie

| ID | Wymaganie |
|---|---|
| F6.1 | Panel analityczny prezentuje obłożenie placówek, czas oczekiwania i utilizację zasobów |
| F6.2 | Administrator placówki może generować raporty epidemiologiczne i kliniczne |
| F6.3 | Administrator placówki może zarządzać personelem i harmonogramami na poziomie placówki i grupy |
| F6.4 | Dane analityczne są zanonimizowane i nie zawierają PII pacjentów |

#### F7 – Bezpieczeństwo i zarządzanie dostępem

| ID | Wymaganie |
|---|---|
| F7.1 | Wielopoziomowy model uprawnień: pacjent, lekarz, specjalista, admin placówki, admin systemu |
| F7.2 | Uwierzytelnianie dwuskładnikowe (MFA) dla personelu medycznego |
| F7.3 | Pacjent może udzielać i cofać zgodę na dostęp do swojej dokumentacji |
| F7.4 | Wszystkie operacje na danych wrażliwych są logowane do niemodyfikowalnego logu audytu |

---

### 1.3 Wymagania niefunkcjonalne

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
