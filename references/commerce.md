# Commerce decision experience

## PURPOSE / USE WHEN

Prowadź UX i implementację zmienianego wyboru produktu, wariantów, konfiguracji, ceny, upload/crop/proof, cart i checkout. Zachowaj rzeczywistą domenę repo i dojrzały silnik handlu. Ta reference nie definiuje drugiego backendu, cennika, modelu zamówień ani silnika płatności.

## SOURCES / REQUIRED INPUTS

Normy: [WEB Canon](canon-web.md), szczególnie EC/CRO/WA05/WS/WA11Y, oraz [APP Canon](canon-app.md), szczególnie UX/ST/CO/SE. Potwierdź aktualnych owners katalogu/wariantów, quote i dostępności, konfiguracji/proofa, pliku, cart/checkout oraz trwałego statusu operacji. Ustal granice rynku/waluty, privacy/retention i istniejące API wersjonowania. Publiczną art direction prowadzi [public-web.md](public-web.md); pracę wewnątrz aplikacji prowadzi [application.md](application.md). Wspólny brief i odbiór: [premium-ui](../SKILL.md).

## DECISION RULES / EXECUTION GUIDANCE

### Product selection i buying clarity — WEB EC01, EC06, IA03–IA04, CRO02–CRO04, WC02

- Rozróżnij produkt, możliwy do kupienia wariant, opcję produkcyjną oraz samą prezentację. Pobieraj dozwolone kombinacje od ownera domeny; UI wyjaśnia wykluczenie i możliwy wybór zamiast wymyślać dostępność.
- Wybór ma jasno wskazane wymagane decyzje, jednostki, materiał, skalę, konsekwencję i następny krok. Nie podmieniaj wyboru użytkownika na inny wariant bez widocznego wyjaśnienia.
- Pokaż różnicę między brakiem wyboru, niedozwoloną kombinacją, brakiem zapasu, oczekiwaniem na potwierdzenie i awarią. Dla każdego stanu określ działanie umożliwiające poprawę, zachowując zgodne wcześniejsze wybory.
- Przed zobowiązaniem ujawnij zakres ceny, estymacje, wymagane koszty i realistyczny termin. Zaufanie opiera się na sprawdzalnym pochodzeniu, materiale, podsumowaniu i warunkach; nie dodawaj fikcyjnej scarcity, opinii ani automatycznych dodatków.

### Wariant → cena → cart — WEB EC01–EC02, EC05; APP ST01, ST03–ST06

- Podepnij prezentację ceny do istniejącego autorytatywnego quote/commerce API. Klient może pokazać oznaczoną estymację, ale nie rozstrzyga kwoty do zapłaty, podatku, rabatu ani zapasu.
- Powiąż wybrane opcje, podgląd, dostępność, quote i wysyłany cart item z tym samym aktualnym snapshotem. Korzystaj z istniejących identyfikatorów produktu/wariantu, wersji konfiguracji i pliku/proofa, ilości, market/currency oraz quote/expiry tam, gdzie należą do kontraktu; nie ustanawiaj obok nowego schematu prawdy.
- Zmiana wyboru lub danych wejściowych unieważnia zależny quote/approval zgodnie z domeną. Stara odpowiedź nie aktualizuje ceny ani przycisku dla nowego wariantu. Pending podaje, co jest przeliczane; poprzednia cena nie udaje aktualnie potwierdzonej.
- Przed przejściem dalej serwer weryfikuje wymagane wybory, dostępność i koszt dla bieżącego kontekstu. Expired quote, zmiana zapasu/market/currency lub rabatu prowadzi do widocznego przeliczenia i aktualnego podsumowania przed płatnym zobowiązaniem.
- Sprawdź zawartość koszyka po przyjęciu przez ownera, a następnie zachowanie snapshotu na granicy checkoutu. Sam klik albo lokalna optimistic linia nie są dowodem utworzenia zamówienia.

### Async, stale responses i retry — APP UX02–UX03, UX07, ST04–ST07, CO06; WEB WA05, CRO05

- Tożsamość żądania obejmuje kontekst, którego wynik dotyczy. Wykorzystaj istniejącą wersję/operation ID; po zmianie wyboru, pliku, sesji lub widoku publikuj tylko aktualny wynik, również po odpowiedziach w złej kolejności.
- Cancel ma określony skutek w UI i po stronie zadania. Jeśli backend mógł już wykonać trwałą operację, recovery odczytuje jej status; timeout nie dowodzi braku skutku i nie uzasadnia ślepego powtórzenia płatności/cart/job.
- Retry zachowuje zgodne dane i korzysta z kontraktu idempotencji istniejącej domeny. Reload, reconnect, dwie karty i session expiry nie tworzą konkurujących snapshots. Zwalniaj subskrypcje i zasoby widoku, zachowując domenowe zadanie zgodnie z jego lifecycle.

### Upload → crop → proof → production — WEB WM02–WM03, WM06, EC05, WS07–WS08; APP AR02–AR04, ST03–ST05

