# Kalkulator C++

Projekt zaliczeniowy AHE z Podstaw Programowania 1 realizowany przez cztery osoby. Docelowy zakres wymaga uzgodnienia.

## Stan projektu

Repozytorium zawiera szkielet programu, a nie gotowy kalkulator. Ustalenia znajdują się w `docs/KONTEKST.md`, analiza wymagań w `docs/WYMAGANIA.md`, plan pracy w `docs/PLAN.md`, a plan prezentacji w `docs/PREZENTACJA_PLAN.md`. Materiałów PDF nie wolno publicznie udostępniać bez pisemnej zgody autora lub AHE.

## Uruchomienie

Wytyczne wskazują Code::Blocks 20.03; projekt i kompilację w tym środowisku należy jeszcze przygotować i sprawdzić. CMake i C++17 są wstępnym szkieletem, nie wymogiem materiałów. W poprzednim sprawdzeniu konsoli nie wykryto kompilatora ani CMake. Aby zbudować obecny szkielet przy użyciu kompilatora C++17 i CMake 3.16+:

```bash
cmake -S . -B build
cmake --build build
```

Uruchom wygenerowany program `kalkulator` z katalogu `build` (jego dokładna lokalizacja zależy od systemu i generatora CMake).

## Współpraca

Pracuj na osobnej gałęzi dla każdego zadania i opisuj zmiany w commitach. Sposób integracji i przydział zadań ustalimy po poznaniu wymagań i możliwości zespołu.
