Digital Healthcare Platform

---

## **Temat: System opieki zdrowotnej (SOZ)**

---

### **Cel**

Zaprojektować architekturę IT dla **Platformy Cyfrowej Opieki Zdrowotnej (SOZ)**, która łączy pacjentów, świadczeniodawców usług medycznych i laboratoria diagnostyczne w bezpieczny, skalowalny i interoperacyjny sposób.

---

## **Kontekst**

Średniej wielkości grupa dostawców usług opieki zdrowotnej prowadzi **pięć szpitali** i **20 przychodni**. Chce zbudować ujednoliconą **System opieki zdrowotnej (SOZ)**, który zmodernizuje ekosystem zarządzania pacjentami i danymi.

System musi obsługiwać **telemedycynę**, **integrację Elektronicznej Dokumentacji Medycznej (EDM)**, **wymianę danych laboratoryjnych** oraz **panele analityczne** w celu uzyskania wglądu operacyjnego.
### **Główne cele systemu**

* Umożliwienie **pacjentom** umawiania wizyt, przeglądania dokumentacji medycznej i konsultacji lekarskich online.
* Umożliwienie **lekarzom** bezpiecznego dostępu do historii pacjentów, wyników badań laboratoryjnych i danych obrazowych.
* Umożliwienie **laboratoriom** elektronicznego przesyłania wyników i integracji z dokumentacją pacjentów.
* Wsparcie **analizy** danych medycznych (np. trendy, obłożenie, wyniki).
* Zgodność z przepisami dotyczącymi prywatności danych i opieki zdrowotnej (Ochrona danych pacjenta / RODO).

---

## **Zadania**

### **1. Analiza wymagań**

Zidentyfikować i opisać:

* **Wymagania funkcjonalne** (telemedycyna, planowanie wizyt, dokumentacja pacjentów, rozliczenia itp.)
* **Wymagania niefunkcjonalne** (dostępność, skalowalność, opóźnienia, bezpieczeństwo, zgodność).
* **Interesariusze** i ich **problemy** (pacjenci, lekarze, administracja szpitali, organy regulacyjne).
* Dokonać szacowania skali systemu (back of envelope calculation).


---

### **2. Projekt architektury**

Stworzyć projekt architektury, który obejmuje:

1. **Warstwa prezentacji:** Portal internetowy pacjenta, aplikacja mobilna, panel lekarza.
2. **Warstwa aplikacji:** Podstawowe mikrousługi (wizyty, konsultacje, dokumentacja, rozliczenia).
3. **Warstwa integracji:** Wymiana danych medycznych z wykorzystaniem standardów HL7/FHIR; kolejki komunikatów do komunikacji opartej na zdarzeniach.
4. **Warstwa danych:** Relacyjna baza danych dla danych ustrukturyzowanych, magazyn obiektów blob dla obrazów/skanów, magazyn danych analitycznych.
5. **Warstwa infrastruktury:** Wdrożenie w chmurze lub hybrydowe; zarządzanie tożsamościami, monitorowanie, rejestrowanie.

Artefakty architektoniczne:

* **Diagram kontekstu (C4 Poziom 1)** – system i encje zewnętrzne.
* **Diagram kontenerów (C4 Poziom 2)** – logiczne podsystemy i punkty integracji.
* **Diagram komponentów (poziom C4 3)** – szczegółowe omówienie jednej usługi (np. usługi umawiania wizyt lub telemedycyny).
* **Diagram wdrożenia** – przedstawiający chmurę, regiony i strefy awaryjne.
* **Diagram encji/klas** – główne elementy danych i ich relacje

---

### **3. Wybór technologii**

Zaproponować technologie/frameworki dla każdej warstwy. Przykładowe decyzje architektoniczne:


* **Frontend:** React / Vue.js / Flutter
* **Backend:** .NET Core / Java Spring Boot / Node.js
* **Integracja:** FHIR APIs, Kafka / RabbitMQ
* **Bazy danych:** PostgreSQL / MongoDB / Azure Cosmos DB / S3 for images
* **Analityka:** Power BI / Tableau / AWS QuickSight
* **Hosting:** Azure Health Cloud / AWS HealthLake / Google Cloud Healthcare API

---

### **4. Wzorce i taktyki architektoniczne**

Opisać wzorce i taktyki architektoniczne dla:

* **Bezpieczeństwo i zgodność:** Uwierzytelnianie (OAuth2, OpenID Connect), szyfrowanie danych, logi audytu.
* **Wydajność:** Równoważenie obciążenia, buforowanie (Redis), przetwarzanie asynchroniczne.
* **Interoperacyjność:** Wykorzystanie standardów danych medycznych (HL7, FHIR).
* **Odzyskiwanie po awarii:** Replikacja danych, kopie zapasowe, redundancja geograficzna.
* **Monitorowanie:** Natywny dla chmury monitoring, alerty, scentralizowane rejestrowanie.

---

### **5. Uzasadnienie architektury**

Uzasadnić adekwatność zaprojektowanej architektury:

* Dlaczego ta architektura jest zgodna z celami biznesowymi
* Jak równoważy złożoność, elastyczność i koszty
* Kluczowe ryzyka i strategie ich ograniczania

---

### 6 **Forma projektu** 

Dokument 10-15 stron zawierający powyżej wymienione diagramy i wszelkie uzasadnienia.  
