# Specyfikacja aplikacji „HCV: ile kosztuje zaniechanie i kiedy zwraca się inwestycja”
## Symulowany panel 6 ról – recenzja przed budową UI, synteza wymagań, runda 2

> **To jest symulowana recenzja.** Sześć „recenzentów” to role odegrane przez autora narzędzia na podstawie publicznie znanych zadań tych instytucji i funkcji. Żadna realna osoba ani instytucja nie recenzowała, nie oceniała ani nie zatwierdzała tej aplikacji. Nie używamy nazwisk.

Stan danych: 27.10.2026. Wszystkie wyniki modelu są **szacunkami**.

---

## 1. Runda 1 – recenzja koncepcji (przed UI)

Recenzowany materiał: silnik modelu (Markov, otwarta kohorta, 2026–2075), parametry (93, każdy ze źródłem i datą), wyniki deterministyczne scenariuszy I1–I5, wcześniejsze analizy (kaskada „co jeśli”, model farmakoekonomiczny v1).

### 1.1 KOL / hepatolog
**Zakres.** Pytania: czy więcej testowania i leczenia zmniejszy liczbę DC, HCC, przeszczepów i zgonów; w jakim horyzoncie; czy model widzi reinfekcje i ryzyko HCC po SVR. Horyzont: dożywotni (≥50 lat), bo zdarzenia wątrobowe narastają powoli.
**Jakość i wiarygodność.** Główne zastrzeżenie: *w scenariuszu status quo model podwaja DC (1 590 → 4 536) i HCC (890 → 2 261) w 10 lat, a polski model Flisiak i in. 2015 przy ~5 000 leczonych/rok pokazuje liczby zbliżone do stałych.* Prawdopodobieństwa CC→DC/HCC z literatury międzynarodowej (tabela analizy AOTMiT) zawyżają zdarzenia w polskich warunkach. Wymaga: kalibracji, tabeli walidacji zewnętrznej, porównania z opublikowanymi modelami, jawnego braku: nadmiarowej śmiertelności PWID, efektu „leczenie jako prewencja”, manifestacji pozawątrobowych.
**Forma.** W 30 s: zdarzenia uniknięte (DC, HCC, LT, zgony) z 95% CI, nie tylko złotówki. Szczegóły: pełna tabela przejść.

### 1.2 NFZ (płatnik)
**Zakres.** Wpływ na budżet NFZ w 5 latach (BIA, bez dyskonta, rok po roku), perspektywa płatnika publicznego (AOTMiT), koszt na dodatkowo leczonego, koszt wykrycia przypadku. Pytanie: „ile dopłacę i w którym roku”.
**Jakość.** Efektywna cena DAA nie jest znana (instrumenty dzielenia ryzyka) – wymaga analizy wrażliwości ceny w obie strony. Koszty stanów z wyceny 2012/2016 – ryzyko niedoszacowania. Nie wolno mieszać transferów ZUS z kosztami NFZ. Liczby pacjentów nie mogą być sumowane między latami.
**Forma.** W 30 s: roczne saldo NFZ na 5 lat i rok zwrotu w perspektywie NFZ. Eksport xlsx z formułami.

### 1.3 Minister Zdrowia
**Zakres.** Czy pakiet eliminacyjny WHO jest wykonalny i opłacalny do 2030/2035; ilu zgonów unikniemy; który instrument (POZ, szpitale/laboratoria, populacje kluczowe) daje najwięcej na złotówkę. Perspektywa sektora publicznego (NFZ + budżet + ZUS/KRUS + utracone wpływy).
**Jakość.** Zgodność z wytycznymi AOTMiT (perspektywy, dyskonto 5%/3,5%, próg 3×PKB/QALY), przejrzystość, jasne oddzielenie danych od założeń.
**Forma.** W 30 s: jedno zdanie odpowiedzi + 3 liczby; język decyzyjny, bez żargonu; wersja do druku.

### 1.4 Konsultant Krajowy ds. chorób zakaźnych
**Zakres.** Wykonalność kadrowa: ile osób rocznie mogą leczyć ośrodki; kolejki (Informator NFZ); utrata pacjentów między testem a poradnią (linkage); populacje kluczowe, więzienia, OST.
**Jakość.** Model zakłada, że budżet w pełni „pracuje” od pierwszego roku – nierealne. Potrzebny okres dochodzenia do skali i sygnał, gdy leczonych jest więcej niż kiedykolwiek obserwowano (8 521 w 2019 r.). Linkage w Polsce: brak danych – musi być parametrem z zakresem.
**Forma.** Mapa regionów, kolejki, ścieżka pacjenta; działania z pierwszym krokiem na 30 dni i miernikami z wartością bazową.

