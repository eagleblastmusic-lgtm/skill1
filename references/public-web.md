# Public web experience

## PURPOSE / USE WHEN

Prowadź premium public websites, marketing/landing pages, editorial, cinematic web oraz prezentację sztuki i produktu. Jednostką projektu jest dokument z narracją i następną decyzją użytkownika. Pracę w private app prowadzi [application.md](application.md); zmieniany wybór, cena, upload/proof lub zakup dodają [commerce.md](commerce.md).

## SOURCES / REQUIRED INPUTS

Norma: [WEB Canon](canon-web.md) oraz dziedziczone Rule IDs z [APP Canon](canon-app.md). Ustal realną ofertę, intencję strony, public/private/index policy, źródło content/page patterns, real assets i docelową konwersję. Wspólny brief i odbiór określa [premium-ui](../SKILL.md). Wybierz sekcje odpowiednie do delty, domykając ich zależności.

## DECISION RULES / EXECUTION GUIDANCE

### PREMIUM VISUAL QUALITY ≠ VISUAL COMPLEXITY — APP UI04, UI06; WEB WC04, WMO01, WMO06

Jakość buduj przez autorski charakter, mocną kompozycję, właściwy rytm tekstu/obrazu i precyzję stanów. Więcej blur, glow, gradients, WebGL, video, scroll-jacking, animacji czy 3D nie jest kryterium premium. Zanim dodasz efekt, nazwij informację lub interakcję, którą wnosi, i sposób oceny tej wartości. Jeśli dobre zdjęcie, typografia albo układ realizują cel, wykorzystaj je.

### Brand character i art direction — APP UI01–UI07; WEB IA01–IA03, WC01–WC04, WRP01, WRP04

- Przełóż charakter marki na konkretne relacje: co jest obiektem uwagi, jaką rolę ma fotografia, jaki kontrast skali niesie tekst, jakie materiały/akcenty i ton podpisów pasują do oferty. „Luksusowy” bez tych decyzji nie jest briefem wykonawczym.
- Opisz mechanizm zaakceptowanych referencji: np. całość dzieła z rzeczowym podpisem i dostępnym wyborem albo zbliżenie materiału wyjaśniające różnicę wariantów. Nie odtwarzaj cudzych assets, copy i rozpoznawalnego layoutu marki.
- Wykorzystaj źródło tokens i page patterns. Dla nowej powierzchni ustanów potrzebne role u rzeczywistego ownera; dla istniejącej zmień ich konsumentów spójnie. Nie uzyskuj nowej tożsamości przez serię niezależnych lokalnych override.
- Ustal, co czytelnik ma zrozumieć w pierwszym widoku i jak przejść dalej. Fakty oferty i materiały mają rzeczywistych owners; brak dowodu nie staje się certyfikatem, opinią klienta ani liczbą w hero.

### Composition, spacing i storytelling — APP UI04, LY04–LY05; WEB IA01–IA06, WC03–WC04, CRO02–CRO04

- Wyznacz główny komunikat, obiekt uwagi i dominującą akcję. Zbuduj różnicę skali pomiędzy leadem, sekcją, body i caption; kolejne nagłówki nie konkurują wszystkie z hero.
- Ustal wspólne osie, proporcje kolumn, szerokości czytania i relację tekst–obraz. Asymetria potrzebuje stabilnych punktów odniesienia. Whitespace oddziela role i grupy; przypadkowe wielkie przerwy nie tworzą rytmu.
- Każda sekcja wnosi informację, dowód, porównanie albo decyzję. Dobierz sekwencję do intencji: całość → detal → wyjaśnienie → wybór jest użyteczna, gdy odbiorca poznaje obiekt; gotowy do działania ma równoległą krótką drogę.
- Dobierz wzorzec do treści: galeria eksponuje obraz i kontekst; editorial utrzymuje lekturę i pochodzenie; oferta technologiczna pokazuje realny skutek użycia. Nie wciskaj każdej sekcji w tę samą kartę.
- Kategorie, headings, captions i etykiety linków tłumaczą cel. Szczegół może być disclosure; warunek potrzebny do decyzji pozostaje odnajdywalny przed zobowiązaniem.

### Typography — APP TY01–TY07; WEB WT01–WT06

