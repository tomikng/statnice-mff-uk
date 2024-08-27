### Principy www, HTML, XHTML, HTML5 a CSS
- [ ] Vytvořit statickou webovou stránku pomocí HTML, HTML5 v rozsahu osobního blogu, či e-shopu
- [x] Na příkladu ukázat výhody HTML5 sémantických tagů ✅ 2024-08-16
- [ ] Na příkladu ukázat využití HTML formulářů včetně validace vstupních polí
- [x] Vysvětlit principy fungování CSS: syntaxe, specificita selektorů, vložení do stránky ✅ 2024-08-16
- [x] Vytvořit responzivní layout stránky v rozsahu: menu, hlavní obsah se sloupci, patička ✅ 2024-08-16
### Architektury, základní principy, návrhové vzory a techniky webových aplikací
- [ ] Vysvětlit použití návrhových vzorů: Front Controller, MVC/MVP, MVVC

### Programování na straně klienta, JavaScript, standardní API v prohlížeči
- [ ] Napsat klientský kód (JavaScript), který v reakci na událost provede dotaz na server, zpracuje odpověď a modifikuje DOM
- [ ] Uvést příklady standardních API dostupných v prohlížeči
- [ ] Vysvětlit a použít mechanizmy pro asynchronní programování v JavaScriptu: callbacks, promises, async/await, event loop

### API webových aplikací a webové služby
- [ ] Vysvětlit základní principy REST API
- [ ] Popsat úrovně REST API
- [ ] Popsat REST API pomocí OpenAPI
- [ ] Položit dotaz v GraphQL, popsat výhody a nevýhody GraphQL

### Single-page aplikace, udržování stavu a uživatelské relace
- [ ] Vysvětlit princip fungování single-page aplikací
- [ ] Popsat možnosti udržování stavu pro webové aplikace v kontextu single-page aplikací

### Programování na straně serveru, CGI a CGI-like aplikace
- [ ] Vysvětlit fungování CGI a CGI-like aplikací
- [ ] Popsat možnosti udržování stavu pro webové aplikace a využití uživatelských relací
- [ ] Na příkladu demonstrovat PHP interleaving
- [ ] Vytvořit jednoduchou stránku v PHP, s využitím HTTP wrapperu a připojením k SQL databázi

### Základy bezpečnosti webových aplikací
- [ ] Vysvětlit vztah HTTPS a HTTP, popsat výhody
- [ ] Na příkladu (JWT) vysvětlit použití autentizačních tokenů
- [ ] Identifikovat a popsat základní bezpečností rizika webových aplikací

### Doporučovací systémy
- [ ] Vysvětlit typické workflow doporučovacích systémů a popsat typické vstupy a výstupy
- [ ] Popsat problémy, které způsobuje dynamičnost doporučovacího procesu (např. cold start, new item problem, online model updates)
- [ ] Vysvětlit princip fungování, výhody a nevýhody kolaborativního filtrování
- [ ] Vysvětlit funkci jednoduchých algoritmů (user/item-based KNN, varianty faktorizace matic)
- [ ] Vysvětlit princip fungování, výhody a nevýhody content-based a knowledge-based doporučování
- [ ] Vysvětlit cíle, rozdíly a omezení v offline/online/user-studies hodnocení doporučovacích systémů a uvést typické hodnotící metriky

### Vyhledávání na webu a v multimediálních databázích
- [ ] Popsat booleovské a vektorové modely, word2vec
- [ ] Popsat vyhledávání v hypertextu, ranking, PageRank
- [ ] Vysvětlit optimalizaci webových stránek pro vyhledávače
- [ ] Popsat metrické indexování podobnosti (filtrování pomocí pivotů, maticové, stromové, hašované a hybridní indexy)
- [ ] Uvést základní formáty spojené s vizuálními daty (konkrétně BMP, JPEG, MP4)
- [ ] Vysvětlit základní principy komprese videa
- [ ] Popsat algoritmy detekce střihů ve videu pomocí podobnosti snímků a konvolučních sítí
- [ ] Formalizovat a vysvětlit základní podobnostní model (deskriptor, funkce podobnosti, Kosinova a Euklidovská vzdálenost)
- [ ] Vysvětlit principy kombinace více modelů (early/late fusion)
- [ ] Vysvětlit způsob vyhledávání a klasifikace v obrázkové databázi na základě textu s využitím neuronové sítě CLIP
- [ ] Popsat techniky vizualizace výsledků hledání v gridu pomocí různých technik zobrazení rankované množiny
- [ ] Popsat a vysvětlit možnosti zobrazení obrázkových dat pomocí SOM (self-organizing map)
- [ ] Popsat algoritmus řazení obrázkových dat ve 2D gridu (self-sorting map)
- [ ] Popsat techniky vyhodnocování efektivity vyhledávacího modelu (zejména pojmy přesnost, úplnost, mAP, F1-score)
- [ ] Popsat možnosti vyhodnocování efektivity interaktivních systémů

