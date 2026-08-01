# Automatyzacja przygotowania RepoMix dla Microsoft 365 Copilot

## Cel

Zautomatyzować przygotowywanie aktualnego kontekstu dla Microsoft 365 Copilot poprzez:

1. Pobranie kodu z repozytoriów Bitbucket.
2. Wygenerowanie RepoMix dla każdego repozytorium.
3. Umieszczenie wygenerowanych plików w SharePoint.
4. Korzystanie z tych plików w Microsoft 365 Copilot.

---

# Założenia

- Repozytoria znajdują się w Bitbucket.
- Nie ma możliwości uruchamiania własnych pipeline'ów.
- Proces ma działać lokalnie.
- Microsoft 365 Copilot ma dostęp do SharePoint.
- RepoMix generuje pojedynczy plik opisujący repozytorium.

---

# Proponowana architektura

```
Bitbucket
      │
      ▼
git pull
      │
      ▼
RepoMix
      │
      ▼
repo-name.md
      │
      ▼
Uploader
      │
      ▼
SharePoint
      │
      ▼
Microsoft 365 Copilot
```

---

# Struktura katalogów

```
C:\Repomix

    config.yaml

    repositories\
        projectA\
        projectB\
        projectC\

    output\
        projectA.md
        projectB.md
        projectC.md
```

---

# Plik konfiguracyjny

Przykład:

```yaml
repositories:

  - name: ProjectA
    path: C:\Repos\ProjectA
    sharepoint: Projekty/ProjectA

  - name: ProjectB
    path: C:\Repos\ProjectB
    sharepoint: Projekty/ProjectB

  - name: ProjectC
    path: C:\Repos\ProjectC
    sharepoint: Projekty/ProjectC
```

Dzięki temu dodanie nowego projektu oznacza dopisanie jednej sekcji.

---

# Proces

## Krok 1

Dla każdego repo:

```
git pull
```

lub

```
git fetch
git reset --hard origin/main
```

---

## Krok 2

Uruchomienie RepoMix

Przykładowo:

```
repomix .
```

Powstaje:

```
ProjectA.md
```

---

## Krok 3

Przeniesienie pliku do katalogu output

```
output/
    ProjectA.md
```

---

## Krok 4

Upload do SharePoint

Możliwości:

### Microsoft Graph API

lub

### Microsoft 365 CLI

lub

### PowerShell PnP

Uploader sprawdza:

- czy plik istnieje
- czy jest nowszy
- jeśli tak — nadpisuje

---

# Harmonogram

Można uruchamiać:

- ręcznie
- codziennie
- co godzinę
- po zakończeniu pracy

Windows:

Task Scheduler

Linux:

cron

---

# Struktura SharePoint

```
RepoMix

    ProjectA
        ProjectA.md

    ProjectB
        ProjectB.md

    ProjectC
        ProjectC.md
```

lub

```
RepoMix

    ProjectA.md
    ProjectB.md
    ProjectC.md
```

---

# Korzystanie z Microsoft 365 Copilot

Copilot może analizować dokumenty znajdujące się w SharePoint, do których użytkownik ma dostęp.

Możliwe polecenia:

- Porównaj implementację w ProjectA i ProjectB.
- Znajdź wszystkie miejsca użycia klasy CustomerService.
- Jak wygląda architektura projektu?
- Gdzie wykonywana jest autoryzacja?
- Jak przebiega przepływ danych?

---

# Ograniczenia

Microsoft 365 Copilot:

- nie zapamiętuje na stałe konkretnego folderu SharePoint jako domyślnego kontekstu,
- nie ładuje automatycznie wskazanych plików RepoMix przy każdym czacie,
- działa wyłącznie na zasobach, do których użytkownik ma uprawnienia.

Aby mieć stałe źródło wiedzy, należałoby wykorzystać **Copilot Studio** i własnego agenta.

---

# Możliwe rozszerzenia

## 1. Generowanie wielu wersji

```
ProjectA-main.md
ProjectA-release.md
ProjectA-develop.md
```

---

## 2. Wersjonowanie

```
ProjectA

    latest.md

    history

        2026-08-01.md
        2026-08-05.md
```

---

## 3. Automatyczne wykrywanie zmian

Skrypt może:

- wykonać `git status`,
- sprawdzić ostatni commit,
- wygenerować RepoMix tylko dla zmienionych repozytoriów.

---

## 4. Raport końcowy

Po zakończeniu:

```
✓ ProjectA

✓ ProjectB

✓ ProjectC

Brak zmian:
ProjectD

Błąd:
ProjectE
```

---

# Docelowy przepływ

```
Uruchom skrypt
        │
        ▼
Pobierz zmiany z Bitbucket
        │
        ▼
RepoMix dla każdego repo
        │
        ▼
Wygeneruj pliki Markdown
        │
        ▼
Prześlij do SharePoint
        │
        ▼
Microsoft 365 Copilot korzysta z aktualnych dokumentów
```

---

# Dalsze usprawnienia

W przyszłości można rozbudować rozwiązanie o:

- automatyczne generowanie diagramów architektury,
- indeksowanie API i klas,
- generowanie streszczeń zmian między commitami,
- tworzenie dokumentacji technicznej wraz z RepoMix,
- generowanie plików zoptymalizowanych pod pracę modeli AI (LLM-ready),
- integrację z własnym agentem w Copilot Studio, który będzie korzystał z RepoMix jako głównego źródła wiedzy.