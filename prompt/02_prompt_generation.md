# Prompt: Generowanie prompta z weryfikacją (kompletność i brak halucynacji)

Jesteś inżynierem promptów. Wygenerowany prompt ma zawierać 3 filary (Goal, Boundaries, Stop) oraz techniki: Role/Context, specyfikację danych (wejścia i wyjścia), przykłady Few-Shot, format JSON. Techniki zastosuj w treści wygenerowanego prompta — nie opisuj ich w nim.

## 🎯 Goal (Cel)
Wygeneruj działający prompt do wykrywania fałszywych respondentów w ankietach, na podstawie metodyki opisanej w książce prof. Grażyny Wieczorkowskiej-Wierzbińskiej (`output/materials/Rafy_metodologiczne_Wieczorkowska_Wierzbinska_Grazyna_2025.md` — konwertowana książka).

## 🧱 Boundaries (Granice)
- Warunek wstępny: plik źródłowy `output/materials/Rafy_metodologiczne_Wieczorkowska_Wierzbinska_Grazyna_2025.md` istnieje. Jeśli nie — STOP i raport; nie odtwarzaj metodyki z pamięci modelu.
- Kryteria oceny czerp wyłącznie z książki; w wygenerowanym prompcie każde kryterium wskazuje rozdział/fragment źródła.
- Nie dodawaj instrukcji spoza treści zadania i poza metodyką z książki.
- Nie zapisuj plików poza wynikiem (patrz Output).

## 📤 Output (kontrakt generowanego promptu)
Plik `output/prompt/score_prompt.txt` (utwórz folder `output/prompt`) zawiera wyłącznie gotowy tekst promptu, bez komentarzy i wstępów.
Wygenerowany prompt specyfikuje **wejście**: strukturę rekordu odpowiedzi ankietowej (identyfikator odpowiedzi/ankiety oraz pola odpowiedzi zgodne z danymi wejściowymi harnessu).
Wygenerowany prompt specyfikuje **wyjście** jako JSON:

```json
{
  "id_odpowiedzi": "<identyfikator ankiety/odpowiedzi, zgodny ze specyfikacją wejścia>",
  "ocena": 0.0,
  "uzasadnienie": "<odniesienie do kryteriów oceny z metodyki + wskazanie rozdziału książki>"
}
```

Skala i interpretacja pola `ocena` pochodzą z metodyki w książce i muszą być w prompcie zdefiniowane (nie wymyślone).

## 🔄 Wykonanie
1. Przeczytaj książkę (`output/materials/...md`) i wypisz fragmenty o diagnostyce/fałszywych respondentach.
2. Wygeneruj prompt: rola, kontekst zadania, specyfikacja wejścia, kryteria oceny (z odwołaniami do rozdziałów), specyfikacja wyjścia JSON, 1–2 przykłady Few-Shot (odpowiedź typowa i podejrzana) zgodne ze specyfikacjami, warunki zakończenia.
3. Zapisz wynik do `output/prompt/score_prompt.txt`.
4. Wykonaj weryfikację jako osobny krok (poniżej).

## 🛑 Stop
Zakończ, gdy wygenerowany prompt przechodzi sekcję „Weryfikacja generowanego prompta".
Maksymalnie 2 rundy poprawek. Potem STOP i raport: których warunków nie spełniono i czego brakuje do kontynuacji.

## 🧐 Weryfikacja generowanego prompta
Przeprowadź niezależnie od generowania — odczytując `score_prompt.txt` od nowa, nie z pamięci.
- **Kompletność**: w pliku są rola, kontekst zadania, specyfikacja wejścia, kryteria oceny, specyfikacja wyjścia JSON, przykłady Few-Shot, cel, granice i warunki zakończenia.
- **Specyfikacja output**: prompt specyfikuje `id_odpowiedzi`, `ocena` (ze zdefiniowaną skalą zgodną z metodyką) i `uzasadnienie` (z odniesieniem do kryteriów oceny w metodyce).
- **Brak halucynacji**: każdy merytoryczny element promptu wynika z treści zadania i z książki (przy każdym kryterium wskazano rozdział); brak instrukcji spoza treści zadania.
- **Spójność przykładów**: przykłady Few-Shot są zgodne ze specyfikacją wejścia i wyjścia.
