# Application experience

## PURPOSE / USE WHEN

Prowadź projekt desktop apps, authenticated web apps i productivity UI, w którym jakość wynika z wykonywania pracy, czytelnej gęstości, selection i przewidywalnych komend. Publiczną narrację prowadzi [public-web.md](public-web.md); zakup i konfigurację prowadzi [commerce.md](commerce.md), tylko gdy są dotknięte.

## SOURCES / REQUIRED INPUTS

Norma: [APP Canon](canon-app.md). Dla web app dobierz [WEB Canon](canon-web.md) do browser navigation, viewport, sesji i prywatności. Ustal bieżący core flow, ownera dokumentu/zadania, model selection, API istniejących komend, źródła wzorców i fixture. Zakres wspólnego briefu i odbioru określa [premium-ui](../SKILL.md).

## DECISION RULES / EXECUTION GUIDANCE

### Hierarchy, density i layout — APP UI04, LY01–LY06

- Wskaż centrum pracy: dokument, lista/detal, canvas albo decyzja. Przydziel pozostałym obszarom rolę nawigacji, narzędzi lub inspektora. Utility nie potrzebuje automatycznie sidebaru; edytor nie potrzebuje siatki kart dashboardu.
- Oddziel stabilną nawigację od chwilowej selection. Inspector opisuje wybrany obiekt; toolbar pokazuje działania właściwe temu kontekstowi. Primary action i stan dokumentu pozostają czytelne przy większej ilości metadanych.
- Gęstość dobierz do częstotliwości pracy i porównywania danych. Grupuj po znaczeniu, ogranicz zbędny chrome, stosuj wspólne osie tekstu i liczb. Compact i comfortable korzystają z tego samego istniejącego kontraktu; mniejszy tekst nie zastępuje decyzji o hierarchii.
- Dla paneli określ kolejność collapse, minimum użytecznej treści, resize, scroll owner i powrót do pracy po zamknięciu overlay. Na szerokim ekranie wykorzystuj miejsce do równoległej pracy, zachowując czytelny measure.

### Typography i język powierzchni — APP UI01–UI03, UI05–UI07, TY01–TY07

- Przypisz role tekstu do nazw widoku, kontrolek, treści dokumentu, metadanych, danych liczbowych i kodu. Wybrane role mają wspólne line-height, wagę i spacing; nie dostrajaj każdego feature osobno.
- W tabeli stabilizuj aktualizowane liczby, precision, units i locale. Długą nazwę pokaż przez wrapping lub istniejący mechanizm ujawnienia; nie pozwól, by jedyna nazwa albo błąd zniknęły w ellipsis.
- Dobierz kontrast skali i materiałów do centrum pracy. Efekt na chrome nie może zagłuszać wybranego obiektu. Sprawdź pary powierzchnia/tekst dla obsługiwanych theme oraz opaque/high-contrast wariant dynamicznego materiału.
- Dla fontu produktu potwierdź realne renderowanie, fallback, języki i prawo do dystrybucji. Zachowaj spójny optyczny ciężar ikon i relację icon/label.

### Selection, commands i focus — APP UX05, CO01–CO03, AC02–AC05

- Nazwij scope selection, stable identity, single/multi/range wybór i zachowanie po filtrowaniu, usunięciu lub odświeżeniu danych. Selected, hovered i focused mają odrębne znaczenie; focus nie zmienia danych przez samą zmianę miejsca.
- Podepnij menu, toolbar, shortcut i palette do istniejącej operacji, jej enabled predicate i rezultatu. Sprawdź realne handlers; nie twórz drugiego modelu komend dla nowego widoku. Palette ułatwia odkrycie akcji, ale nie jest jedyną drogą.
- Przy akcji pokaż obiekt i przyczynę niedostępności. Skróty respektują Cmd/Ctrl, edytowane pole, IME i scope aktywnego widoku. Esc ma właściwy skutek dla najwyższej warstwy lub aktualnego trybu.
- W overlay określ wejście, kolejność oraz powrót focusu, także po usunięciu otwierającego obiektu. Drag/resize/canvas potrzebują dostępnego sposobu wykonania tej samej pracy, właściwego platformie.

### States, feedback i recovery — APP UX01–UX04, UX06–UX07, CO03–CO06, ST01–ST07

Wybierz reprezentatywne stany zmienianej ścieżki, nie tylko idealny ekran:

