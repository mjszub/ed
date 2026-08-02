Strategia optymalizacji kosztów agentów AI: Codex, Claude Code i projektowanie harnessa

Cel

Celem jest zaprojektowanie środowiska pracy z agentami AI, które maksymalizuje stosunek:

jakość wykonania / koszt modeli / czas realizacji

Problem:

- najmocniejszy model daje najlepsze decyzje, ale jest kosztowny,
- słabszy model jest tani, ale może podejmować gorsze decyzje,
- współczesne harnessy agentowe pozwalają delegować pracę, ale dynamiczny routing inteligencji nadal jest ograniczony.

---

Czym jest harness?

Harness to warstwa sterująca wokół modelu AI.

Model odpowiada za:

- rozumowanie,
- generowanie kodu,
- analizę problemu.

Harness odpowiada za:

- kiedy uruchomić agenta,
- jakiego modelu użyć,
- jakie narzędzia udostępnić,
- ile kontekstu przekazać,
- kiedy delegować zadanie,
- kiedy eskalować problem.

Można traktować harness jak managera zespołu programistów.

Model = programista.

Harness = lider techniczny organizujący pracę.

---

Dwie podstawowe strategie

Strategia 1: Mądry koordynator + tanie wykonanie

Schemat:

Mocny model
     |
     |
     +---- tani agent: wyszukiwanie
     |
     +---- tani agent: testy
     |
     +---- tani agent: proste refaktoryzacje

Zalety

- bardzo dobre planowanie,
- mniejsze ryzyko złej architektury,
- dobra praca przy dużych projektach.

Wady

- główny model zużywa tokeny cały czas,
- koszt rośnie nawet przy prostych zadaniach,
- część decyzji może być wykonywana przez zbyt drogi model.

---

Strategia 2: Tani koordynator + eskalacja

Schemat:

Średni/tani model
        |
        |
        +---- rozwiązuje większość problemów
        |
        +---- prosi mocny model o pomoc
                  |
                  +---- architektura
                  +---- trudny debugging
                  +---- decyzje projektowe

Zalety

- dużo niższy koszt,
- większość pracy nie wymaga topowego modelu,
- łatwo skalować.

Wady

- słabszy model może nie rozpoznać trudności,
- może za późno eskalować,
- może stworzyć rozwiązanie wymagające późniejszej poprawy.

---

Rekomendowana strategia

Dla typowej pracy programisty najlepszy jest model hybrydowy:

80% pracy
|
+-- tani / średni model

15%
|
+-- mocniejszy model

5%
|
+-- najmocniejszy model

---

Proponowany podział ról agentów

Agent wykonawczy

Zadania:

- implementacja funkcji,
- poprawki błędów,
- testy,
- refaktoryzacje lokalne.

Model:

- tani lub średni.

---

Agent badawczy

Zadania:

- analiza repozytorium,
- znalezienie zależności,
- analiza dokumentacji,
- przygotowanie planu.

Model:

- tani.

---

Agent architekt

Zadania:

- decyzje projektowe,
- duże zmiany,
- migracje,
- analiza kompromisów.

Model:

- najmocniejszy.

---

Agent reviewer

Zadania:

- code review,
- szukanie błędów,
- kontrola jakości.

Model:

- średni lub mocny.

---

Aktualne ograniczenie Codexa

Obecnie nie można w prosty sposób skonfigurować reguły:

jeżeli zadanie proste:
    użyj modelu A

jeżeli zadanie średnie:
    użyj modelu B

jeżeli zadanie trudne:
    użyj modelu C

Czyli brakuje pełnego dynamicznego routera inteligencji.

Możliwe jest natomiast:

- ustawienie domyślnego modelu,
- ustawienie modeli dla subagentów,
- ograniczenie liczby agentów,
- określenie zasad delegowania przez instrukcje projektu.

---

Najlepsza praktyka instrukcji dla agenta

Przykład polityki:

Przed rozpoczęciem pracy oceń złożoność zadania.

Nie używaj mocnego modelu dla:
- formatowania,
- prostych zmian,
- pojedynczych testów,
- lokalnych refaktoryzacji.

Eskaluj do mocniejszego modelu gdy:
- zmiana obejmuje wiele modułów,
- wymagana jest decyzja architektoniczna,
- problem nie został rozwiązany po dwóch próbach,
- istnieje wiele możliwych rozwiązań.

---

Porównanie Codex vs Claude Code

Obszar| Codex| Claude Code
Jakość modeli| bardzo wysoka| bardzo wysoka
Konfigurowanie agentów| prostsze| bardziej rozbudowane
Subagenci| dostępni| bardzo elastyczni
Routing modeli| ograniczony| bardziej konfigurowalny
Kontrola workflow| średnia| wysoka
Możliwości własnego harnessa| wysokie przez API| wysokie przez konfigurację

---

Idealny przyszły harness

Docelowo najlepszy system powinien działać tak:

flowchart TD
    A[Nowe zadanie] --> B[Analiza trudności]

    B --> C{Poziom trudności}

    C -->|Proste| D[Tani model]
    C -->|Średnie| E[Średni model]
    C -->|Trudne| F[Mocny model]

    D --> G[Testy]
    E --> G
    F --> G

    G --> H{Problem?}

    H -->|Nie| I[Gotowe]
    H -->|Tak| F

---

Rekomendacja końcowa

Najbardziej efektywny obecnie workflow:

1. Nie uruchamiać najmocniejszego modelu cały czas.
2. Używać taniego modelu jako pierwszej linii.
3. Traktować mocny model jako konsultanta.
4. Tworzyć wyspecjalizowane role agentów.
5. Automatyzować eskalację dopiero przez własny harness.

Największa oszczędność nie wynika z wyboru jednego najlepszego modelu.

Wynika z tego, żeby najlepszy model pojawiał się dokładnie wtedy, gdy jego inteligencja daje największą wartość.