- Przypisz rzeczywiste treści do ról display/lead/body/caption/price. Sprawdź measure, interlinię, wagę, tracking i łamanie długich tytułów. Fluid scale ma zachować różnicę poziomów przy zoomie i na narrow; nie dopasowuj tekstu do jednego screenshotu.
- Zweryfikuj realne font files, używane wagi/osie, licencję i glify wszystkich locale, w tym polskie znaki i waluty. Dodatkowy font potrzebuje roli; variable font dobieraj do rzeczywiście używanych osi/wag.
- Sprawdź fallback metrics i cold/slow/failure loading: komunikat, menu i CTA są czytelne, układ nie gubi rytmu po swapie. Priorytet pobierania wynika z użycia na zmienionej stronie.

### Imagery, crop, media i produkt — WEB WM01–WM06, WP04–WP05, WC02

- Dla każdego medium ustal source/version, prawa, funkcję, alt/caption, crop/focal point oraz pochodną do faktycznego slotu. Publiczna pochodna, archiwalny oryginał i prywatny materiał klienta mają różne role.
- Obejrzyj całość produktu, detal i potrzebny kontekst skali. Kampanijny crop może nadawać charakter, ale nie zastępuje wiernego widoku sprzedawanego obiektu. Oznacz wizualizację; rama, margines i skala odpowiadają aktualnie prezentowanemu wariantowi.
- Dobierz mobile crop świadomie. Sprawdź `srcset`/`sizes`, DPR, rzeczywiście pobrane `currentSrc`, rezerwację miejsca, ostrość/detal oraz awarię decode/asset. Placeholder nie stanowi finalnego materiału do premium acceptance.
- Potwierdzony LCP otrzymuje potrzebny zasób wcześnie; nie ukrywaj go za wejściową dekoracją. Pozostałe media dostarczaj według wartości i kosztu. Profiluj realny materiał, zamiast wnioskować o jakości z nazwy kodeka/CDN.
- Dla filmu zaprojektuj poster, odmowę autoplay, pause/controls i potrzebne alternatywy treści. Dla P3/HDR lub dodatkowego toru obrazu sprawdź cały pipeline i zwykły SDR wariant. Web preview nie obiecuje proofu koloru druku.

### Responsive/mobile i interaction — APP CO02–CO06, UX01–UX07; WEB RS01–RS06, WR05, WA11Y02–WA11Y05

- Zaprojektuj kolejność treści i decyzji na narrow, a następnie kompozycję większych szerokości. Gdy menu, nagłówek lub panel wyboru przestają działać, zmień wzorzec przy tej granicy; sprawdź obie jej strony z długą treścią.
- Zachowaj main task, czytelny crop i akcję w landscape/tablet, desktop i ultra-wide. Duży ekran nie oznacza nieograniczonej szerokości akapitów; mobile nie jest pomniejszonym desktopem.
- Sticky CTA, consent, safe areas, browser chrome i klawiatura mają wspólny kontrakt zajmowania przestrzeni. Testuj focus, zoom i koszt/summary pod nakładającymi się warstwami; scena nie wymaga pełnej wysokości viewportu bez potrzeby.
- Menu/disclosure/forms mają jasny skutek, stan i drogę powrotu. Touch/pointer i keyboard wykonują tę samą istotną czynność; drag/hover nie mogą być jedynym sposobem. URL, history/back/forward i focus zachowują kontekst decyzji.

### Motion, cinematic enhancement i graceful fallback — APP MO01–MO07, CO06; WEB WMO01–WMO06, WR02, WP01, WP03–WP06

| Warstwa | Decyzja wykonawcza |
| --- | --- |
| Baza | Semantyczne sekcje, obraz/poster, tekst, linki i działający next action istnieją bez zaawansowanej sceny. |
| Enhancement | Ruch podkreśla zmianę informacji, orientację albo materiał; statyczna sekwencja zachowuje znaczenie. |
| Zaawansowana scena | Canvas/WebGL/WebGPU dodaj wyłącznie dla nazwanej wymaganej zdolności, z budżetem, ownerem zasobów i HTML alternatywą. |

