---
dg-publish: true
tags:
  - tomas
  - web
  - databaze_a_web
---
## Externí Materiály
[Procvičení JS DOM](https://www.jschallenger.com/javascript-dom-exercises/)
[Procvičení JS Základu](https://www.jschallenger.com/javascript-basics)


[Poznamky z Vyhledavani ve videu](https://cdn.tom-nguyen.dev/Video_retrieval_exam.pdf)
## Otázky

> [!DANGER] Pozor
> Nepokrývám zde všechny témata, jelikož jsou pro mě jasná, nebo si osobně myslím, že v dalším mém termínu (Září) nebudou.
### Principy www, HTML, XHTML, HTML5 a CSS
-  Vytvořit statickou webovou stránku pomocí HTML, HTML5 v rozsahu osobního blogu, či e-shopu
-  Na příkladu ukázat výhody HTML5 sémantických tagů
-  Na příkladu ukázat využití HTML formulářů včetně validace vstupních polí
-  Vysvětlit principy fungování CSS: syntaxe, specificita selektorů, vložení do stránky
-  Vytvořit responzivní layout stránky v rozsahu: menu, hlavní obsah se sloupci, patička
### [[Návrhové vzory|Architektury, základní principy, návrhové vzory a techniky webových aplikací]]
-  Vysvětlit použití návrhových vzorů: Front Controller, MVC/MVP, MVVC

### [[Programování na straně klienta, JavaScript, standardní API v prohlížeči]]
-  Napsat klientský kód (JavaScript), který v reakci na událost provede dotaz na server, zpracuje odpověď a modifikuje DOM
-  Uvést příklady standardních API dostupných v prohlížeči
-  Vysvětlit a použít mechanizmy pro asynchronní programování v JavaScriptu: callbacks, promises, async/await, event loop

### API webových aplikací a webové služby (bylo na minulém termínu, snad nebude znova :D)
-  Vysvětlit základní principy REST API
-  Popsat úrovně REST API
-  Popsat REST API pomocí OpenAPI
-  [[GraphQL|Položit dotaz v GraphQL, popsat výhody a nevýhody GraphQL]]

### Single-page aplikace, udržování stavu a uživatelské relace (Popsat REACT)
-  Vysvětlit princip fungování single-page aplikací
-  Popsat možnosti udržování stavu pro webové aplikace v kontextu single-page aplikací

### Programování na straně serveru, [[CGI|CGI a CGI-like aplikace]]
-  Vysvětlit fungování CGI a CGI-like aplikací
-  Popsat možnosti udržování stavu pro webové aplikace a využití uživatelských relací
-  Na příkladu demonstrovat [[PHP#PHP Interleaving|PHP interleaving]]
-  [[PHP#Příklad PHP stránky|Vytvořit jednoduchou stránku v PHP, s využitím HTTP wrapperu a připojením k SQL databázi]]

### Základy bezpečnosti webových aplikací
-  Vysvětlit vztah HTTPS a HTTP, popsat výhody
-  Na příkladu (JWT) vysvětlit použití autentizačních tokenů
-  Identifikovat a popsat základní bezpečností rizika webových aplikací

### [[Recommender Systems|Doporučovací systémy]] [🔗](https://www.ksi.mff.cuni.cz/~peska/vyuka/nswi166/)
-  Vysvětlit typické workflow doporučovacích systémů a popsat typické vstupy a výstupy
-  Popsat problémy, které způsobuje dynamičnost doporučovacího procesu (např. cold start, new item problem, online model updates)
-  Vysvětlit princip fungování, výhody a nevýhody kolaborativního filtrování
-  Vysvětlit funkci jednoduchých algoritmů (user/item-based KNN, varianty faktorizace matic) [📹](https://www.youtube.com/watch?v=ZspR5PZemcs)
	- ![[Pasted image 20240827140243.png]]
-  Vysvětlit princip fungování, výhody a nevýhody content-based a knowledge-based doporučování
-  Vysvětlit cíle, rozdíly a omezení v offline/online/user-studies hodnocení doporučovacích systémů a uvést typické hodnotící metriky

### Vyhledávání na webu a v multimediálních databázích 
-  [[Booleovský model|Popsat booleovské a vektorové modely, word2vec]]
-  [[Vyhledávání Hypertext, Ranking, PageRank|Popsat vyhledávání v hypertextu, ranking, PageRank]]
-  [[SEO|Vysvětlit optimalizaci webových stránek pro vyhledávače]]
-  Popsat metrické indexování podobnosti (filtrování pomocí pivotů, maticové, stromové, hašované a hybridní indexy) [[Metricke indexovani podobnosti]]
-  Uvést základní formáty spojené s vizuálními daty (konkrétně BMP, JPEG, MP4) [[Zakladni formaty spojene s vizualni daty]]
-  Vysvětlit základní principy komprese videa [[Komprese videa]]
-  Popsat algoritmy detekce střihů ve videu pomocí podobnosti snímků a konvolučních sítí [[Detekce strihu]]
-  Formalizovat a vysvětlit základní podobnostní model (deskriptor, funkce podobnosti, Kosinova a Euklidovská vzdálenost) [[Podobnostni model]]
-  Vysvětlit principy kombinace více modelů (early/late fusion) [[Kombinace vide modelu (multi-modal)]]
-  Vysvětlit způsob vyhledávání a klasifikace v obrázkové databázi na základě textu s využitím neuronové sítě CLIP [[CLIP]]
-  Popsat techniky vizualizace výsledků hledání v gridu pomocí různých technik zobrazení rankované množiny [[Self sorting map + SOM]]
-  Popsat a vysvětlit možnosti zobrazení obrázkových dat pomocí SOM (self-organizing map), Popsat algoritmus řazení obrázkových dat ve 2D gridu (self-sorting map) [[Self sorting map + SOM]]
-  Popsat techniky vyhodnocování efektivity vyhledávacího modelu (zejména pojmy přesnost, úplnost, mAP, F1-score), Popsat možnosti vyhodnocování efektivity interaktivních systémů [[Vyhodnocovani efeketivity vyhledavaciho modelu]]