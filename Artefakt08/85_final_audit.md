# RAPORT Z AUDYTU BEZPIECZEŃSTWA: APIDEMOS

**Data:** 16.04.2026 
**Audytor:** Jakub Smoliński 95360
**Projekt:** ApiDemos

## 1. OCENA KOŃCOWA (SECURITY SCORE)
**WYNIK:** 0/100  
**STATUS:** REJECTED

## 2. KLUCZOWE OBSZARY RYZYKA

### A. Konfiguracja Systemowa (Zadanie 8.1)
**Problem:** Aplikacja posiada ryzykowne uprawnienia i wymaga oceny zgodności z funkcją biznesową.  
**Wpływ:** Zwiększona powierzchnia ataku i ryzyko nadużycia uprawnień.

### B. Wycieki Danych (Zadanie 8.2)
**Problem:** W kodzie lub zasobach wykryto potencjalne wzorce sugerujące obecność danych wrażliwych, adresów URL lub tokenów.  
**Wpływ:** Możliwość ujawnienia punktów komunikacji, konfiguracji lub elementów pomocnych w ataku.

### C. Biblioteki Zewnętrzne (Zadanie 8.3)
**Problem:** Wykryto przestarzałe biblioteki z przypisanymi podatnościami CVE.  
**Wpływ:** Aplikacja dziedziczy ryzyka bezpieczeństwa z łańcucha dostaw oprogramowania.

## 3. MAPA DROGOWA NAPRAWCZA (REMEDIATION)
1. **PRIORYTET 1:** Aktualizacja podatnych bibliotek i usunięcie komponentów z poziomem CRITICAL/HIGH.  
2. **PRIORYTET 1:** Przegląd i ograniczenie niepotrzebnych uprawnień w `AndroidManifest.xml`.  
3. **PRIORYTET 2:** Usunięcie hardcoded secrets oraz przeniesienie konfiguracji do bezpiecznego mechanizmu zarządzania sekretami.

## WNIOSKI KOŃCOWE
Aplikacja wymaga działań naprawczych przed uznaniem jej za bezpieczną. Największe ryzyko wynika z połączenia przestarzałych bibliotek, ryzykownych uprawnień i potencjalnych wycieków danych.