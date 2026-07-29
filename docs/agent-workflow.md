# Agent Workflow

## Cel

Standardowy proces wykonywania pracy przez agenta.

---

# 1. Explore

Cel:
zrozumienie sytuacji.

Agent:

- znajduje odpowiedzialny kod,
- analizuje zależności,
- sprawdza istniejące rozwiązania.

Rezultat:

- opis problemu,
- lista istotnych plików,
- ograniczenia.

---

# 2. Plan

Agent przygotowuje:

- cel,
- kroki,
- przewidywane zmiany,
- ryzyka.

Duże zadania dzielone są na mniejsze etapy.

---

# 3. Execute

Zasady:

- jeden etap naraz,
- małe zmiany,
- częsta walidacja.

Nie łączyć:

- nowych funkcji,
- refaktoru,
- zmian infrastruktury

w jednym kroku bez potrzeby.

---

# 4. Verify

Walidacja według kosztu:

1. analiza statyczna,
2. testy lokalne,
3. testy integracyjne,
4. pełny pipeline.

Najpierw najtańsza informacja.

---

# 5. Review

Agent ocenia:

- regresje,
- ryzyka,
- prostotę rozwiązania,
- możliwość ograniczenia zmian.

---

# Zasada nadrzędna

Nie wykonuj więcej pracy.

Wykonuj właściwą pracę.