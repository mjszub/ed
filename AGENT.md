# AGENTS.md

## Workflow

Szczegółowy proces pracy znajduje się w:

docs/agents-workflow.md

Używaj go jako rozszerzenia procesu przy:
- dużych zadaniach,
- zmianach wieloetapowych,
- pracach obejmujących wiele modułów,
- zmianach architektury.

---

## Priorytety

1. Poprawność ponad szybkość.
2. Minimalny zakres zmian.
3. Wykorzystuj istniejący kod przed tworzeniem nowego.
4. Zachowuj istniejącą architekturę.
5. Efektywnie używaj czasu i narzędzi.

---

## Zanim zmienisz kod

- Zrozum problem.
- Znajdź odpowiedzialny obszar.
- Sprawdź istniejące wzorce.
- Przygotuj plan.

Nie implementuj rozwiązania zanim nie rozumiesz kontekstu.

---

## Podczas implementacji

- Wykonuj małe kroki.
- Zmieniaj tylko wymagany zakres.
- Nie wykonuj refaktoringu przy okazji.
- Nie twórz nowych abstrakcji bez potrzeby.
- Nie zmieniaj publicznych interfejsów bez uzasadnienia.

---

## Kontrola kontekstu

Nie analizuj całego repozytorium bez potrzeby.

Najpierw znajdź najmniejszy obszar odpowiedzialny za problem.

Nie czytaj kodu "na zapas".

Jeżeli musisz rozszerzyć zakres analizy, wyjaśnij dlaczego.

---

## Narzędzia

Nie uruchamiaj narzędzi tylko dlatego, że są dostępne.

Każda operacja powinna dostarczyć informacji potrzebnej do rozwiązania problemu.

---

## Skills

Przed rozpoczęciem pracy oceń, czy zadanie pasuje do któregoś ze skills.

Użyj odpowiedniego skilla dla:
- bugfix,
- feature,
- refactor,
- large-change,
- performance,
- security review,
- dependency upgrade.

---

## Kosztowne operacje

Nie uruchamiaj automatycznie:

- pełnego builda,
- pełnych testów,
- długich pipeline'ów.

Najpierw oceń, czy wynik wniesie nową informację.

---

## Zatrzymanie

Poproś użytkownika o decyzję, gdy:

- zmiana obejmuje wiele modułów,
- zmienia architekturę,
- wymaga dużej migracji,
- wymagania są niejasne.

---

## Po zmianach

Sprawdź:

- Czy rozwiązanie jest minimalne?
- Czy istnieje prostsza droga?
- Jakie są ryzyka?