# Lab 2 - Parsowanie i analiza logów OpenSSH

## Dane wejściowe

Do wykonania zadań wymagany jest plik:
* `OpenSSH_2k.log`

## Zadania do wykonania

1. **Wczytanie i parsowanie logów**
   * Korzystając z biblioteki `pygrok`, `parse`, `re` lub innej dowolnej, przenieś plik z logami do obiektu `DataFrame`, a treść logu zapisz do kolumny `msg`.

2. **Analiza braków danych**
   * Bazując na ramce danych z zadania 1, sprawdź, w ilu rekordach występują wartości puste (`None`).

3. **Aktywność procesów**
   * Przygotuj zestawienie liczby logów wygenerowanych przez poszczególne procesy (np. `sshd`, `ftpd`, `su`).

4. **Konwersja daty i czasu**
   * Na bazie przygotowanego wcześniej `DataFrame`, przekonwertuj kolumnę z datą i czasem ze zwykłego tekstu na typ `datetime` (w pliku nie podano roku - wstaw rok `2025`).

5. **Ekstrakcja informacji o atakach**
   * Wykorzystując dowolną bibliotekę (`pygrok`, `parse`, `re`), wyciągnij z kolumny `msg` informacje o adresie IP i nazwie użytkownika dla komunikatów, które zawierają frazy `"Failed password"` oraz `"Invalid user"`.

6. **Identyfikacja zagrożeń i eksport**
   * Korzystając z metod filtracji i grupowania, zidentyfikuj i wyświetl zestawienie:
     * top 5 adresów IP generujących najwięcej błędów uwierzytelniania,
     * top 5 najczęściej atakowanych nazw użytkowników (np. `root`, `admin`).
   * Wyniki wyeksportuj do pliku `JSON`.