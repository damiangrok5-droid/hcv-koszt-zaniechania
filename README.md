# HCV w Polsce – czy inwestycja w testowanie i leczenie się zwraca?

Edukacyjny model farmakoekonomiczny WZW typu C (HCV) w Polsce. Pokazuje, czy i kiedy dodatkowe wydatki publiczne na testowanie i leczenie HCV zwracają się państwu (NFZ, ZUS, KRUS, budżet), z 95% przedziałami niepewności. Pokazuje też wariant, w którym testy finansuje inny płatnik (koszt wyleczenia vs koszt nieleczenia) – koszt testów nie znika wtedy z budżetu publicznego, tylko przechodzi do innego płatnika.

**Wszystkie wyniki to szacunki modelu, nie dane obserwowane.** Materiał ma charakter edukacyjny, jest neutralny i nie jest reklamą żadnego produktu leczniczego. Nie zawiera nazw leków ani firm.

## Deklaracja finansowania i konfliktu interesów
Autor pracuje w sektorze farmaceutycznym. Analiza powstała prywatnie, bez zlecenia i finansowania jakiejkolwiek firmy. Nie wymienia ani nie promuje żadnych produktów leczniczych. Część wykorzystanych źródeł była finansowana przez przemysł — oznaczono to w Źródłach.

## Zawartość
- `index.html` – jedna aplikacja (jeden plik, działa offline), cztery grupy sekcji:
  - **Odpowiedź**: wynik, kalkulator, scenariusze;
  - **Problem i rynek**: kaskada opieki i hipotezy, regiony, leki i zamówienia publiczne (bez nazw leków i firm);
  - **Działania**: TOP 3, inicjatywy, ocena działań systemowych, wzór dla samorządów;
  - **Metoda i źródła**: założenia, przewodnik „Jak czytać”, metodologia z deklaracją, sprawdzenie (symulowana recenzja i audyt), źródła, aneks.
- `pobierz/hcv_model_inwestycji.xlsx` – model z formułami (bez makr), z przeliczonymi wartościami; arkusze dla scenariuszy S0, I1, I2, I3, I4, I5, V1.
- `pobierz/parametry.csv` – 114 parametrów, każdy ze źródłem, datą i typem (dane PL / zagraniczne / założenie).
- `SPEC_panel_6_rol.md` – specyfikacja i **symulowana** recenzja sześciu ról (np. płatnik, ZUS, klinicysta). Role zostały odegrane przez autora narzędzia; żadna realna osoba ani instytucja nie recenzowała ani nie zatwierdzała tej aplikacji.

## Metoda w skrócie
Model Markowa z otwartą kohortą (2026–2075, grupy wieku, korekta połowy cyklu), wyniki główne dla wartości bazowych założeń, probabilistyczna analiza wrażliwości (Monte Carlo, 2000 losowań), perspektywy płatnika zgodne z wytycznymi AOTMiT, dyskontowanie 5% / 3,5%. Koszt QALY porównujemy z progiem 244 821 zł w perspektywie NFZ (płatnika); perspektywa sektora publicznego pokazana osobno. Szczegóły i ograniczenia: zakładka „Metodologia” w aplikacji.

## Źródła
Dane publiczne: NFZ (statystyki programu lekowego B.71, Informator o terminach leczenia), NIZP PZH-PIB (EPIMELD), GUS, ZUS, AOTMiT, literatura recenzowana. Pełna lista ze źródłem i datą każdej liczby: zakładka „Źródła” oraz `pobierz/parametry.csv`. Stan danych: 28.10.2026.

## Audyt 3 – 28.10.2026 (symulowany)
Trzeci audyt (role analityka danych i researchera źródeł odegrane przez asystenta AI – nie realni eksperci; ocena przed poprawkami 6,5/10, B−): 2 ustalenia krytyczne, 6 istotnych, 11 drobnych. Wszystkie wprowadzone albo opisane jako ograniczenie. Część wyników się poprawiła, część pogorszyła – pokazujemy je bez wybierania. Wszystkie liczby to szacunek modelu.

