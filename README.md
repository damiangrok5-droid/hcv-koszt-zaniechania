# HCV w Polsce – czy inwestycja w testowanie i leczenie się zwraca?

Edukacyjny model farmakoekonomiczny WZW typu C (HCV) w Polsce. Pokazuje, czy i kiedy dodatkowe wydatki publiczne na testowanie i leczenie HCV zwracają się państwu (NFZ, ZUS, KRUS, budżet), z 95% przedziałami niepewności. Pokazuje też wariant, w którym testy finansuje inny płatnik (koszt wyleczenia vs koszt nieleczenia) – koszt testów nie znika wtedy z budżetu publicznego, tylko przechodzi do innego płatnika.

**Wszystkie wyniki to szacunki modelu, nie dane obserwowane.** Materiał ma charakter edukacyjny, jest neutralny i nie jest reklamą żadnego produktu leczniczego. Nie zawiera nazw leków ani firm.

## Zawartość
- `index.html` – aplikacja (jeden plik, działa offline): wynik, kalkulator, scenariusze, założenia, przewodnik „Jak czytać”, metodologia, źródła.
- `pobierz/hcv_model_inwestycji.xlsx` – model z formułami (bez makr).
- `pobierz/parametry.csv` – 110 parametrów, każdy ze źródłem, datą i typem (dane PL / zagraniczne / założenie).
- `SPEC_panel_6_rol.md` – specyfikacja i **symulowana** recenzja sześciu ról (np. płatnik, ZUS, klinicysta). Role zostały odegrane przez autora narzędzia; żadna realna osoba ani instytucja nie recenzowała ani nie zatwierdzała tej aplikacji.

## Metoda w skrócie
Model Markowa z otwartą kohortą (2026–2075, grupy wieku, korekta połowy cyklu), wyniki główne dla wartości bazowych założeń, probabilistyczna analiza wrażliwości (Monte Carlo, 2000 losowań), perspektywy płatnika zgodne z wytycznymi AOTMiT, dyskontowanie 5% / 3,5%. Szczegóły i ograniczenia: zakładka „Metodologia” w aplikacji.

## Źródła
Dane publiczne: NFZ (statystyki programu lekowego B.71, Informator o terminach leczenia), NIZP PZH-PIB (EPIMELD), GUS, ZUS, AOTMiT, literatura recenzowana. Pełna lista ze źródłem i datą każdej liczby: zakładka „Źródła” oraz `pobierz/parametry.csv`. Stan danych: 28.10.2026.

## Lista zmian – 28.10.2026 (wersja po audycie)
Wersja po wewnętrznym audycie metodycznym (3 błędy krytyczne, 8 istotnych, 12 drobnych – wszystkie wprowadzone lub opisane jako ograniczenie). **Wyniki programów są gorsze niż w wersji z 27.10.2026** – np. testowanie w populacjach kluczowych nie zwraca się już w 50 lat (wcześniej ok. 2041 r.). Główna przyczyna: koszty opieki i świadczenia ZUS liczone teraz tylko dla osób zdiagnozowanych i pozostających pod opieką. Tabela „przed i po”: zakładka „Jak to zostało sprawdzone” w aplikacji.

- K1: koszty opieki NFZ (F0–F4) i absencja/ZUS liczone tylko dla zdiagnozowanych pod opieką (wcześniej dla wszystkich ok. 155 tys. z wiremią). Wariant dawny = scenariusz CARE_ALL=1.
- K2: PSA – mnożniki kalibracyjne K_DC, K_HCC oraz DC0, PLT0 losowane symetrycznie (lognormalnie) wokół wartości bazowej; K=1 przeniesione do osobnego scenariusza.
- K3: opis zgonów poprawiony – liczby C22/K74 to wszystkie zgony z tych przyczyn, tylko część wynika z HCV; zgony z przyczyną wyjściową B18 (przewlekłe WZW typu B i C łącznie) to 88 w 2023 r. (NIZP PZH-PIB); model szacuje ok. 920 zgonów wątrobowych związanych z HCV rocznie (2026).
- I1: źródło kosztów i prawdopodobieństw opisane jako analiza wnioskodawcy (firma konsultingowa) opublikowana w BIP AOTMiT; model choroby dla Polski (2015) opisany jako wspierany finansowo przez producenta leków; błędy standardowe z Tab. 198.
- I2: maksimum leczonych w B.71 = 12 171 (2017), nie 8 521; szczyt pakietu WHO porównany z tą wartością.
- I3: wynik główny = wynik bazowy (deterministyczny); Monte Carlo podawane osobno jako mediana [95%] i P(oszczędność).
- I4: pakiet WHO zawiera koszt nawigacji pacjenta (NAV) i koszty stałe programu (FIX); I1/I2 – koszty stałe.
- I5: kalibracja raka wątroby do Krajowego Rejestru Nowotworów (ok. 712 nowych HCC przypisanych HCV w 2026 r.).
- I6: rozrzut ceny leków w PSA z wahań 2017–2025; cena z 2017 r. (33 872 zł) jako scenariusz.
- I7: renty przeliczane wskaźnikami waloryzacji ZUS; WLOSS skalibrowane do danych ZUS; EMP opisane jako ograniczenie.
- I8: kohorta w 4 grupach wieku (B.71 2025); średni wiek losowany w PSA.
- D1–D12: p90 kolejki 567/585 dni; Rosińska i in. 2015 (dane 2004–05); RE_KEY 6,2/100 osobolat; korekta połowy cyklu; SMR 10 dla PWID (symetrycznie); SVR 0,97; uwaga o niespójności p_SCCHCC; koszt 1. roku po przeszczepie 30 167,61 zł (×CPI); uwagi o reinfekcji i użytecznościach; scenariusz malejącej zapadalności; 38 zamawiających; kalkulator 300 vs 2 000 losowań i kolejność kwantyli roku zwrotu.
- Nowe: wariant „testy finansuje inny płatnik” (porównanie samego kosztu wyleczenia z kosztami nieleczenia) oraz wynik na jednego zdiagnozowanego pacjenta.
- Model z wersji v1 (pe_model) jest zastąpiony przez silnik aplikacji i nie jest publikowany.
- Dodatkowo: w pliku xlsx usunięto kolizję nazw zakresów (stopa dyskonta kosztów i efektów) – po poprawce wartości w arkuszu zgadzają się ze stroną.

Poprzednia wersja (27.10.2026) jest dostępna w historii repozytorium; jej wyniki są nieaktualne.

## Licencja
Treść, dane pochodne i model: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pl). Dane źródłowe pozostają na licencjach ich wydawców.