- Zacznij od istniejącego motion systemu lub prostszego mechanizmu, który wystarcza. Konkretne API sprawdź na wspieranych browserach; branding biblioteki nie dowodzi wsparcia. Porównanie faktury papieru może wymagać dobrego zbliżenia, a obrót przestrzennego produktu może uzasadniać scenę.
- Narracja nie opóźnia treści/CTA ani ukończonej nawigacji. Zwykły scroll, anchors, skip, history i focus działają. Reveal nie przechowuje ważnego tekstu niewidocznego do zakończenia pobierania JS.
- Reduced motion daje świadomy statyczny wariant także po zmianie preferencji w sesji. Pause/stop oraz bezpieczne media ocenia się osobno. Awaria engine, autoplay albo brak wsparcia prowadzą do użytecznej bazy.
- Nazwij lifecycle timeline/RAF/listeners/GPU: wejście, przerwanie, hidden/offscreen, powrót i disposal po opuszczeniu trasy. Testuj context/device loss i słabsze urządzenie wraz z menu oraz wyborem produktu; isolated scene demo nie wystarcza.
- Jeśli bazowy produkt rzeczywiście wymaga JS, pokaż jego wymaganie i dostępną alternatywę uzgodnioną w repo. Działająca droga konwersji pozostaje dostępna bez dekoracyjnej warstwy; nie symuluj wykonania konfiguracji lub zakupu statycznym przyciskiem.

### Dokument, conversion clarity, a11y, SEO i performance — WEB WA01–WA05, WR01–WR06, SEO01–SEO08, CRO01–CRO06, WA11Y01–WA11Y06, WP01–WP08

- Zachowaj semantyczną zależność headings, landmarks i treści niezależnie od wizualnej wielkości tekstu. Nawigacja używa rzeczywistych linków, akcja właściwej kontrolki; istotna informacja nie istnieje wyłącznie w canvas/video.
- CTA nazywa następny skutek i wynika z aktualnego wyboru. Oferta, koszty, terminy i ograniczenia są realne; wizualne zaufanie uzupełnia sprawdzalny kontakt, materiały i warunki. Szczegóły zmienianego buying flow należą do commerce.
- Zakres dostępności obejmuje zmieniony pełny proces: semantic controls, tekstowe błędy, keyboard/focus, media alternatives, zoom/reflow i screen reader. Automatyczny skan nie rozstrzyga wszystkich tych własności.
- Dla zmienionych publicznych tras sprawdź rzeczywisty HTML/headers/status, direct entry/refresh, crawl links, canonical/index policy oraz zgodność metadata/schema z treścią. Nie wymieniaj działającego renderer/CMS dla samej etykiety premium.
- Przypisz koszt assetów, JS, fontów i third parties do przyjętego scenariusza/budżetu. Ustal privacy/consent trigger dla nowych odbiorników. Cold/warm, cache i slow/failure mają własne wyniki; progi CWV i rozdział field/lab pozostają w WP01–WP02.

## VERIFICATION / COMPLETION — WEB VQA01–VQA06, WTE01–WTE06; APP TE04

- Obejrzyj rzeczywistą stronę z końcowymi assets/fontami: first view i full page. Oceń hierarchy/composition, relację tekst–obraz, rytm sekcji, spacing/alignment, crop/detal i jasność następnej decyzji.
- Zbadaj narrow, tablet/landscape, desktop/ultra-wide oraz okolice zmienionych breakpointów z właściwymi fixture: długie locale, brak medium, loading/empty/error/validation i slow network. Nie zastępuj rzeczywistej klawiatury telefonu samą emulacją viewportu.
- Wykonaj nawigację, menu/form/wybór, back, sticky/consent i focus po działaniu. Sprawdź statyczną/reduced-motion bazę oraz błędy mediów. Deterministyczny diff layoutu i real-time motion/font-loading wymagają odrębnej oceny.
- Wyjaśnij ważne diffs względem przyjętego wzorca. Sprawdź właściwe a11y, SEO i performance contracts na aktualnej ścieżce; local browser nie dowodzi deployed adaptera, field CWV ani conversion uplift.

Zakończenie i mapa dowodów: [premium-ui](../SKILL.md). Niespełnione kryterium premium pozostaje otwarte mimo poprawnego builda; zakres bez realnego urządzenia, final assets lub deployment evidence ma nazwane ograniczenie.