### 1.5 GM firmy farmaceutycznej (bez nazw firm)
**Zakres.** Jak cena leków DAA i umowy wolumenowe zmieniają zwrot; czy przy niższej cenie jednostkowej i wyższym wolumenie płatnik wychodzi na plus.
**Jakość.** Uczciwa niepewność ceny (od ceny z danych NFZ do najwyższej ceny urzędowej). Neutralność: żadnych nazw leków i firm, inaczej materiał traci wiarygodność i łamie art. 57 Prawa farmaceutycznego i Kodeks INFARMA.
**Forma.** Suwak ceny DAA w kalkulatorze, wykres tornado, eksport parametrów CSV.

### 1.6 ZUS
**Zakres.** Absencja chorobowa, renty z tytułu niezdolności do pracy, KRUS, utracone składki; w podziale na płatników.
**Jakość.** Dane ZUS o kosztach według ICD są z 2012 r. – wymagają przeliczenia i jawnego oznaczenia; świadczenia ZUS to transfery (nie wchodzą do perspektywy społecznej, tylko do sektora publicznego). Walidacja: koszt ZUS z modelu vs przeliczenie top-down.
**Forma.** Osobna kolumna ZUS w tabeli płatników; „brak danych” tam, gdzie go brak.

---

## 2. Synteza

### 2.1 Wymagania konsensusowe (wszystkie role)
1. Odpowiedź na jedno pytanie na górze: „czy dodatkowa złotówka na testowanie + leczenie wraca do państwa i kiedy” – **uczciwie**, także gdy nie wraca.
2. Każdy wynik: szacunek, 95% CI z Monte Carlo (2 000 losowań), rok zwrotu, ROI, saldo skumulowane w czasie.
3. Każdy parametr: źródło, data, typ (dane / literatura / założenie / kalibracja); zagraniczne oznaczone.
4. Zgodność z AOTMiT (perspektywy, dyskonto, próg) i CHEERS 2022; sekcja „Jak to zostało sprawdzone”.
5. Neutralność: bez firm, leków z nazwy, logotypów; język edukacyjny.
6. Eksport: xlsx z formułami, CSV parametrów.
7. Mobile-first, ciemny/jasny motyw, dostępność.

### 2.2 Konflikty i rozstrzygnięcia

| # | Konflikt | Rozstrzygnięcie | Uzasadnienie |
|---|---|---|---|
| K1 | NFZ: perspektywa NFZ i 5 lat vs MZ/ZUS: sektor publiczny i długi horyzont vs KOL: dożywotni | Domyślnie **sektor publiczny, 20 lat**; przełączniki NFZ / publiczny / społeczny i 5/10/20/50 lat; osobna tabela BIA NFZ 5 lat bez dyskonta | 20 lat obejmuje większość zdarzeń wątrobowych i jest bliżej horyzontu decyzji niż 50; nic nie jest ukryte |
| K2 | MZ chce „dowodu oszczędności” vs KOL/NFZ: rzetelność | Pokazujemy wynik taki, jaki jest: większość scenariuszy **nie** zwraca się w 10 lat; zwrot zależy od celowania; równolegle koszt-efektywność (ICER vs próg) | Zasada uczciwości; decyzje zdrowotne w PL opierają się na ICER, nie na samym zwrocie |
| K3 | GM: niższa cena DAA za wolumen vs NFZ: cena efektywna nieznana | Suwak ceny DAA (od 30% do 430% bazowej) + tornado; baza = wartość refundacji / pacjent z danych NFZ 2025 | Cena jest największym źródłem niepewności |
| K4 | Konsultant: wykonalność vs MZ: pakiet WHO od razu | Okres dochodzenia do skali (RAMP = 3 lata, zakres 1–5) i ostrzeżenie, gdy leczeni > 8 521/rok | Realizm kadrowy; obserwowane maksimum B.71 |
| K5 | KOL: prawdopodobieństwa z literatury vs kalibracja do PL | **Kalibracja** mnożnikami K_DC = 0,333 i K_HCC = 0,413 (status quo odtwarza DC/HCC 2030 z modelu Flisiak 2015); PSA losuje K między kalibracją a 1 (brak kalibracji) | Konserwatywne dla oszczędności; niepewność strukturalna w CI |
| K6 | ZUS: pełne koszty ZUS vs ekonomia: transfery | ZUS w sektorze publicznym, wyłączony z perspektywy społecznej; osobna kolumna | Zgodne z teorią ekonomii zdrowia i AOTMiT |
| K7 | Ilość treści (raport, 12 pomysłów, opcje, rynek) vs 30-sekundowy odbiór | Kolejność: Wynik → Kalkulator → Scenariusze → Problem i kaskada → Regiony → Działania → Metodologia → Jak sprawdzone → Źródła → **Aneks** (rynek w agregatach, listy opcji, hipotezy, stare wyniki) | Treści o niskiej wartości dla decyzji nie są usuwane, tylko przesunięte |
| K8 | Rola branży vs neutralność | Opcje „pozycja firmy” przeniesione do aneksu w formie neutralnej (narzędzia monitorowania danych publicznych); bez taktyki przetargowej | Strona edukacyjna, nie reklama |

