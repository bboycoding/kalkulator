# Analiza materiałów i wymagania

## Źródła

- **Z**: `Podstawy C++_Założenia do Projektu 1d.pdf`, 6 stron, rok 2025/26. Najważniejsze źródło kryteriów i organizacji.
- **P**: `Podstawy C++_Projekt 1c.pdf`, 8 stron, rok 2022. Materiał pomocniczy, przykładowy kod i prezentacja działania.
- Oba pliki zastrzegają zakaz publicznego udostępniania bez pisemnej zgody autora lub uczelni. Nie publikować oryginałów w publicznym repozytorium bez zgody.

## Cel i zakres ocen

- Konsolowy kalkulator C++, korzystający z pseudografiki opartej na tabeli kodów znaków; materiały wskazują Code::Blocks 20.03 [Z s. 3].
- Na **3**: dodawanie, odejmowanie, mnożenie i dzielenie [Z s. 3]. Przykładowy interfejs ma nagłówek z nazwiskami, semestrem i grupą oraz podawanie danych, działania i wyniku [Z s. 5].
- Na **5**: powyższe oraz potęgowanie, pierwiastkowanie, obliczanie π i e, interfejs oparty na tabeli kodów oraz większa funkcjonalność, stabilniejszy i bardziej efektowny interfejs niż na 4 [Z s. 3, 6]. Dokument nie określa zamkniętej listy cech spełniających ostatni warunek, więc nie można zagwarantować oceny na podstawie checklisty.
- Zapis mówi również o wykonywaniu działań na obliczonych stałych, nie tylko ich wyświetleniu [Z s. 3; P s. 1]. Sposób wyboru stałych jako argumentów zaprojektować i potwierdzić.
- Przykładowa tabela wyników zawiera silnię x! [Z s. 6], ale lista działań na 5 na s. 3 nie wymienia jej wprost. Warto uwzględnić lub zapytać prowadzącego; nie przedstawiać jako jednoznacznego kryterium.
- Interfejs na 4 pokazano przykładowo [Z s. 5–6], ale brak kompletnego formalnego wykazu funkcji na 4.

## Organizacja i oddanie

- Zespół 4 lub 5 osób, wybór lidera; lider w porozumieniu z członkami wypełnia tabelę projektu [Z s. 1]. Nasz zespół: cztery osoby; nazwiska i lider do ustalenia.
- Formularz obejmuje dane lidera, tytuł, skład z numerami indeksów, opis, grupę docelową, co najmniej trzy cele, formę wdrożenia, plan i terminy, narzędzia, mocne i słabe strony, zagrożenia oraz podział pracy [Z s. 2–3].
- Przesłanie na Platformę Zdalną najpóźniej na przedostatnich zajęciach, prezentacja na ostatnich zajęciach; dat kalendarzowych materiały nie podają [Z s. 1]. Potwierdzić daty i dokładny zestaw plików.
- Prezentacja PowerPoint około 15–20 slajdów, opis funkcjonalności i interfejsu, kody źródłowe, kilka zrzutów ekranu [Z s. 1].

## Pseudografika i kodowanie

Tabela w [Z s. 4] nazywa 256 znaków ASCII, ale ścisłe ASCII ma 128 kodów 0–127; znaki ramek z przykładów należą do rozszerzonej strony kodowej, w szczególności zestawu zgodnego z CP437. Przykład [P s. 4–7] wykorzystuje m.in. 201 ╔, 187 ╗, 200 ╚, 188 ╝, 205 ═, 186 ║. Wygląd zależy od kodowania konsoli i czcionki. Należy sprawdzić wyświetlanie w docelowym Code::Blocks/Windows i ustalić z prowadzącym akceptowalny wariant. Nie zakładać, że wypisanie bajtów powyżej 127 działa w UTF-8.

Ramka to znaki wypisywane wiersz po wierszu, menu i wyniki to zwykły tekst; nie wymaga okienkowego GUI. Przykładowa tabela wyników jest w [Z s. 5–6]. Konkretny układ jest decyzją projektową, lecz wymóg atrakcyjniejszego, stabilnego interfejsu jest jakościowy.

## Stałe — wymagane wzory i kontrola

[Z s. 4] pokazuje szereg bazylejski `π²/6 = suma(1/k²), k=1..∞` oraz dla e szereg `e = suma(1/k!), k=0..∞` i alternatywną granicę `(1+1/n)^n`. Przykładowa implementacja [P s. 5] korzysta z szeregów; należy obliczać, a nie podstawiać gotowe wartości stałych.

- π: sumuj `1.0/(double(k)*k)` dla k=1..N, następnie `sqrt(6*suma)`; np. N=1 000 000, typ `double`. Rzutowanie przed mnożeniem chroni przed przepełnieniem typu całkowitego. Obliczenie pomocnicze zwróciło 3.1415916986604673, po zaokrągleniu 3.14159. Dla N=9999 uzyskano ok. 3.14149715, czyli 3.14150: za mało do pięciu miejsc. W kodzie P pętla dla argumentu 9999 obejmuje 1..9998, a nie 1..9999; użyto też `float`, co dodatkowo pogarsza dokładność.
- e: `suma=1`, `wyraz=1`; dla k=1..15 wykonaj `wyraz /= k; suma += wyraz`. To kolejne 1/k! bez przepełnienia całkowitej silni. Wynik pomocniczy: 2.718281828458995, po zaokrągleniu 2.71828.
- Użyj `std::fixed << std::setprecision(5)` z `<iomanip>` dla prezentacji; samo formatowanie nie poprawia niedokładnych obliczeń. Sprawdź także błąd wartości wewnętrznej i pięć cyfr po zaokrągleniu w rzeczywistej kompilacji.
- Materiały błędnie podają e ≈ 2,7871 [Z s. 3; P s. 1]. Poprawne jest e ≈ 2,71828; sam przykład wyniku [P s. 8] pokazuje 2,71828. Zasygnalizować rozbieżność.
- Przykładowe `silnia` [P s. 5] niepoprawnie obsługuje 0 i przepełnia typ przy odpowiednio dużych argumentach. Jeżeli dodamy opcję silni, zaprojektować osobną kontrolę dziedziny i zakresu.

## Pytania do prowadzącego

1. Czy wynik projektu wymaga silni jako osobnego działania i jak dokładnie mają działać operacje na π/e?
2. Jakie funkcje i elementy wystarczą dla jakościowego kryterium stabilności i efektowności na 5? Czy ramki zgodne z CP437 i wariant zastępczy ASCII są dopuszczalne?
3. Czy konieczna jest dokładnie wersja Code::Blocks 20.03, format projektu `.cbp`, określony kompilator i konkretny standard C++?
4. Jakie pliki, poza prezentacją, należy przesłać, czy wymagany jest formularz i gdzie? Jakie są dokładne daty?
5. Czy dozwolone są nowe wersje narzędzi i prezentowanie źródeł na kilku slajdach zamiast pełnego kodu na slajdach?
