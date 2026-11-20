# Prompt: Konwersja książki do markdown

Jesteś redaktorem technicznym, który konwertuje publikacje naukowe z PDF do markdowna "rozumianego" przez AI.

## 🎯 Goal (Cel)
Zamień książkę `materials/Rafy_metodologiczne_Wieczorkowska_Wierzbinska_Grazyna_2025.pdf` na plik markdown `output/materials/Rafy_metodologiczne_Wieczorkowska_Wierzbinska_Grazyna_2025.md` zawierający pełny tekst książki: nagłówki rozdziałów (`##`), akapity, listy, cytaty, tabele; każdy obraz zastąpiony adnotacją tekstową (treść obrazka staje się opisem).

## 🧱 Boundaries (Granice)
- Plik źródłowy (PDF) traktuj jako wyłącznie do odczytu — nie modyfikuj go ani nie usuwaj.
- Zapisuj wyłącznie w `output/materials/` (plik wynikowy i notatka); nie twórz plików poza tym katalogiem.
- Nie wymyślaj treści, której nie ma w książce. Nie streszczaj — konwertuj pełny tekst. Zachowuj oryginalne nazwy rozdziałów i sekcji.
- Nie zakładaj konkretnej biblioteki (np. Docling): przeanalizuj środowisko (skills, umiejętności, narzędzia, biblioteki), wybierz narzędzie do konwersji PDF z obrazkami do markdowna z adnotacjami tekstowymi i użyj go, jeśli już istnieje; jeśli nie istnieje — utwórz środowisko z wymaganymi bibliotekami.

## 🔄 Podział pracy (środowisko, wykonanie, weryfikacja)
1. **Środowisko**: wybierz albo utwórz środowisko i narzędzie konwersji.
2. **Konwersja**: przeprowadź konwersję do pliku wynikowego. Adnotacja obrazu ma format:
   `> **[Ryc. <numer/oznaczenie>, s. <strona>]** <opis treści obrazu>`
3. **Notatka**: w `output/materials/konwersja_notatka.md` zapisz: użyte narzędzie/biblioteki i dlaczego; liczbę rozdziałów i obrazów w źródle; liczbę rozdziałów i adnotacji w wyniku; ewentualne odstępstwa.
4. **Weryfikacja**: sekcja poniżej, wykonana jako osobny krok.

## 🛑 Stop
Konwersja jest zakończona, gdy: plik wynikowy istnieje, jest niepusty i przechodzi sekcję „Weryfikacja: kompletność i brak halucynacji".
Maksymalnie 2 rundy poprawek po nieudanej weryfikacji. Potem STOP i raport: których warunków nie spełniono, co sprawdzono i jakich danych brakuje do kontynuacji.

## 🔬 Weryfikacja: kompletność i brak halucynacji
Wykonaj niezależnie od generowania — odczytując pliki od nowa, nie z pamięci.
1. Kompletność: liczba rozdziałów i sekcji w markdown == liczba rozdziałów i sekcji w źródle (metoda porównania: zakładki PDF / spis treści); w markdown są spis treści (lub lista rozdziałów) i wstęp.
2. Brak halucynacji: 10 losowo wybranych fragmentów markdowna (po co najmniej 1 pełnym zdaniu) występuje 1:1 w tekście książki; nagłówki rozdziałów i sekcji są dosłownie zgodne z oryginałem (bez zmyślonych tytułów).
3. Obrazy: liczba adnotacji w markdown == liczba obrazów zgłoszonych przez narzędzie konwertujące (obie liczby odnotuj w notatce wynikowej).
4. Jeśli weryfikacja wykryje braki: popraw je, uzupełniając z konwersji — nie zmyśloną treścią.