- Odwzoruj fazy faktycznego pipeline: wybór lokalnego pliku, transport, weryfikacja/decode, przygotowanie podglądu, edycja/crop i gotowość/approval. Odróżnij progress transferu od poprawności pliku; nie ogłaszaj print-ready po samym uploadzie.
- Pokaż wymagania pliku przed wyborem, realny postęp/fazę oraz błąd z drogą poprawy. Obsłuż przerwanie, timeout, odrzucony/uszkodzony/za duży plik i ponowne wejście. Po zmianie pliku wynik starego decode/preview nie staje się podglądem nowego.
- Crop/proof wiąże tożsamość i wersję pliku z transformacją, opcjami produkcyjnymi i zależną akceptacją. Zmiana którejkolwiek zależności wymaga aktualnego proofa/quote według ownera; stara akceptacja nie przechodzi automatycznie na nowe dane.
- Serwer rozstrzyga dopuszczenie pliku i stan produkcji. UI korzysta z istniejącej izolacji decode, limitów i prywatnych pochodnych; nie omija walidacji przez client-side preview. Linki/logi nie ujawniają prywatnego oryginału ani sekretów.
- Podgląd przedstawia aktualny crop, materiał i rozmiar, z dostępnym widokiem całości. Wizualizacja i webowa barwa nie udają zatwierdzonego proofu druku bez rzeczywistego kontraktu procesu.

### Cart, checkout i confirmation — WEB EC02–EC04, WS09, CRO05–CRO06, WA11Y03

- Rozróżnij koszyk, checkout, próbę płatności, potwierdzone zamówienie i gotowość do produkcji. Powrót z success URL pokazuje autorytatywny status; wymagane proof approval pozostaje odrębnym warunkiem.
- Przy failed/pending/niepewnym wyniku pokaż status poprzedniej próby i bezpieczny następny krok. Wykorzystaj istniejącą obsługę webhooków/reconciliation; nie odtwarzaj zamówienia, maila ani druku po podwójnym kliknięciu lub powrocie.
- Summary umożliwia sprawdzenie/poprawę wariantu, ilości, adresu i kosztów. Guest checkout pozostaje widoczny, jeśli produkt go dopuszcza. Płatne zobowiązanie ma jednoznaczny skutek.
- Confirmation pokazuje trwały numer/status, przyjęty snapshot i dalszy etap/kontakt. Stan maila nie zastępuje potwierdzenia transakcji. Zmiany/refund obsługuje rzeczywista domena, w zakresie zadania.

### Mobile, accessibility i recovery — WEB RS02–RS04, WA11Y02–WA11Y06; APP AC02–AC07

- Zachowaj powiązanie preview → wybory → aktualna cena → następny krok na narrow, bez chowania istotnego kosztu pod sticky/consent/klawiaturą. Powrót i obrót nie resetują pracy użytkownika.
- Pola i grupy wyborów mają labels, instrukcje i lokalne tekstowe błędy. Status quote/upload/cart jest dostępny bez zbędnego focus jump; summary błędów prowadzi do właściwego wyboru.
- Crop/drag ma alternatywę keyboard i pojedynczym wskaźnikiem bez dragowania. Kluczowy zakup działa bez obowiązkowego 3D/motion; focus po error, menu, proof review i powrocie z checkoutu jest przewidywalny.

## VERIFICATION / COMPLETION — WEB WTE01–WTE06, VQA04, EC04–EC05; APP TE01–TE03

Wykonaj aktualny zakres flow z realnymi owners/sandboxami, nie wyłącznie z mockiem ceny. Wybierz istniejące fixture i dowody dla istotnych granic:

| Zmieniany kontrakt | Odrębny scenariusz do sprawdzenia |
| --- | --- |
| Wybór / quote / cart | Niedozwolona kombinacja, brak zapasu, dwa quote w złej kolejności, expiry, zmiana ilości lub market; zaakceptowana linia odpowiada aktualnemu wyborowi. |
| Upload / proof | Realny decode/failure, cancel i zmiana pliku w trakcie pracy, zmiana cropu/opcji po approval, retry/reload; nieaktualny preview lub proof nie trafia dalej. |
| Checkout / trwały skutek | Success, failed/pending, timeout po możliwym skutku, status poprzedniej próby, powrót i właściwe retry; brak podwójnego skutku. Refund i webhook obejmij, gdy są w delcie. |
| Doświadczenie decyzji | Czytelne podsumowanie oraz error/recovery, aktualna cena/preview, focus/status, narrow ze sticky i klawiaturą, alternatywa crop/drag. |

Dowód domeny i oceniony stan po interakcji są odrębne. Zakończenie i zapis ograniczeń określa [premium-ui](../SKILL.md). Brak aktualnego modelu ceny/proofa lub dostępu do operatora blokuje zależny kontrakt; nie zastępuj go fikcyjną integracją i nie deklaruj kompletnego checkout/production PASS.
