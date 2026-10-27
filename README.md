# HCV w Polsce – czy inwestycja w testowanie i leczenie się zwraca?

Edukacyjny model farmakoekonomiczny WZW typu C (HCV) w Polsce. Pokazuje, czy i kiedy dodatkowe wydatki publiczne na testowanie i leczenie HCV zwracają się państwu (NFZ, ZUS, KRUS, budżet), z 95% przedziałami niepewności.

**Wszystkie wyniki to szacunki modelu, nie dane obserwowane.** Materiał ma charakter edukacyjny, jest neutralny i nie jest reklamą żadnego produktu leczniczego. Nie zawiera nazw leków ani firm.

## Zawartość
- `index.html` – aplikacja (jeden plik, działa offline): wynik, kalkulator, scenariusze, założenia, przewodnik „Jak czytać”, metodologia, źródła.
- `pobierz/hcv_model_inwestycji.xlsx` – model z formułami (bez makr).
- `pobierz/parametry.csv` – 93 parametry, każdy ze źródłem, datą i typem (dane PL / zagraniczne / założenie).
- `SPEC_panel_6_rol.md` – specyfikacja i **symulowana** recenzja sześciu ról (np. płatnik, ZUS, klinicysta). Role zostały odegrane przez autora narzędzia; żadna realna osoba ani instytucja nie recenzowała ani nie zatwierdzała tej aplikacji.

## Metoda w skrócie
Model Markowa z otwartą kohortą (2026–2075), probabilistyczna analiza wrażliwości (Monte Carlo, 2000 losowań), perspektywy płatnika zgodne z wytycznymi AOTMiT, dyskontowanie 5% / 3,5%. Szczegóły i ograniczenia: zakładka „Metodologia” w aplikacji.

## Źródła
Dane publiczne: NFZ (statystyki programu lekowego B.71, Informator o terminach leczenia), NIZP PZH-PIB (EPIMELD), GUS, ZUS, AOTMiT, literatura recenzowana. Pełna lista ze źródłem i datą każdej liczby: zakładka „Źródła” oraz `pobierz/parametry.csv`. Stan danych: 27.10.2026.

## Licencja
Treść, dane pochodne i model: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pl). Dane źródłowe pozostają na licencjach ich wydawców.