### 2.3 Poprawki modelu wynikające z rundy 1
1. **Kalibracja DC/HCC** (KOL) – patrz K5; tabela walidacji zewnętrznej w aplikacji.
2. **Okres dochodzenia programu do skali** (Konsultant) – RAMP.
3. **Scenariusz walidacyjny V1** (KOL/NFZ): te same dodatkowe leczenia co I1, ale bez kosztu wykrywania – porównanie z opublikowanymi modelami „czas zwrotu leczenia”.
4. **BIA NFZ 5 lat** (NFZ) – rok po roku, bez dyskonta.
5. **Ostrzeżenie o przepustowości** (Konsultant/NFZ).
6. Jawne ograniczenia (KOL): brak efektu prewencji transmisji (konserwatywne), brak nadmiarowej śmiertelności PWID (zawyża korzyść I3), brak manifestacji pozawątrobowych (konserwatywne), koszty stanów z 2012/2016 (prawdopodobnie zaniżone → konserwatywne).

### 2.4 Specyfikacja aplikacji
- Jeden plik HTML, bez zależności, skill „projektowanie-stron” (szkło, ciemny/jasny, iPhone-first), wykresy SVG z alternatywą tabelaryczną.
- Nawigacja: zakładki (pasek dolny na iPhonie: Wynik, Kalkulator, Scenariusze, Założenia, Więcej; na desktopie wszystkie): **Wynik, Kalkulator, Scenariusze, Problem, Regiony, Działania, Założenia, Jak czytać, Metodologia, Sprawdzenie, Źródła, Aneks**.
- **Brak przełącznika ról i zakładki „Perspektywy”** – role istnieją wyłącznie jako opisany, symulowany panel w sekcji „Jak to zostało sprawdzone”.
- Kalkulator: suwaki – budżet testowania (szpitale/laboratoria, POZ, populacje kluczowe), dodatkowe kursy leczenia bez nowego testowania (0–10 000/rok), odsetek rozpoczynających leczenie, cena DAA dla dodatkowych pacjentów (7 000–98 000 zł; baza 22 760 zł), czas programu, horyzont, stopa dyskontowa, linkage; perspektywa; wynik deterministyczny + pasmo 95% z 300 losowań PSA liczonych w przeglądarce.
- Wszystkie liczby wynikowe opisane „szacunek modelu”.
- Pobieranie: xlsx (formuły, bez metadanych), CSV parametrów.

---