| Sytuacja | Decyzja implementacyjna |
| --- | --- |
| Pierwsze użycie / pusta kolekcja | Pokaż czynność prowadzącą do pierwszego wyniku. |
| Brak wyników po filtrze | Zachowaj filtr i pozwól go skorygować/resetować, bez mylenia z awarią. |
| Loading / refresh / partial data | Ustal, czy zachować poprzedni wynik, i oznacz jego świeżość; lokalna praca nie zamraża całego workspace. |
| Pending command | Feedback wskazuje fazę oraz obiekt; retry i kolejne wejście uwzględniają możliwy skutek poprzedniej próby. |
| Validation / error / offline / conflict | Pokaż konkretną przeszkodę i możliwy następny krok w miejscu pracy; poprawne wejścia pozostają dostępne. |
| Success / dirty / saved | Rozróżnij lokalną edycję, zaakceptowany zapis i trwały rezultat zgodnie z ownerem. |
| Cancel / close / restart | Wyjaśnij, jaka część pracy ustała, co zachowano i jak wrócić do aktualnego stanu. |

- Rozdziel stan edycji, nawigacji, query cache i zadania według istniejących owners. Wysoka częstotliwość inputu nie powinna wymuszać przebudowy całego UI.
- Wynik async publikuj tylko do właściwego obiektu i wersji. Ustal skutek szybkiej zmiany wyboru, cancel, ponownego uruchomienia, unmount oraz zakończenia starego workera. Sam abort klienta nie dowodzi cofnięcia trwałej operacji.
- Optimistic feedback rozlicza się z ownerem danych; przy odmowie pokaż aktualny wynik i możliwość poprawy. Toast nie zastępuje trwałego, lokalnego komunikatu istotnego błędu ani nie kradnie focusu.
- Destrukcyjne działanie ujawnia konkretny obiekt, zakres i nieodwracalny skutek. Użyj istniejącego undo, gdy rzeczywiście cofa tę operację; confirmation dobierz do konsekwencji. Nie obiecuj cofnięcia zewnętrznego skutku samym przyciskiem UI.

### Motion i responsive — APP MO01–MO07, LY02–LY06, AC06

- Ruch może utrzymywać orientację przy zmianie panelu, selection lub stanu. Cel nie przemieszcza się spod wskaźnika podczas kliknięcia; nowy input rozstrzyga aktualny stan mimo przerwanego przejścia.
- Dobierz zachowanie małego okna lub wąskiego viewportu do priorytetu pracy: zmiana układu/panelu zamiast obcinania potrzebnej akcji. Sprawdź resize, zoom, text scale, długie etykiety i obsługiwane tryby kontrastu/ruchu.
- W web app zastosuj WEB RS01–RS04, WR05, WA05, WS02 i WA11Y02–WA11Y06 tam, gdzie zmieniają się formularze, history, reload, reconnect lub expiry sesji. Publiczne SEO nie wynika z samego faktu użycia przeglądarki.

### Platform / shell — APP AR02–AR04, AR07, LY07, SE02, PE01–PE07, TE05

Otwieraj tę część dla zmiany dotykającej shella lub integracji OS. Potwierdź docelowy runtime i zachowanie title bar/drag regions, menu, clipboard, dialogów, deep linków lub wielu okien według zakresu. Sprawdź dirty-close, współdzielenie dokumentu, zmianę monitora/DPI i przywrócenie geometrii tam, gdzie są istotne. Nowy widok nie jest powodem wymiany shella; webowy mock IPC nie dowodzi działania jego granicy. Dla kosztownej pracy użyj istniejącego workera/transportu i jego cancel/disposal, zamiast blokować pętlę UI.

## VERIFICATION / COMPLETION — APP TE01–TE07, AC07

- W rzeczywistym target runtime oceń centrum uwagi, gęstość, align/spacing, role tekstu, selection i spójność chrome. Przejdź działanie od wejścia do wyniku; sprawdź stan po błędzie, odzyskaniu i ponownym otwarciu, jeśli trwałość jest w zakresie.
- Wykonaj dotknięte drogi komendy, keyboard/focus i overlay. Sprawdź reprezentatywną długą/dużą treść oraz małe okno, scaling/theme i tryb ograniczonego ruchu w zakresie targetu. Dla aplikacji webowej użyj właściwych VQA01–VQA06 i WTE05.
- Przy zmianie async wykorzystaj dowód wyścigu odpowiedzi, cancel/retry i opuszczenia widoku. Gdy zmiana dotyka kosztu pracy, porównaj właściwy scenariusz z przyjętym budżetem, obejmując zwolnienie zasobów.

Kryteria wspólnego zakończenia i zapisu dowodów są w [premium-ui](../SKILL.md). Brak testu shella lub wspieranej platformy ogranicza claim do faktycznie zbadanego widoku/runtime.
