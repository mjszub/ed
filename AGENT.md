# AGENTS.md

## Priorytety

Pracuj według kolejności:

1. Poprawność.
2. Minimalny zakres zmian.
3. Zachowanie istniejącej architektury.
4. Efektywne użycie czasu i narzędzi.

---

## Sposób pracy

Każde zadanie wykonuj etapami:

1. Analiza:
   - znajdź właściwy obszar kodu,
   - zrozum istniejący przepływ,
   - nie zmieniaj jeszcze kodu.

2. Plan:
   - podziel pracę na małe kroki,
   - wskaż pliki i komponenty, które będą zmieniane.

3. Implementacja:
   - wykonuj jeden krok naraz,
   - nie dodawaj zmian niezwiązanych z zadaniem.

4. Walidacja:
   - uruchamiaj najpierw najtańsze i najbardziej lokalne testy,
   - pełny build/pipeline tylko gdy jest potrzebny.

---

## Kontrola zakresu

Nie próbuj analizować całego repozytorium.

Najpierw znajdź najmniejszy obszar odpowiedzialny za problem.

Nie czytaj kodu "na zapas".

Jeżeli potrzebujesz rozszerzyć analizę poza obecny obszar, wyjaśnij dlaczego.

---

## Minimalne zmiany

Preferuj:

- istniejący kod,
- istniejące wzorce,
- lokalne poprawki.

Nie wykonuj refaktoringu przy okazji.

Nie twórz nowych abstrakcji bez potrzeby.

Nie zmieniaj publicznych interfejsów bez uzasadnienia.

---

## Kosztowne operacje

Nie wykonuj automatycznie:

- pełnego builda,
- pełnego zestawu testów,
- analizy całego repozytorium.

Najpierw oceń, czy wynik wniesie nową informację.

---

## Punkty zatrzymania

Zatrzymaj się i przedstaw plan, jeśli:

- zmiany obejmują więcej niż 15 plików,
- dotyczą więcej niż 2 modułów,
- zmieniają architekturę,
- zmieniają kontrakty między komponentami.

---

## Review

Po zakończeniu sprawdź:

- Czy rozwiązanie jest minimalne?
- Czy istnieje prostsza droga?
- Jakie są ryzyka?
- Czy kolejny krok wymaga decyzji użytkownika?