## Datove formaty
- [ ]  Datové formáty. 
	- [ ]  Popsat základní typy strukturovaných dat, uvést jejich reprezentanty a použití. Popsat, ve kterých situacích se který formát hodí, ukázat příklady. 
	- [ ]  Vysvětlit rozdíl mezi pojmy datový model, datový formát a datové schéma. Popsat základní vlastnosti tex- tových formátů, uvést příklady standardizačních organizací, popsat jejich fungování, uvést příklady stan- dardů definujících datové formáty. 
	- [ ]  Uvést, popsat, porovnat a použít modely a formáty pro grafová data - RDF a jeho serializace, Labeled Property Graf. Uvést, popsat a použít slovník pro definici slovníků použitelných v RDF - RDF Schema a uvést příklady použití. Uvést, popsat a použít jazyky pro dotazování a transformaci grafových dat - SPARQL, Cypher. 
	- [ ]  Uvést, popsat, porovnat a použít formáty pro stromová (hierarchická) data (XML, JSON), uvést, popsat a použít jazyky pro schémata stromových (hierarchických) dat XML Schema a JSON Schema, včetně příkladů. 9 Vysvětlit, jakým způsobem lze zajistit, že na data v JSON lze nahlížet také jako na data v RDF vhodná pro výměnu na Webu (JSON-LD). Popsat a použít jazyk pro transformaci XML dat (XSLT). 
	- [ ]  Uvést, použít a popsat formát pro tabulková data CSV a jeho specifikace. Popsat použití standardu CSV on the Web pro tvorbu schémat a zajištění, že na data v CSV lze nahlížet také jako na data v RDF vhodná pro výměnu na Webu. 
	- [ ]  Vysvětlit a ukázat na příkladech, co je to souřadnicový referenční systém v kontextu prostorových dat, a ukázat, jak lze prostorová data reprezentovat v různých formátech, zejména WKT, GML, GeoJSON a GeoSPARQL. 
	- [ ]  Vysvětlit, jak lze sémanticky popsat data pomocí RDF Schema a slovníků jako je Dublin Core či SKOS. Popsat datový model Wikidata a vysvětlit, jak se lze ve Wikidata dotazovat. 
- [ ]  Procesy zpracování dat 
	- [ ]  Popsat a na příkladu vysvětlit datové operace data selection, data projection, data summarization, data re- duction, data lifting a data lowering. 
	- [ ]  Vysvětlit pojem datové kvality a její důležitost pro uživatele dat. 
	- [ ]  Uvést příklady dimenzí datové kvality a jejich měření. 
	- [ ]  Na zvoleném příkladu vysvětlit data provenance a ten popsat pomocí PROV-O ontologie. 
- [ ]  Katalogizace dat, metadata 
	- [ ]  Vyjmenovat druhy metadat a uvést jejich význam. 
	- [ ]  Popsat význam a využití datového katalogu. 
	- [ ]  Vysvětlit, jak je možné realizovat datový katalog pomocí DCAT (Data Catalog Vocabulary). 
	- [ ]  Na příkladu ukázat použití DCAT - zejména třídy dcat:Dataset, dcat:DataService, dcat:Distribution a dcat:Catalog. 
- [ ]  Sémantický popis dat, slovníky 
	- [ ]  Popsat vznik a řešení problému datových sil. 
	- [ ]  Popsat výhody využití kontrolovaných slovníků (controlled vocabulary) k popisu dat. 
	- [ ]  Vysvětlit rozdíl mezi typy slovníků (controlled list, taxonomy, thesaurus, classification scheme, ontology). 
	- [ ]  Popsat základní strukturu SKOS (Simple Knowledge Organization System). - [ ]  Definovat ontologii pomocí SKOS a následně jí použít k popisu dat. 
- [ ]  Základy šifrování a komprese dat 
	- [ ]  Vysvětlit význam Shannonovy věty o kódování zdrojů (Shannon’s source coding theorem) v kontextu kom- prese dat. 
	- [ ]  Na příkladech vysvětlit základní myšlenky algoritmů pro kompresi: Run-Length Encoding, Huffman Coding, Lempel-Ziv-Welch a Arithmetic coding. 
	- [ ]  Vysvětlit pojem digitálního certifikátu a jeho použití. 
	- [ ]  Vysvětlit potřebu existence PKI (public key infrastructure) ve vztahu k digitálnímu certifikátu. 
	- [ ]  Vysvětlit použití symetrického a asymetrického šifrování v kontextu digitálního certifikátu. 
- [ ]  Základy indexování 
	- [ ]  Na příkladech vysvětlit práci se základními typy organizace souborů (hromada, sekvenční soubor, indexo- vaný sekvenční soubor) a jejich (ne)výhody. 
	- [ ]  Vysvětlit a na příkladech demonstrovat pojmy přímé/nepřímé indexování a primární/sekundární index. 
	- [ ]  Vysvětlit principy hashování na vnější paměti, vybraný konkrétní přístup (např. Cormack, Larson & Kalja, Fagin, …) demonstrovat na příkladu. 
	- [ ]  Vysvětlit, k čemu slouží a jaké jsou výhody hierarchických indexů. Na příkladu demonstrovat datovou strukturu B-strom a související operace. Popsat další modifikace (B+ strom, B* strom). 
	- [ ]  Indexování v prostorových databázích 
	- [ ]  Nakreslit a vysvětlit výhody křivek vyplňujících prostor (Z-křivka, Hilbertova křivka). 
	- [ ]  Pro zadaný příklad nakreslit Quad-tree, vysvětlit princip, výhody a nevýhody. 
	- [ ]  Pro zadaný příklad nakreslit k-d-tree, vysvětlit princip, výhody a nevýhody. 
	- [ ]  Pro zadaný příklad nakreslit R-strom, vysvětlit princip, výhody a nevýhody. Vysvětlit rozdíly oproti R+ stromu, popř. R* stromu. 
	- [ ]  Vysvětlit pojem prostorové spojení - princip, problémy. Na příkladu demonstrovat konkrétní přístup po- drobněji.