| Wynik | Po audycie 2 | Po audycie 3 |
|---|---|---|
| Koszt zaniechania (S0), 20 lat, sektor publiczny (bazowo) | 1 036 mln zł | 1 129 mln zł |
| S0, 20 lat – bez zasiłków chorobowych (ekstrapolacja absencji) | 180 mln zł | 273 mln zł |
| S0, 50 lat (bazowo) | 6 034 mln zł | 6 353 mln zł |
| S0, 50 lat – bez zasiłków chorobowych | 3 761 mln zł | 4 080 mln zł |
| S0 dla NFZ: 10 / 20 / 30 lat | −629 mln zł (taniej) w 10 lat | −629 / −145 / +713 mln zł |
| Pakiet WHO (I4), saldo 20 lat (bazowo) | +2 408 mln zł | +2 439 mln zł |
| I4, saldo 20 lat – Monte Carlo mediana [95%] | 2 707 [2 281–3 293] | 2 446 [2 117–2 774] |
| I4, wydatek NFZ w 5 lat: bazowo / MC | 1 629 / 1 972 [1 641–2 501] mln zł | 1 742 / 1 735 [1 561–1 959] mln zł |
| I4, koszt QALY 20 lat – NFZ / publiczny | 82 294 / 77 717 zł | 72 483 / 66 049 zł |
| POZ (I2), koszt QALY 20 lat – NFZ; szansa < progu | 165 038 zł; 99% | 165 038 zł; 91% |
| Samo leczenie (V1), rok zwrotu (publiczny) | 2059 | 2056 |
| Koszty ZUS przypisane HCV, 2026 | 27,4 mln zł | 43,8 mln zł |

Najważniejsze zmiany: rozkłady Monte Carlo wyśrodkowane na wartościach bazowych (K1); koszt zaniechania bez ekstrapolowanych zasiłków pokazany obok wyniku głównego (K2); udziały HCV rekalibrowane w każdym losowaniu (I1); odsetek rozpoczynających leczenie w pakiecie 69,45% – środek 57,4–81,5% (I2); udział HCV w marskości K74 37,2% – bez marskości alkoholowej (I3); scenariusz POZ 0,26% (I4). Egipt 91,8% wyliczony z pełnego tekstu (1 054 695 / 1 148 346), nieużywany; zgony B18 = 88 nadal niezweryfikowane. Próg 244 821 zł/QALY: stan 28.10.2026 – nowe obwieszczenie GUS jeszcze nie opublikowane. Rozkład zmian krok po kroku: zakładka „Jak to zostało sprawdzone” → „Audyt 3”.

## Audyt 2 – 28.10.2026 (symulowany)
Drugi audyt (role analityka danych i researchera źródeł odegrane przez asystenta AI – nie realni eksperci): 2 ustalenia krytyczne, 9 ważnych, 18 drobnych. Wszystkie wprowadzone albo opisane jako ograniczenie. **Część wyników się pogorszyła i pokazujemy je bez zmian.** Wszystkie liczby to szacunek modelu (wartości bazowe).

| Wynik (wartości bazowe) | Przed audytem 2 | Po audycie 2 |
|---|---|---|
| Koszt zaniechania (S0), 50 lat, sektor publiczny | 8 336 mln zł | 6 034 mln zł |
| Koszt zaniechania (S0), 20 lat | 2 001 mln zł | 1 036 mln zł |
| Pakiet WHO (I4), saldo 20 lat, sektor publiczny | +2 987 mln zł (koszt) | +2 408 mln zł (koszt) |
| Pakiet WHO, koszt QALY 20 lat – NFZ (porównywany z progiem) | 58 483 zł | 82 294 zł |
| Pakiet WHO, koszt QALY 20 lat – sektor publiczny | 52 157 zł | 77 717 zł |
| Testowanie w szpitalach (I1), koszt QALY 20 lat – NFZ | 48 298 zł | 67 446 zł |
| Testowanie w POZ (I2), koszt QALY 20 lat – NFZ | 166 173 zł | 165 038 zł |
| Populacje kluczowe (I3), koszt QALY 20 lat – NFZ | 22 260 zł | 20 463 zł |

