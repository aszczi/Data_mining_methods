# Lab 3 - Wizualizacja danych i analiza ruchu SSL

## Dane wejściowe

Do wykonania zadania 3 wymagany jest plik:
* `ssl.csv`

*Uwaga: Dla każdego wykresu opisz osie, nadaj tytuł wykresu oraz dodaj legendę.*

## Zadania do wykonania

1. **Podstawy rysowania kształtów**
   * Narysuj koło o środku w punkcie `(0,0)` i promieniu `2`.
   * Powinno być ono wypełnione półprzezroczystą barwą zieloną, mieć wyraźnie zaznaczony brzeg i nie wyglądać jak elipsa (zachowaj odpowiednie proporcje osi).

2. **Wizualizacja ze zbiorem `tips` (Seaborn)**
   * Korzystając z pakietu `seaborn` i wbudowanego zbioru danych `tips`, narysuj następujące wykresy:
     1. Dwa wykresy (kołowy i słupkowy), które będą podsumowywać zmienną `smoker`.
     2. Wykres skrzynkowy (boxplot) dla procentowego udziału napiwku w całkowitej wartości rachunku w rozbiciu na podgrupy generowane przez kombinacje `sex` i `day`.
     3. Wykres skrzynkowy dla procentowego udziału napiwku w całkowitej wartości rachunku na podstawie całej ramki danych `tips`.

3. **Analiza ruchu sieciowego SSL (`ssl.csv`)**
   * Korzystając z pliku `ssl.csv`, wykonaj następujące polecenia:
     1. **Algorytmy szyfrujące:** Odczytaj dane z kolumny `cipher` i zidentyfikuj najczęściej używane algorytmy szyfrujące. Przedstaw dane na wykresie i odpowiedz, czy najpopularniejszy algorytm jest bezpiecznym rozwiązaniem.
     2. **Najbardziej aktywne hosty:** Bazując na kolumnie `source_ip`, wyszukaj stacje robocze lub serwery generujące największy ruch SSL. Przedstaw na wykresie 6 najaktywniejszych urządzeń.
     3. **Status walidacji certyfikatów:** Kolumna `certificate_validation_status` zawiera dane o certyfikatach. Przedstaw te informacje na wykresie kołowym (uwzględniając znak `-` oznaczający brak danych) i sprawdź, jaki rodzaj statusu występuje najczęściej.
     4. **Rozkład czasowy połączeń:** Kolumna `timestamp_unix` zawiera znacznik czasowy. Przekonwertuj ją na czas, policz liczbę połączeń w każdej godzinie i przedstaw wyniki na wykresie liniowym.