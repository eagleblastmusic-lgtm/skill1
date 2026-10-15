---
name: premium-ui
description: Projektuj i implementuj premium UX/UI aplikacji desktopowych, aplikacji webowych oraz publicznych stron marketingowych, editorial i commerce, gdy wysoka jakość wizualna lub istotny redesign flow jest jawnym celem. Pomijaj backend-only, czyste SEO lub profiling oraz drobne mechaniczne poprawki bez celu redesignu.
---

# Premium experience

## PURPOSE / USE WHEN

Połącz funkcję, treść, UX i prezentację w jeden działający rezultat z ocenionym renderem. Używaj dla premium redesignu, nowej premium powierzchni, feature + premium UI, istotnej przebudowy flow, art direction, premium public web lub większej zmiany prezentacji produktu. Jawne użycie tego skilla nadal respektuje żądany rodzaj wyniku: prompt lub analiza nie uruchamia implementacji.

## DO NOT USE WHEN

Samodzielny backend bug, technical SEO, canonical, sitemap, performance profile, rename, literówka, mechaniczny CSS fix, dodanie istniejącego komponentu i zwykły bugfix bez zmiany doświadczenia nie aktywują tego workflow. Słowo w symbolu, np. `premiumPrice`, nazwa marki oraz generic research nie są triggerem. Relewantne Canony i references można wtedy czytać bez aktywacji skilla.

## REQUIRED INPUTS / SOURCES

Z aktualnego zadania, repo i przyjętych źródeł ustal:

- odbiorcę, główne zadanie, zmienianą powierzchnię i działający wynik;
- charakter marki, art direction, strukturę treści, hierarchy i dominujący język wizualny;
- autorytatywne domeny funkcji oraz źródła tokens, komponentów, typography, ikon i motion;
- realną treść i assets, prawa/wersje mediów, ich rolę oraz sposób dostarczenia;
- stany interakcji, primary action, recovery i ścieżkę konwersji;
- model spacing/rhythm, zachowanie breakpointów, cel ruchu oraz przyjęte ograniczenia performance, a11y i SEO.

Uzupełniaj tylko informacje mające wpływ na deltę. Istotnego brakującego ownera lub decyzji nie zastępuj fikcyjną domeną albo placeholderem; nazwij `SPEC_BLOCKED` dla zależnej części i wykonaj niezależny zakres.

## DECISION RULES / REFERENCES

Dobierz treść według zmienianego doświadczenia; nie czytaj wszystkich references domyślnie.

| Powierzchnia / skutek | Reference wykonawcza | Norma do celowanego odczytu |
| --- | --- | --- |
| Desktop, productivity, authenticated web app | [application.md](references/application.md) | APP UI/TY/LY/UX/CO/ST/AC; MO/PE i shell według delty. W przeglądarce także WEB RS/WR05/WA11Y/WS, gdy dotknięte. |
| Public marketing, landing, editorial, cinematic, art/product presentation | [public-web.md](references/public-web.md) | WEB WA/WR/IA/WM/WT/RS/CRO/VQA oraz właściwe WP/SEO/WA11Y/WMO; dziedziczona baza APP. |
| Wybór produktu, konfiguracja, upload/proof, cart/checkout | [commerce.md](references/commerce.md) | WEB EC/CRO/WA05/WS/WA11Y i APP UX/ST/CO/SE. Dodaj application dla zmienianej pracy aplikacyjnej lub public-web dla zmienianej publicznej prezentacji. |

Normy znajdują się w [canon-app.md](references/canon-app.md) i [canon-web.md](references/canon-web.md). References opisują HOW TO EXECUTE; oryginalne Canony pozostają WHAT MUST BE TRUE. Sprawdź binding przyjęty w repo, wyszukaj wskazane Rule IDs i przeczytaj kompletne reguły z istotnymi zależnościami. Odczyt pliku Canonu nie wymaga uruchomienia skilla. Binding wersji, provenance oraz dostęp do researchu: [SYSTEM.md](../../SYSTEM.md), wyłącznie gdy potrzebne do identyfikacji źródła.

WEB dziedziczy właściwą bazę APP; viewport zastępuje desktop minimum-window, a delivery webu zastępuje installer. Dla zwykłej strony pomiń desktop shell/IPC/update; dla desktopu z osadzonym webem oceń je według rzeczywistego targetu. Research otwieraj dla konkretnego nierozstrzygniętego mechanizmu lub trade-offu, nie jako preload.

## EXECUTION GUIDANCE

Przed kodem ustal jeden zwięzły kontrakt zmienionego flow: wynik funkcji, treść i decyzje użytkownika, kompozycja, źródła wyglądu, stany oraz kryteria odbioru. Projektuj funkcję i UI razem, korzystając z wybranej reference. Nową potrzebę design systemu wprowadź u rzeczywistego ownera z nazwą roli i wpływem na odbiorców. Efekt wizualny wybieraj dla nazwanej informacji lub interakcji.

Native agent prowadzi planowanie, implementację, debugowanie, testy i review. Ten skill nie dodaje własnego execution loop, obowiązkowego TDD, łańcucha reviewers ani delegacji.

## VERIFICATION / COMPLETION

Uruchom zmienioną ścieżkę i obejrzyj jej rzeczywisty render z właściwą treścią oraz assets w docelowym browserze/runtime. Zapisz adres lub ekran, wersję, środowisko, viewport/DPR lub scaling, fixture i stan; dodaj screenshot oraz ocenę. Dla ważnych kryteriów powiąż Rule IDs, implementację, wykonane sprawdzenie, dowód i ograniczenie w istniejącym wyniku zadania.

Oceń hierarchy, composition, rhythm, typography, spacing/alignment, imagery/crop oraz spójność stanów. Wykonaj dotknięte interakcje, keyboard/focus, responsive i motion/fallback; reference doprecyzowuje scenariusze powierzchni. Kontrole techniczne wynikają z kontraktów produktu.

Ukończenie wymaga działającej funkcji i ocenionego doświadczenia w zadeklarowanym zakresie. Build PASS nie daje visual PASS, screenshot bez oceny nie daje premium acceptance, a lab nie daje field PASS. Brak potrzebnego renderera, assets lub dowodu nazwij `BLOCKED`/`NOT_RUN`; wykrytą niezgodność nazwij `FAIL`. Konflikt przyjętej normy ujawnij wraz z regułą i wpływem, bez cichego osłabienia odbioru. Po domknięciu kryteriów zakończ, zachowując konkretne ograniczenia.
