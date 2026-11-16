# Lab 5 - Wnioskowanie statystyczne, testy hipotez i analiza HR / UNSW-NB15

## Dane wejściowe

* Plik lokalny: `HR.csv`
* Zbiór z Kaggle (zadanie 4):

```python
import kagglehub
from kagglehub import KaggleDatasetAdapter

df = kagglehub.load_dataset(
    KaggleDatasetAdapter.PANDAS,
    "mrwellsdavid/unsw-nb15",
    "UNSW_NB15_training-set.csv",
)
```

## Zadania do wykonania

### 1. Pomiary filamentu (statystyki podstawowe)
Kupiłeś szpulę filamentu o deklarowanej średnicy $1.75\text{ mm}$ do drukarki 3D. Za pomocą suwmiarki wykonałeś pięć pomiarów w różnych punktach na szpuli: `1.78, 1.75, 1.72, 1.74, 1.77`.
* Oblicz średnią oraz odchylenie standardowe dla tego zbioru wartości.

### 2. Przedział ufności dla średniej
Masz wątpliwości, czy filament rzeczywiście ma deklarowane $1.75\text{ mm}$ średnicy. Wykonałeś $34$ pomiary, dla których średnia próby wynosi $1.715588$, a odchylenie standardowe próby $0.029252$.
* Wyznacz $99$-procentowy przedział ufności dla średniej średnicy filamentu na całej szpuli.

### 3. Analiza danych pracowników (`HR.csv`)

**Opis kolumn:**
* `satisfaction_level` - poziom satysfakcji pracownika w skali od $0$ do $1$,
* `last_evaluation` - ocena pracownika w skali od $0$ do $1$,
* `number_project` - liczba projektów, w które zaangażowany był pracownik,
* `average_montly_hours` - średnia liczba godzin w miesiącu spędzona w biurze,
* `time_spend_company` - liczba lat spędzonych w firmie,
* `work_accident` - wypadek przy pracy (`1` - tak, `0` - nie),
* `left` - czy pracownik się zwolnił (`1` - tak, `0` - nie),
* `promotion_last_5years` - awans w ciągu ostatnich 5 lat (`1` - tak, `0` - nie),
* `sales` - dział zatrudnienia,
* `salary` - wysokość zarobków (grupy).

**Polecenia:**
1. Jaka jest minimalna i maksymalna ocena poziomu satysfakcji pracownika?
2. Jaka jest średnia ocena pracownika (`last_evaluation`), a jaka mediana?
3. Ile jest/było pracowników w poszczególnych działach? Sporządź odpowiedni wykres słupkowy.
4. Podaj liczbę pracowników, którzy zwolnili się w każdym dziale oraz jaki to procent danego działu.
5. Podaj liczbę pracowników, którzy otrzymali awans w każdym dziale oraz jaki to procent danego działu.
6. Wyznacz macierz korelacji dla kolumn ramki `hr` z uwzględnieniem zarobków (dokonaj konwersji danych kategorycznych na numeryczne) i utwórz mapę ciepła. Powtórz analizę osobno dla pracowników, którzy się zwolnili, oraz tych, którzy zostali.
7. Zbadaj związek między poziomem satysfakcji a odejściem z firmy:
   * oblicz korelację między poziomem satysfakcji a decyzją o odejściu,
   * za pomocą testu t-Studenta oceń, czy istnieją statystycznie istotne różnice w poziomie satysfakcji między obiema grupami.
8. Czy wynagrodzenie wpływa na rotację pracowników? Sprawdź to na trzy sposoby:
   * wizualizacja rozkładu wynagrodzenia w zależności od rotacji (wykres słupkowy),
   * obliczenie procentu pracowników, którzy odeszli, w różnych grupach płacowych,
   * test chi-kwadrat.
9. Za pomocą testu t-Studenta porównaj poziom satysfakcji między pracownikami, którzy otrzymali awans, a tymi, którzy go nie otrzymali.
10. Skategoryzuj ocenę poziomu satysfakcji na 6 przedziałów: $[0, 0.2, 0.4, 0.6, 0.8, 0.9, 1.0]$ o nazwach: `Lowest`, `Low`, `Average`, `Good`, `High`, `Highest`. Przedstaw na wykresie słupkowym liczbę pracowników, którzy się zwolnili i którzy zostali, w podziale na te kategorie.

### 4. Analiza ruchu sieciowego (`UNSW-NB15`)
Wczytaj zbiór `UNSW_NB15_training-set.csv` i usuń ewentualne rekordy z brakami danych (`NaN`):
1. Oblicz liczebność ruchu prawidłowego (`label=0`) oraz ruchu związanego z atakami (`label=1`).
2. Dla kolumny `sbytes` oblicz: średnią, medianę, odchylenie standardowe oraz wartości ekstremalne (minimum i maksimum).
3. Przedstaw na histogramie wartości kolumny `sbytes` dla ruchu normalnego i ataków.
4. Dodaj kolumnę `log_sbytes = np.log1p(sbytes)` i przedstaw jej rozkład na wykresie dla obu grup.
5. Wylosuj po 2000 rekordów z każdej grupy i przeprowadź dwustronny test t-Studenta dla prób niezależnych dla zmiennej `log_sbytes`. Zweryfikuj hipotezę, czy sam wolumen przesłanych danych od źródła do celu jest wiarygodną metryką do budowy reguł detekcyjnych.