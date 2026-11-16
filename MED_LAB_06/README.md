# Lab 6 - Uczenie maszynowe i klasyfikacja

## Dane wejściowe

* Pliki lokalne: `login.csv`, `transakcje.csv`
* Zbiór z Kaggle (zadanie 3):

```python
import kagglehub
from kagglehub import KaggleDatasetAdapter

df = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "uciml/sms-spam-collection-dataset",
    "spam.csv",
)
```

## Zadania do wykonania

1. **Drzewa decyzyjne (`login.csv`)**
   * Odczytaj plik `login.csv` i podziel dane na zbiór uczący oraz testowy w proporcji `80/20`, stosując podział warstwowy (`stratify`).
   * Wytrenuj klasyfikator drzew decyzyjnych (`DecisionTreeClassifier`) i oceń jego działanie, obliczając wskaźniki: macierz pomyłek (Confusion matrix), `Accuracy`, `Precision` oraz `Recall` (możesz użyć `classification_report`).
   * Za pomocą metody `plot_tree` lub `export_text` z pakietu `sklearn.tree` przedstaw reguły wyuczone przez klasyfikator (pamiętaj o przekazaniu parametru `feature_names`).
   * Zidentyfikuj najdłuższą ścieżkę prowadzącą do liścia z decyzją `"zablokowany"`.
   * Wytrenuj ponownie model, ustawiając parametr `max_depth=2`, i sprawdź, jak wpłynie to na czułość (`Recall`) klasyfikatora.

2. **Lasy losowe i ważność cech (`transakcje.csv`)**
   * Odczytaj dane z pliku `transakcje.csv` i przygotuj je do trenowania modelu lasów losowych (`RandomForestClassifier`).
   * Po wytrenowaniu modelu przeanalizuj macierz pomyłek.
   * Wyciągnij z wytrenowanego modelu wektor `feature_importances_` i stwórz wykres słupkowy pokazujący 3 najważniejsze cechy wykorzystywane przy wykrywaniu oszustw.

3. **Klasyfikacja tekstu - Naiwny Klasyfikator Bayesa (`spam.csv`)**
   * Odczytaj dane ze zbioru *SMS Spam Collection Dataset* (pozostaw tylko kolumny `class` i `sms`) i sprawdź, czy występują w nich braki danych.
   * Podziel dane na zbiór uczący i testowy w proporcji `80/20` z użyciem `stratify`.
   * Wytrenuj naiwny klasyfikator Bayesa (np. `MultinomialNB` po wektoryzacji tekstu) i sprawdź jego skuteczność za pomocą macierzy pomyłek.
   * Utwórz własne przykładowe wiadomości tekstowe, aby przetestować działanie wytrenowanego klasyfikatora na nowych danych.