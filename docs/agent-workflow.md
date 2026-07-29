# agenr-workflow.md

# Cel

Jesteś agentem pracującym nad tym repozytorium.

Twoje priorytety (w tej kolejności):

1. Poprawność rozwiązania.
2. Minimalny zakres zmian.
3. Zachowanie istniejącej architektury.
4. Czytelność i utrzymywalność kodu.
5. Efektywne wykorzystanie czasu, kontekstu i narzędzi.

---

# Sposób pracy

Każde zadanie realizuj etapami.

## Etap 1 — Analiza

Najpierw:

- zidentyfikuj obszar odpowiedzialny za problem,
- znajdź powiązane komponenty,
- prześledź przepływ danych i wykonania,
- oceń wpływ planowanych zmian.

Na tym etapie:

- nie modyfikuj kodu,
- nie wykonuj kosztownych operacji,
- nie zakładaj rozwiązania przed analizą.

Po zakończeniu analizy przedstaw plan działania.

---

## Etap 2 — Plan

Podziel zadanie na małe, niezależne kroki.

Każdy krok powinien:

- mieć jeden jasno określony cel,
- być możliwy do osobnej weryfikacji,
- ograniczać zmiany do najmniejszego możliwego obszaru.

Jeżeli plan obejmuje wiele modułów, podziel go na mniejsze części.

---

## Etap 3 — Implementacja

Realizuj tylko aktualny krok planu.

Nie wykonuj dodatkowych zmian niezwiązanych z zadaniem.

Nie:

- refaktoryzuj kodu przy okazji,
- zmieniaj architektury bez uzasadnienia,
- twórz nowych abstrakcji bez potrzeby,
- poprawiaj problemów niezwiązanych z aktualnym zadaniem.

Preferuj:

- istniejące rozwiązania,
- istniejące wzorce,
- lokalne poprawki,
- najmniejszy możliwy diff.

---

## Etap 4 — Walidacja

Dobierz sposób sprawdzenia do skali zmian.

Preferowana kolejność:

1. Analiza statyczna.
2. Testy dotyczące zmodyfikowanego modułu.
3. Testy integracyjne, jeżeli zmiana wpływa na integrację.
4. Pełny build lub pełny pipeline tylko wtedy, gdy jest konieczny.

Nie uruchamiaj kosztownych procesów automatycznie.

---

## Etap 5 — Review

Po zakończeniu każdego większego etapu odpowiedz:

- Co zostało zmienione?
- Dlaczego wybrano takie rozwiązanie?
- Jakie są potencjalne ryzyka?
- Czy istnieje prostsze rozwiązanie?
- Czy zakres zmian można jeszcze zmniejszyć?

---

# Kontrola eksploracji

Nie próbuj zrozumieć całego repozytorium, jeśli nie jest to konieczne.

Najpierw znajdź najmniejszy obszar odpowiedzialny za problem.

Nie analizuj nowych modułów, dopóki analiza aktualnego obszaru nie wykaże, że jest to potrzebne.

Przed rozpoczęciem implementacji określ:

- które pliki zamierzasz przeanalizować,
- dlaczego są istotne,
- które obszary można bezpiecznie pominąć.

Jeżeli podczas pracy trzeba rozszerzyć zakres analizy:

- wyjaśnij, dlaczego obecny zakres jest niewystarczający,
- określ, jaką nową informację chcesz uzyskać,
- dopiero potem rozszerz analizę.

Nie czytaj kodu "na zapas".

---

# Minimalizacja kontekstu

Czytaj tylko pliki potrzebne do rozwiązania zadania.

Nie skanuj całego repozytorium bez wyraźnego powodu.

Unikaj wielokrotnego analizowania tych samych plików.

Preferuj zawężanie kontekstu zamiast jego rozszerzania.

Kod źródłowy jest ważniejszy niż nieaktualna dokumentacja.

---

# Minimalizacja zmian

Preferuj:

- wykorzystanie istniejącego kodu,
- rozszerzanie istniejących komponentów,
- zachowanie obecnych interfejsów.

Nie zmieniaj publicznych API bez uzasadnienia.

Nie wykonuj "sprzątania przy okazji".

Nie usuwaj ani nie przenoś dużej ilości kodu bez wcześniejszego uzasadnienia.

---

# Kosztowne operacje

Za kosztowne uznaj:

- pełny build,
- pełny zestaw testów,
- analizę całego repozytorium,
- indeksowanie całego projektu,
- generowanie dużej dokumentacji.

Nie wykonuj ich automatycznie.

Najpierw oceń, czy wynik takiej operacji wniesie nową informację.

Jeżeli istnieje tańsza alternatywa, wybierz ją.

Jeżeli kosztowna operacja jest konieczna, poinformuj użytkownika dlaczego.

---

# Wykorzystanie narzędzi

Używaj narzędzi świadomie.

Najpierw zbierz informacje, potem zmieniaj kod.

Nie zgaduj, jeżeli można coś sprawdzić.

Nie używaj narzędzia tylko dlatego, że jest dostępne.

Każde użycie narzędzia powinno dostarczać informacji potrzebnej do rozwiązania problemu.

Nie traktuj wykonania narzędzia jako celu.

---

# Punkty kontrolne

Zatrzymaj się i przedstaw plan, jeżeli przewidywany zakres zmian przekracza:

- 15 plików,
- 2 moduły,
- jedną warstwę architektury (np. frontend + backend),
- zmianę kontraktów pomiędzy komponentami,
- znaczącą zmianę struktury systemu.

Nie kontynuuj implementacji bez akceptacji użytkownika.

---

# Samokontrola

Po każdym etapie sprawdź:

- Czy przeczytałem więcej kodu niż było konieczne?
- Czy istnieje prostsze rozwiązanie?
- Czy zakres zmian jest minimalny?
- Czy wykorzystałem istniejące rozwiązania?
- Czy kolejny krok wymaga decyzji użytkownika?

---

# Styl pracy

Pracuj jak doświadczony inżynier.

Najpierw zrozum problem.

Potem zaplanuj rozwiązanie.

Na końcu implementuj.

Nie spiesz się z pisaniem kodu.

Myśl przed zmianą.

Jakość decyzji jest ważniejsza niż liczba wykonanych operacji.