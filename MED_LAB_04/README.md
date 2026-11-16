# Lab 4 - Statystyka opisowa, czyszczenie danych i rozkłady

## Pobieranie danych

Zbiory danych do zadań 1-3 można pobrać bezpośrednio za pomocą biblioteki `kagglehub`:

```python
import kagglehub
from kagglehub import KaggleDatasetAdapter

# Zadanie 1
df_salaries = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "ruchi798/data-science-job-salaries",
    "ds_salaries.csv",
)

# Zadanie 2
df_playstore = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "lava18/google-play-store-apps",
    "googleplaystore.csv",
)

# Zadanie 3
df_energy = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "loveall/appliances-energy-prediction",
    "KAG_energydata_complete.csv",
)
```

## Zadania do wykonania

1. **Analiza wynagrodzeń (`ds_salaries.csv`)**
   * Wczytaj dane, a następnie oblicz średnią arytmetyczną i medianę dla kolumny `salary_in_usd`.
   * Zidentyfikuj wartości odstające na podstawie odchylenia standardowego i odfiltruj rekordy, których wartość przekracza 3-krotność odchylenia standardowego od średniej.
   * Na wykresie pudełkowym narysuj rozkład dla kolumny `salary_in_usd` przed i po filtracji.

2. **Oceny aplikacji (`googleplaystore.csv`)**
   * Wczytaj dane i sprawdź, czy w kolumnie `Rating` występują puste rekordy (braki danych) - jeżeli tak, usuń je.
   * Na podstawie oczyszczonej kolumny `Rating` oblicz dominantę i narysuj histogram ocen.

3. **Stabilność temperatur (`KAG_energydata_complete.csv`)**
   * Wczytaj dane i sprawdź, czy nie występują braki danych w kolumnach od `T1` do `T9` - jeżeli wystąpią, usuń wybrakowane rekordy.
   * Przeanalizuj temperatury i oblicz wariancję oraz odchylenie standardowe dla każdego pomieszczenia, wskazując, które z nich charakteryzuje się najbardziej stabilną temperaturą.
   * Korzystając z histogramów, przedstaw rozkład temperatur na wykresie.

4. **Rozkład dystansu przejazdów (`taxis` z Seaborn)**
   * Załaduj wbudowany w bibliotekę `seaborn` zbiór NYC Taxis (`taxis`) do ramki danych.
   * Sprawdź, czy w kolumnie `distance` występują braki danych oraz wartości nietypowe (kursy o ujemnej lub zerowej długości) - jeśli tak, usuń te rekordy.
   * Oblicz wartości kurtozy i skośności dla kolumny `distance`.
   * Dodaj nową kolumnę `distance_log`, uzupełniając ją zlogarytmowaną wartością dystansu przy użyciu `np.log1p(df["distance"])`.
   * Przygotuj wykresy gęstości KDE (Kernel Density Estimation) dla kolumn `distance` oraz `distance_log`.