# Polskie Radio - Zegar

Ten projekt to próba odtworzenia systemu mierzenia czasu używanego w Polskim Radiu. Składa się on z zegara analogowego (wzorowanego na tarczach firmy Favag) oraz cyfrowego, wzorowanego na tablicach LEDowych. Aplikacja zegarowa zawiera także tzw. GUM - sygnał ogłaszania pełnej godziny (skrótowiec od "Głównego Urzędu Miar (i Wag)").

### Zegar analogowy
Zegar analogowy wzorowany jest na tarczy czasomierza Favag Impulse Broadcast, używanych w budynkach Polskiego Radia do wskazywania czasu. Zegary te sterowane są impulsowo poprzez centralę ustalającą puls. 

### Zegar cyfrowy
Zegar cyfrowy wzorowany jest na tablicach ledowych wyświetlających godzinę, używanych w budynkach rozgłośni jako zapasowy system wskazywania czasu w przypadku awarii systemu analogowego. 

### Sygnał foniczny czasu (tzw. "GUM")
Sygnał GUM-u można włączyć poprzez przełącznik w prawym górnym rogu okna aplikacji zegarowej. Po włączeniu funkcji, aplikacja będzie, podobnie jak ma to miejsce w rozgłośniach Polskiego Radia, ogłaszać pełną godzinę poprzez wyemitowanie fonicznego sygnału czasu składającego się z 6 pików: 5 oznajmiających ostatnie 5 sekund mijającej godziny oraz ostatni, wydłużony sygnał, którego początek oznacza punktualnie nową pełną godzinę. 

- `xx:59:55` - `xx:59:59` - Sygnał o długości 100ms
- `xx+1:00:00` - Sygnał o długości 300ms

Aplikacja emituje podobną sekwencję sygnału czasu również w momencie upłynięcia połowy godziny, tzn. w zakresie `xx:29:55` - `xx:30:00`. 

### Sposób ustalania wzorca czasu
Aplikacja została wyposażona we własny backend API, który komunikuje się z serwerem NTP Głównego Urzędu Miar i Wag (tzw. `Tempus`). W momencie uruchomienia aplikacji ta odpytuje API o dostrojenie się do sygnału czasu przekazywanego przez GUM. API próbuje uzyskać informację najpierw od serwera głównego (`tempus1`). Jeśli to się nie uda, próbuje uzyskać informacje od serwera zapasowego (`tempus2`).

W przypadku niemożliwości połączenia się aplikacji z API lub brakiem informacji od serwerów GUM w API, aplikacja próbuje uzyskać informacje o wzorcu czasu z publicznie dostępnych usług API (`WorldTimeAPI`). 

Gdy wszystkie powyższe metody łączenia zawiodą, aplikacja pobiera czas z tego ustawionego w systemie użytkownika - w przypadku domyślnej konfiguracji systemów operacyjnych będzie to oznaczało, że aplikacja zegara będzie pokazywać godzinę z dokładnością +/- 1 sekundy (biorąc pod uwagę naturalny odchył zegara systemowego i niestałe dostrajanie się do wzorca czasu podanego w systemie użytkownika). 

Stan połączenia raportowany jest zarówno poprzez "dymek" widoczny w lewym górnym rogu strony, jak również poprzez konsolę w narzędziach deweloperskich przeglądarki. 

### Dostępne parametry adresowe
`antena=1` - przesuwa dźwięk GUM-u o ok. 700ms - 1 sekundę do przodu / kompensacja opóźnienia FM - pełna godzina anonsowana jest dłuższym pikiem o godz xx:59:59. Jest to mechanizm stosowany w Polskim Radiu - dzięki takiemu przesunięciu słuchacz odbierający rozgłośnię poprzez FM usłyszy pik o pełnej godzinie.

`gum-test=1` - aktywacja pików testowych - Zegar po zaznaczeniu opcji GUM wydaje również 30 pików kontrolnych: od `xx:59:15` do `xx:59:45` oraz od `xx:29:15` do `xx:29:45`.

## [Uruchom zegar](https://maksmotyka.github.io/PR-Clock/)
