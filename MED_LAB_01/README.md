# Lab 1 - Analiza logów klastra HPC

## Dane wejściowe

Do wykonania zadań wymagany jest plik:
* `HPC_2k.log_structured.csv`

## Zadania do wykonania

1. **Konwersja czasu**
   * Kolumna `Time` zawiera czas w formacie UNIX Timestamp (liczba sekund od 1 stycznia 1970 r.).
   * Stwórz nową kolumnę `Datetime`, konwertując wartości z kolumny `Time` na obiekt daty i czasu.
   * Wyodrębnij godzinę z nowej kolumny do zmiennej `Hour`.
   * Oblicz liczbę logów wygenerowanych w poszczególnych godzinach i zidentyfikuj okno czasowe z największą aktywnością systemu.

2. **Identyfikacja najbardziej awaryjnego węzła**
   * Klaster obliczeniowy składa się z wielu maszyn (węzłów). Należy ustalić, które z nich wymagają największej uwagi administratorów.
   * Zgrupuj dane według kolumny `Node` i policz całkowitą liczbę wystąpień dla każdego węzła.
   * Posortuj wyniki malejąco i wyodrębnij 5 maszyn, które wygenerowały najwięcej zdarzeń w badanym okresie.

3. **Identyfikacja stanów systemu**
   * Kolumna `State` przechowuje informacje o statusie danego zdarzenia w klastrze.
   * Zidentyfikuj wszystkie unikalne wartości występujące w kolumnie `State`.
   * Oblicz procentowy udział każdego ze stanów w stosunku do wszystkich 2000 logów.
   * Przedstaw wyniki z dokładnością do dwóch miejsc po przecinku (np. `45.50%`), aby sprawdzić, czy dominują rutynowe komunikaty, czy zmiany stanu na niedostępny.