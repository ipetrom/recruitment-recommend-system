
## 1. Dane i ich schematy

**Krótki opis wszystkich plików:**  
> Pliki zawierają dane ofert (`rr_vac_set.parquet`, `rr_vac_skills_set.parquet`), profile kandydatów (`contact_profiles_set.parquet`), umiejętności kandydatów (`contact_skills_set.parquet`), reguł asocjacyjnych (`ar_set.parquet`) oraz definicje profili stanowisk wraz z kategoriami (`position_profile_data.csv`).

### 2.1. Schemat plików

- **rr_vac_set.parquet** (oferty + agregaty aplikacji)  
  - `offer_id` – unikalny identyfikator oferty  
  - `accepted` – liczba kandydatów zaakceptowanych na tę ofertę  
  - `rejected` – liczba kandydatów odrzuconych na tę ofertę  
  - `name_profile` – nazwa profilu (np. „Data Scientist”) powiązana z ofertą  
  - `experience_years_min` – minimalne lata doświadczenia wymagane przez ofertę  

- **rr_vac_skills_set.parquet** (umiejętności wymagane przez oferty)  
  - `offer_id` – identyfikator oferty  
  - `skill` – nazwa umiejętności (np. „Python”, „SQL”)  
  - `source_type` – źródło umiejętności (np. „job_description”, „manual_tag”)  

- **contact_profiles_set.parquet** (profile kandydatów)  
  - `contact_id` – unikalny identyfikator kandydata  
  - `name_profile` – nazwa profilu kandydata (np. „Backend Engineer”)  
  - `is_main_profile` – flaga (True/False), czy to główny profil  
  - `is_preferred_profile` – flaga (True/False), czy to preferowany profil  
  - `experience_calculated` – wyliczone lata doświadczenia kandydata  

- **contact_skills_set.parquet** (umiejętności kandydatów)  
  - `contact_id` – identyfikator kandydata  
  - `skill` – nazwa umiejętności posiadanej przez kandydata  

- **ar_set.parquet** (reguły asocjacyjne między umiejętnościami)  
  - `lhs` – lewa strona reguły (np. zestaw umiejętności)  
  - `rhs` – prawa strona reguły  
  - `confidence` – wartość ufności reguły  
  - `lift` – wartość liftu reguły  

- **position_profile_data.csv** (definicje profili stanowisk)  
  - kolumny:  
    1. `PositionTitle` – tytuł stanowiska  
    2. `cat_name_profile` – główna kategoria profilu  
    3. `cat_name_subprofile` – podkategoria / subprofil  

---

## 2. Zadanie: System rekomendacyjny (Notebook)

> **UWAGA:** Zadania **nie da się rozwiązać w 100%** – chodzi o **podejście**, kreatywność, dokumentację procesu, pomysły, “ślepe drogi” i plany, czego brakuje, by w rzeczywistości dopasować kandydatów do ofert. Dane są rzeczywiste, ale bardzo okrojone więc nie uda ci się przewidzieć rzeczywistości.  

1. **Preprocessing & Eksploracja**  
   - Wczytaj `rr_vac_set.parquet` (kolumny: `offer_id`, `accepted`, `rejected`, `name_profile`, `experience_years_min`) oraz pliki umiejętności i profili.  
   - Zbadaj rozkłady: liczba zaakceptowanych vs odrzuconych, profile ofert, wymagane vs posiadane skille.

2. **Model / Heurystyka**  
   - W notebooku zbuduj własny system rekomendacyjny (content-based, collaborative, hybryda, heurystyka lub zaproponuj coś swojego).  
   - Opisz **wszystkie** podejścia: pomysły, metryki, testowane warianty, ślepe drogi, braki danych.

3. **Rezultaty**  
   - Dla przykładowych `offer_id` wygeneruj ranking `contact_id` (plik `offer_id`, `status`, `contact_id`) i uzasadnij wybór (kluczowe skille, zgodność profilu, doświadczenie).

4. **Dokumentacja w notebooku**  
   - Komórki Markdown z opisem kroków, wniosków oraz co i dlaczego **nie** da się osiągnąć przy obecnych danych.

---

## 3. Notatka końcowa (README.md)

Na koniec w `README.md` opisz krótko:

- **Co zostało zrobione**  
- **Co zostało pominięte**  
- **Wyzwania** i **wnioski**

---
