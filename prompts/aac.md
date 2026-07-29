KOMPLETNY PROMPT – APLIKACJA AAC NA TABLET (OFFLINE, Z EDYCJĄ)

== CEL ==
Stworzyć prostą aplikację AAC na tablet (działa offline), która:
- Czyta strukturę folderów (foldery = kategorie, zdjęcia = przyciski)
- Ma pasek odczytu (konstruktor zdań) z TTS
- Pozwala edytować parametry każdego elementu (nazwa, tekst, kolor, ukrycie)
- Działa w przeglądarce jako PWA (HTML/CSS/JS) – najprostsza technologia

== 1. JAK DZIAŁA ==
Użytkownik wskazuje główny folder (np. "Tablica AAC").
Aplikacja skanuje jego strukturę:
- Każdy podfolder = kategoria (przycisk)
- Każde zdjęcie (.jpg, .png, .gif, .webp) = przycisk
- Dowolny poziom zagnieżdżeń = podkategorie
- Kliknięcie zdjęcia = dodanie tekstu do paska odczytu
- Kliknięcie folderu = przejście do niego

== 2. NAZEWNICTWO PLIKÓW (ZNACZNIKI) ==
Aplikacja parsuje nazwy plików/folderów według wzorca:
[nazwa_wyświetlana][@@tekst_mówiony][##ukryj_nazwę][^^indeks_koloru].rozszerzenie

Znaczniki:
- @@ = oddziela nazwę wyświetlaną od tekstu mówionego
- ## = ukrywa nazwę (przycisk bez etykiety)
- ^^ + liczba (0-9) = indeks koloru z palety

Przykłady:
- śniadanie@@Chcę zjeść##^^3.jpg → wyświetla: (pusto), mówi: "Chcę zjeść", kolor: indeks 3
- obiad@@Dziś zjem zupę^^1.jpg → wyświetla: "obiad", mówi: "Dziś zjem zupę", kolor: indeks 1
- woda.jpg → wyświetla: "woda", mówi: "woda", kolor: domyślny

Ikony folderów:
- Opcjonalny plik "ikona.jpg" lub "folder.jpg" w folderze
- Jeśli brak – domyślna ikona (emoji 📁)

== 3. EKRAN APLIKACJI (od góry do dołu) ==

A. Pasek nawigacyjny:
[🔙] [ścieżka: Jedzenie > Fast food] [✏️ Edycja] [⚙️] [🎨]
- 🔙 = powrót do poprzedniego folderu
- ✏️ = przełącznik trybu edycji (włącz/wyłącz)
- ⚙️ = ustawienia (motyw, kolumny, głos)
- 🎨 = zmiana motywu

B. Pasek odczytu (konstruktor zdań):
[wyświetla zebrane teksty: "Chcę zjeść | burger | z serem"]
[► Odtwórz] [🗑️ Wyczyść] [📋 Kopiuj]
- Kliknięcie elementu = usuń z paska
- ► = TTS czyta całość
- 🗑️ = czyści pasek
- 📋 = kopiuje tekst do schowka

C. Siatka przycisków (zdjęcia + opcjonalne nazwy):
- Liczba kolumn: 2-6 (konfigurowalna)
- Tryb normalny: kliknięcie = dodanie do paska
- Tryb edycji: kliknięcie = otwarcie okna edycji

D. Klawiatura (opcjonalnie):
- Przycisk pokaż/ukryj klawiaturę systemową
- Wpisany tekst dodaje się do paska odczytu

== 4. TRYB EDYCJI ==
Po włączeniu ✏️:
- Kliknięcie zdjęcia → otwiera okno edycji
- Kliknięcie folderu → otwiera okno edycji kategorii

Okno edycji zdjęcia:
┌─────────────────────────────────┐
│ Edytuj element                   │
│ [podgląd zdjęcia]                │
│ Nazwa wyświetlana: [________]    │
│ Tekst mówiony:    [________]    │
│ Ukryj nazwę:      [✓]           │
│ Kolor:            [▼ 0-9]       │
│ [Zapisz] [Anuluj] [Usuń]       │
└─────────────────────────────────┘

Okno edycji folderu:
┌─────────────────────────────────┐
│ Edytuj kategorię                 │
│ Nazwa: [________]                │
│ Tekst mówiony: [________]       │
│ Kolor: [▼ 0-9]                  │
│ [Zapisz] [Anuluj]              │
└─────────────────────────────────┘

== 5. ZAPISYWANIE ZMIAN ==
Wszystkie zmiany zapisywane w LocalStorage (proste, offline):
{
  "ścieżka/do/pliku.jpg": {
    "displayName": "Śniadanie",
    "speechText": "Chcę zjeść",
    "hideName": true,
    "colorIndex": 3
  },
  "ścieżka/do/folderu": {
    "displayName": "Jedzenie",
    "speechText": "Głodny jestem",
    "colorIndex": 1
  }
}

== 6. MOTYWY KOLORYSTYCZNE ==
Paleta 10 kolorów (indeksy 0-9):
0=#FF6B6B (czerwony), 1=#FF9F43 (pomarańczowy), 2=#FECA57 (żółty)
3=#1DD1A1 (zielony), 4=#54A0FF (niebieski), 5=#5F27CD (fioletowy)
6=#FFFFFF (biały), 7=#2D3436 (czarny), 8=#A29BFE (jasny fiolet), 9=#00B894 (morski)

Użytkownik może wybrać motyw w ustawieniach (motyw = inna paleta).

== 7. TECHNOLOGIA (NAJPROSTSZA) ==
- HTML5 + CSS3 + JavaScript (ES6)
- Web Speech API (TTS – synteza mowy)
- File System Access API (czytanie folderów – nowoczesne przeglądarki)
- Service Worker (działanie offline)
- LocalStorage (zapisywanie zmian)
- PWA – można zainstalować na tablecie

== 8. STRUKTURA APLIKACJI ==
index.html – główny plik
style.css – wszystkie style
app.js – cała logika
sw.js – Service Worker (offline)
manifest.json – instalacja PWA

== 9. GŁÓWNE FUNKCJE W app.js ==
- openFolder() – wybór folderu przez użytkownika
- scanFolder(path) – skanuje strukturę rekurencyjnie
- parseFilename(name) – parsuje znaczniki (@@, ##, ^^)
- renderGrid(items) – wyświetla siatkę przycisków
- addToSpeechBar(text) – dodaje do paska odczytu
- speak(text) – TTS
- editItem(item) – otwiera okno edycji
- saveConfig() – zapis do LocalStorage
- loadConfig() – odczyt z LocalStorage

== 10. PRZYKŁADOWA STRUKTURA FOLDERÓW ==
Tablica AAC/
├── Jedzenie/
│   ├── ikona.jpg
│   ├── śniadanie@@Chcę zjeść##^^3.jpg
│   ├── obiad@@Dziś zjem zupę^^1.jpg
│   └── Fast food/
│       ├── hamburger@@Kupię burgera^^1.jpg
│       └── pizza.jpg
├── Napoje/
│   ├── woda@@Poproszę wodę^^4.jpg
│   └── sok.jpg
└── Pomoc/
    ├── ikona.jpg
    ├── pomoc@@Potrzebuję pomocy^^0.jpg
    └── toaleta@@Chcę iść do toalety^^0.jpg

== 11. PRZYKŁAD DZIAŁANIA ==
1. Otwieram aplikację → wybieram folder "Tablica AAC"
2. Widzę kategorie: Jedzenie, Napoje, Pomoc
3. Klikam "Jedzenie" → przejście do podfolderu
4. Widzę: śniadanie, obiad, Fast food
5. Klikam ✏️ (tryb edycji) → ramki wokół przycisków
6. Klikam "śniadanie" → okno edycji
7. Zmieniam tekst mówiony na "Chcę zjeść śniadanie", zaznaczam "Ukryj nazwę"
8. Zapisuję → zmiana w LocalStorage
9. Wyłączam tryb edycji
10. Klikam zdjęcie → pasek odczytu: "Chcę zjeść śniadanie" (nazwa ukryta)
11. Klikam "Fast food" → przejście
12. Klikam "hamburger" → pasek: "Chcę zjeść śniadanie | Kupię burgera"
13. Klikam "pizza" → pasek: "Chcę zjeść śniadanie | Kupię burgera | pizza"
14. Klikam ► → TTS czyta: "Chcę zjeść śniadanie. Kupię burgera. Pizza."
15. Klikam 🗑️ → pasek wyczyszczony
16. Klikam klawiaturę → wpisuję "Dziękuję" → pasek: "Dziękuję"
17. Klikam ► → TTS: "Dziękuję."

== 12. WYMAGANIA (lista) ==
[x] Czytanie struktury folderów
[x] Parsowanie znaczników (@@, ##, ^^)
[x] Siatka przycisków (zmienna liczba kolumn)
[x] Pasek odczytu (konstruktor zdań)
[x] TTS (Web Speech API)
[x] Tryb edycji (zmiana nazwy, tekstu, koloru, ukrycia)
[x] Zapisywanie zmian (LocalStorage)
[x] Praca offline (Service Worker)
[x] Instalacja jako PWA
[x] Klawiatura systemowa
[x] Motywy kolorystyczne
[x] Nawigacja między folderami

== 13. PROSTE ROZWIĄZANIA ==
- Zamiast bazy danych → LocalStorage
- Zamiast serwera → Service Worker
- Zamiast API → bezpośrednie czytanie folderów
- Zamiast logowania → brak (aplikacja lokalna)

== 14. OGRANICZENIA ==
- Wymaga nowoczesnej przeglądarki (Chrome, Edge, Safari)
- Czytanie folderów wymaga zgody użytkownika
- TTS zależy od systemowego głosu

== 15. CO CHCĘ UZYSKAĆ W NOWEJ SESJI ==
1. Potwierdzenie zrozumienia koncepcji
2. Kompletny kod (index.html, app.js, style.css, sw.js, manifest.json)
3. Instrukcja uruchomienia
4. Gotowa do użycia aplikacja PWA