# Polskie Radio - Zegar

Ten projekt to próba odtworzenia systemu mierzenia czasu używanego w Polskim Radiu. Składa się on z zegara analogowego (wzorowanego na tarczach firmy Favag) oraz cyfrowego, wzorowanego na tablicach LEDowych. Aplikacja zegarowa zawiera także GUM - sygnał ogłaszania pełnej godziny (skrótowiec od "Głównego Urzędu Miar (i Wag)").

Zegar pobiera czas z tego ustawionego w komputerze - w przypadku domyślnej konfiguracji systemów operacyjnych będzie to oznaczało, że aplikacja zegara będzie pokazywać dokładną godzinę co do sekundy. 

### GUM
Sygnał GUM-u można włączyć poprzez przełącznik w prawym górnym rogu okna aplikacji zegarowej. Po włączeniu funkcji, aplikacja będzie, podobnie jak ma to miejsce w rozgłośniach Polskiego Radia, ogłaszać pełną godzinę poprzez wyemitowanie sygnału czasu składającego się z 6 pików: 5 oznajmiających ostatnie 5 sekund mijającej godziny oraz ostatni, wydłużony sygnał, którego początek oznacza punktualnie nową pełną godzinę. 

### Dostępne parametry adresowe
`antena=1` - przesuwa dźwięk GUM-u o 1 sekundę do przodu / kompensacja opóźnienia FM - pełna godzina anonsowana jest dłuższym pikiem o godz xx:59:59. Jest to mechanizm stosowany w Polskim Radiu - dzięki takiemu przesunięciu słuchacz odbierający rozgłośnię poprzez FM usłyszy pik o pełnej godzinie.

`gum-test=1` - aktywacja pików testowych - Zegar po zaznaczeniu opcji GUM wydaje również 30 pików kontrolnych: od xx:59:15 do xx:59:45 oraz od xx:29:15 do xx:29:45.

## [Uruchom zegar](https://maksmotyka.github.io/PR-Clock/)