Najważniejsze zmiany: zasiłek chorobowy liczony jako dni × 80% stawki tylko u pracujących (K-A); tabela krok po kroku zamiast mieszania wyników (K-B); koszt QALY w perspektywie NFZ (W1); kalibracja oddzielona od walidacji (W2); wydajność testów w POZ 0,47% jako scenariusz (W3); 1,2% opisane jako laboratoria w kampanii (W4); przejście do leczenia 57,4% (W5); udział HCV w marskości 20,4% (W6); przejście F3→rak wątroby (W7); brak zaległej puli w status quo (W8); scenariusz wolniejszej progresji (W9). Egipt 91,8% i zgony B18 = 88 oznaczone jako niezweryfikowane. Rozkład zmian krok po kroku: zakładka „Jak to zostało sprawdzone” → „Audyt 2”.

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
- D1–D12: p90 kolejki 567/585 dni; Rosińska i in. 2015 (dane 2004–05); RE_KEY 6,2/100 osobolat; korekta połowy cyklu; SMR 10 dla PWID (symetrycznie; od audytu 2: SMR 14,68, Mathers 2013); SVR 0,97; uwaga o niespójności p_SCCHCC; koszt 1. roku po przeszczepie 30 167,61 zł (×CPI); uwagi o reinfekcji i użytecznościach; scenariusz malejącej zapadalności; 38 zamawiających; kalkulator 300 vs 2 000 losowań i kolejność kwantyli roku zwrotu.
- Nowe: wariant „testy finansuje inny płatnik” (porównanie samego kosztu wyleczenia z kosztami nieleczenia) oraz wynik na jednego zdiagnozowanego pacjenta.
- Model z wersji v1 (pe_model) jest zastąpiony przez silnik aplikacji i nie jest publikowany.
- Dodatkowo: w pliku xlsx usunięto kolizję nazw zakresów (stopa dyskonta kosztów i efektów) – po poprawce wartości w arkuszu zgadzają się ze stroną.
- Deklaracja finansowania i konfliktu interesów (CHEERS 2022) – w stopce, na ekranie Wynik, w Metodologii, w arkuszu xlsx i w README; źródła finansowane przez przemysł oznaczone w Źródłach.
- Jedna aplikacja (28.10.2026): cała treść wcześniejszych roboczych stron (raport, model v1, audyt) przeniesiona do aplikacji – hipotezy, zakładka „Leki i zamówienia publiczne”, ocena działań A1–A9, przebieg audytu; pogrupowana nawigacja. Treści o charakterze komercyjnym nie zostały przeniesione.
- Inwentarz danych (28.10.2026): przywrócono pominięte dane publiczne z wcześniejszych wersji (m.in. 0,47% z wiremią – PLoS One 2017; trend rozpoznań i leczenia wobec 2019 r.; dane programu Moje Zdrowie z IV 2026; EUDA 2024; UKHSA 2025; interpretacja luk wojewódzkich; dodatkowe ograniczenie modelu; pełna tabela weryfikacji 33 parametrów). Wyniki modelu bez zmian.
- Audyt 2 i audyt 3 (28.10.2026, symulowane): zob. sekcje „Audyt 3” i „Audyt 2” powyżej oraz zakładkę „Aneks – lista zmian” w aplikacji.

Poprzednia wersja (27.10.2026) jest dostępna w historii repozytorium; jej wyniki są nieaktualne.

## Licencja
Treść, dane pochodne i model: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.pl). Dane źródłowe pozostają na licencjach ich wydawców.
