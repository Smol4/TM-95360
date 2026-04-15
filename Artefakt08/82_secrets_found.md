# RAPORT ANALIZY WYCIEKÓW (SECRETS)

**Imię i nazwisko:** Jakub Smoliński 
**Numer indeksu:** 95360

## 1. Top 3 Zagrożenia
1. res/layout/mapview.xml: apiKey
	Uzasadnienie: wpis apiKey w pliku związanym z widokiem mapy jest najbardziej zbliżony do realnego sekretu konfiguracyjnego. Nawet jeśli skaner nie pokazał wartości klucza, sama obecność takiego identyfikatora sugeruje, że aplikacja mogła korzystać z klucza API powiązanego z usługą zewnętrzną.
2. res/xml/device_admin_sample.xml: password / login
	Uzasadnienie: zestaw trafień login i password w jednym pliku jest bardziej podejrzany niż pojedyncze wystąpienia tych słów. Może wskazywać na formularz logowania, konfigurację testową albo demonstracyjne dane, które warto ręcznie sprawdzić pod kątem osadzonych poświadczeń.
3. smali/...: token w kodzie zdekompilowanym
	Uzasadnienie: wystąpienia słowa token w plikach .smali mogą wskazywać na obsługę tokenów sesyjnych, autoryzacyjnych albo obiektów komunikacyjnych. Nie potwierdza to wycieku, ale z punktu widzenia analizy bezpieczeństwa taki trop zasługuje na weryfikację, bo może prowadzić do mechanizmów uwierzytelniania aplikacji.

## 2. Top 3 False Positives
1. http://schemas.android.com/apk/res/android
	Uzasadnienie: to standardowa przestrzeń nazw Androida, pojawiająca się masowo w plikach XML. Nie jest sekretem ani poufnym adresem — to normalny element składni zasobów aplikacji.
2. **res/values/ids.xml i res/values/public.xml: login / password** 
	Uzasadnienie: tutaj loginipassword` wyglądają jak identyfikatory zasobów interfejsu, a nie prawdziwe dane logowania. Skaner dopasował słowa do wzorca, ale sam wpis nie oznacza obecności hasła.
3. http://www.google.com, http://www.example.com/...
	Uzasadnienie: to zwykłe przykładowe lub demonstracyjne adresy URL. Pasują do heurystyk skanera, ale nie stanowią realnego sekretu ani podatności samej w sobie.

## 3. Wniosek końcowy
Automatyczny skaner wykrył wiele trafień, ale zdecydowana większość wygląda na szum: standardowe adresy Androida, identyfikatory pól interfejsu oraz przykładowe teksty i linki. Najbardziej warte ręcznej weryfikacji są wpisy związane z apiKey, parą login/password w jednym pliku oraz odwołania do token w kodzie. Ostatecznie analiza potwierdza, że największą wartość ma ręczna interpretacja wyników i odróżnienie realnych zagrożeń od false positives.