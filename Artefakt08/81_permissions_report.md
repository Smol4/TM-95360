# RAPORT ANALIZY UPRAWNIEŃ

## 1. Zawartość raportu
Na podstawie pliku `AndroidManifest.xml` wykryto zestaw uprawnień oznaczonych jako ryzykowne oraz sprawdzono flagę `debuggable`.

## 2. Interpretacja wyniku
Jeśli aplikacja zawiera nadmiarowe uprawnienia, zwiększa to powierzchnię ataku. Szczególnie groźne są uprawnienia do SMS, połączeń, kontaktów oraz lokalizacji, gdy nie wynikają bezpośrednio z funkcji biznesowej aplikacji.

## 3. Wnioski inżynierskie
- Uprawnienia należy oceniać w kontekście funkcji aplikacji.
- Flaga `debuggable=true` w wersji produkcyjnej jest poważnym błędem bezpieczeństwa.
- Nawet pozornie „niskie” uprawnienia, jak `INTERNET`, mają znaczenie przy analizie całkowitego ryzyka.