### 2.5 Zakładka „Założenia”
- Wszystkie 93 założenia jako karty w **7 grupach** (epidemiologia i kohorta; przebieg choroby i jakość życia; koszty NFZ – stany choroby; koszty ZUS, KRUS, podatki i produktywność; leczenie i testy; scenariusze programu; dyskonto, horyzont i próg).
- Każda karta: wartość bazowa i zakres min–max, *dlaczego*, metoda, źródło i data, typ danych (dane źródłowe / dane zagraniczne / prognoza z metodą / założenie scenariuszowe / brak danych PL), rozkład w losowaniach Monte Carlo, wpływ na wynik (miejsce w tornado, rozrzut salda) i „co gdyby było inaczej” (liczbowo dla pakietu WHO 50 lat i populacji kluczowych 20 lat; szacunek).
- Wyszukiwarka i filtr grup; każdy wynik w Wyniku, Kalkulatorze i Scenariuszach ma link „→ jak to policzono” do właściwego założenia lub sekcji przewodnika; wiersze tornado linkują do kart (#zal-ID).

### 2.6 Przewodnik „Jak czytać i interpretować wyniki”
- Pojęcia z przykładami liczbowymi z modelu: QALY, ICER i próg AOTMiT, ROI, rok zwrotu, BIA, koszt zaniechania, oszczędności netto (saldo).
- Niepewność: 95% przedział i Monte Carlo („losujemy tysiące wersji świata” – 2 000 losowań), prawdopodobieństwo zwrotu.
- Jak czytać każdy typ wykresu: krzywa salda z pasmem, trajektorie, tornado, CEAC, mapa, kaskada.
- Perspektywy (NFZ / sektor publiczny / społeczna) i horyzonty; dyskontowanie; szacunek vs dane źródłowe; czego model nie mówi; typowe błędy interpretacji (sumowanie pacjentów między latami, mylenie transferu z kosztem, odczytywanie mediany jako pewnika).
- **Ikona „i”** przy każdym wykresie, tabeli wynikowej i kafelku KPI (34 ikony): krótkie wyjaśnienie w okienku + link do sekcji przewodnika. Okienko zamyka Esc / klik obok; fokus wraca do ikony.

### 2.7 CEAC
- Krzywa akceptowalności dla I1–I4 i V1 (sektor publiczny, 20 lat; 2 000 losowań), oś pozioma liniowa w zł za QALY, pionowa linia przy progu AOTMiT 244 821 zł.

---

## 3. Runda 2 – ocena gotowej aplikacji (symulowana)

Ten sam symulowany panel ocenił zbudowaną aplikację (skala 1–10). Oceny zostały wygenerowane w symulacji; nie wystawiły ich realne osoby ani instytucje.

| Rola (symulowana) | Zakres | Jakość | Wiarygodność | Forma | Najważniejsza uwaga |
|---|---|---|---|---|---|
| Hepatolog (ekspert kliniczny) | 8 | 7 | 7 | 8 | Kalibracja do jednego polskiego modelu; brak efektu zapobiegania nowym zakażeniom i wyższej śmiertelności osób przyjmujących narkotyki. |
| Przedstawiciel NFZ | 8 | 7 | 7 | 7 | Cena efektywna leków DAA nie jest publiczna; wynik pakietu WHO zależy od niej najbardziej. |
| Minister Zdrowia (perspektywa polityki) | 9 | 8 | 8 | 8 | Brakowało przełożenia na zgony i koszt QALY – dodane do wyników. |
| Konsultant krajowy ds. chorób zakaźnych | 8 | 7 | 7 | 8 | Kolejki do poradni są opisane, ale nie modelowane jako ograniczenie przepustowości. |
| Dyrektor generalny firmy farmaceutycznej (bez nazw) | 7 | 8 | 8 | 8 | Umowa wolumenowa zmienia ekonomię – dodano osobną cenę kursu dla dodatkowych pacjentów. |
| Przedstawiciel ZUS | 7 | 7 | 6 | 7 | Koszty ZUS w modelu o 38% wyższe niż w rachunku odgórnym; wymaga weryfikacji na danych ZUS. |
| **Średnia** | **7,8** | **7,3** | **7,2** | **7,7** | |

### 3.1 Poprawki wprowadzone po rundzie 2
1. Kafelki zgonów i kosztu QALY w Wyniku i Kalkulatorze (MZ).
2. Osobna cena kursu DAA dla dodatkowych pacjentów + suwak dodatkowych kursów leczenia (GM, NFZ).
3. Tabela walidacji: koszt ZUS model vs rachunek odgórny (+38%), NFZ „brak danych”, zgony wątrobowe vs szacunki ekspertów (ZUS, KOL).
4. CEAC i prawdopodobieństwo zwrotu przy każdym scenariuszu (NFZ).
5. Ostrzeżenie o przepustowości (> 8 521 leczonych/rok) w kalkulatorze (Konsultant).
6. Złagodzone sformułowania: „mieści się poniżej progu AOTMiT” zamiast „tanio”; CHEERS „źródła finansowania” – „częściowo” (deklarację uzupełnić przed publikacją).
7. QA UI: brak przepełnień na iPhonie i desktopie (jasny/ciemny), czytelne tabele na telefonie (przedział w osobnej linii), liniowa oś CEAC, brak błędów konsoli.

### 3.2 Uwagi niezałatwione (luki)
- Brak modelu transmisji (efekt „leczenie jako prewencja”) – wynik konserwatywny.
- Kolejki do poradni nie są ograniczeniem w modelu – tylko ostrzeżenie.
- Efektywna cena DAA i dane NFZ o kosztach stanów – brak danych publicznych.
- Kalibracja do jednego modelu (Flisiak i in. 2015); brak realnych konsultacji z interesariuszami.
