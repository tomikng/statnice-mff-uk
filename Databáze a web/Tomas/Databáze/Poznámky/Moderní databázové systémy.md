### Základní třídy moderních databázových systémů

1. **Relational Databases (RDBMS):**
   - **Popis:** Relační databázové systémy jsou založeny na relačním modelu, kde data jsou ukládána v tabulkách s přísně definovanými strukturami (schema-on-write). Každá tabulka obsahuje záznamy (řádky) a atributy (sloupce). Data jsou propojena pomocí primárních a cizích klíčů.
   - **Vlastnosti:** Poskytují silnou konzistenci a ACID vlastnosti, což zaručuje, že data jsou vždy v konzistentním stavu. Typické operace zahrnují CRUD (Create, Read, Update, Delete).
   - **Příklady:** MySQL, PostgreSQL, Oracle Database.

2. **NoSQL Databases:**
   - **Popis:** NoSQL databáze se odlišují od tradičních relačních databází svou schopností zpracovávat nestrukturovaná a semi-strukturovaná data. Nevyžadují přísnou strukturu a jsou navrženy pro horizontální škálování.
   - **Typy NoSQL databází:**
     - **Dokumentové databáze:** Ukládají data jako dokumenty (např. JSON, BSON). Každý dokument může mít jinou strukturu.
       - **Příklad:** MongoDB, CouchDB.
     - **Klíč-hodnota databáze:** Data jsou ukládána jako páry klíč-hodnota, což umožňuje velmi rychlé vyhledávání.
       - **Příklad:** Redis, Riak.
     - **Sloupcové databáze:** Ukládají data po sloupcích namísto po řádcích, což je výhodné pro analytické dotazy na velké datové sady.
       - **Příklad:** Apache Cassandra, HBase.
     - **Grafové databáze:** Specializované na ukládání a práci s daty, která jsou vzájemně propojená (uzly a hrany).
       - **Příklad:** Neo4j, Amazon Neptune.
   - **Vlastnosti:** Nabízejí vysokou dostupnost, horizontální škálování a jsou často optimalizovány pro rychlý přístup k velkým objemům dat.

3. **NewSQL:**
   - **Popis:** NewSQL databáze kombinují výhody relačních databází (RDBMS) s výhodami NoSQL systémů, přičemž zachovávají podporu pro SQL jako dotazovací jazyk a ACID vlastnosti.
   - **Vlastnosti:** Nabízejí vysokou škálovatelnost a výkon, podobně jako NoSQL systémy, ale s konzistencí a strukturou známou z RDBMS.
   - **Příklady:** Google Spanner, CockroachDB.

4. **In-Memory Databases:**
   - **Popis:** Tyto databáze ukládají data přímo v paměti (RAM), což umožňuje extrémně rychlý přístup k datům. Jsou využívány pro aplikace vyžadující velmi nízkou latenci a vysoký výkon.
   - **Vlastnosti:** Velmi rychlý přístup k datům, ale vyšší náklady na provoz kvůli potřebě velkého množství paměti.
   - **Příklady:** Redis (může fungovat jako klíč-hodnota databáze v paměti), SAP HANA.

### Big Data

1. **Popis a vlastnosti:**
   - **Big Data** se týká masivních datových souborů, které jsou příliš velké a komplexní, než aby je bylo možné zpracovat tradičními databázovými systémy. Big Data se vyznačují následujícími charakteristikami:
     - **Objem (Volume):** Obrovské množství dat produkovaných každý den, například z IoT zařízení, sociálních sítí, nebo finančních transakcí.
     - **Rychlost (Velocity):** Rychlost, jakou jsou data generována a potřebná k analýze. Příkladem může být analýza dat v reálném čase z Twitteru nebo datových toků z finančních transakcí.
     - **Různorodost (Variety):** Různé formáty dat, jako jsou strukturovaná, nestrukturovaná a semi-strukturovaná data, například textové dokumenty, videa, zvukové soubory a senzory.
     - **Proměnlivost (Variability):** Změna ve struktuře a kvalitě dat v průběhu času. Příkladem je sezónní změna v datech z e-commerce nebo náhlé změny ve vzorcích chování uživatelů.

2. **Výzvy Big Data:**
   - **Ukládání:** Tradiční systémy často nedokáží efektivně ukládat a spravovat tak velké objemy dat.
   - **Zpracování:** Potřeba paralelního zpracování velkých objemů dat vyžaduje distribuované systémy, jako jsou Hadoop a Spark.
   - **Integrace:** Kombinace různorodých datových zdrojů do jednoho konzistentního formátu.
   - **Bezpečnost a soukromí:** Ochrana citlivých dat je klíčová, zvláště při práci s tak obrovskými a různorodými datovými sadami.

3. **Big Data Ekosystém:**
   - **Apache Hadoop:** Open-source rámec pro distribuované ukládání a zpracování velkých datových sad. Hadoop používá HDFS (Hadoop Distributed File System) pro ukládání dat a MapReduce pro paralelní zpracování.
   - **Apache Spark:** Rámec pro zpracování dat, který nabízí rozšířené možnosti nad Hadoopem, jako je in-memory zpracování, což umožňuje rychlejší analýzu dat.
   - **Data Lakes:** Úložiště pro velké množství nestrukturovaných a strukturovaných dat, která mohou být zpracována podle potřeby. Umožňuje ukládat data ve své původní podobě bez potřeby předběžného zpracování (schema-on-read).

### Princip MapReduce

1. **Princip a aplikace:**
   - **MapReduce** je programovací model a související implementace pro zpracování velkých datových sad paralelně na velkém počtu strojů (clusterů). Skládá se ze dvou hlavních fází:
     - **Map fáze:** Rozděluje úlohu na menší podúlohy a zpracovává každý záznam jednotlivě. Vstup je převeden na dvojice klíč-hodnota.
     - **Reduce fáze:** Shrnuje výsledky z *Map* fáze tak, že kombinuje všechny hodnoty přiřazené ke stejnému klíči.
   - **Příklad pseudokódu:**
     ```python
     map(key, value):
        for each word in value:
            emit(word, 1)
 
     reduce(key, values):
        sum = 0
        for each value in values:
            sum += value
        emit(key, sum)
     ```
   - **Výhody:** Škálovatelnost, odolnost vůči chybám díky distribuci dat a úkolů.
   - **Nevýhody:** Omezená flexibilita, komplexnost implementace pro některé typy analýz.

### NoSQL databáze

1. **Typy a vlastnosti:**
   - **Dokumentové databáze:** Ukládají data ve formě dokumentů (např. JSON, BSON). Každý dokument může obsahovat různé typy a množství dat.
   - **Klíč-hodnota databáze:** Data jsou organizována do párů klíč-hodnota, kde klíč je unikátní identifikátor a hodnota může být libovolná data.
   - **Sloupcové databáze:** Umožňují ukládání dat po sloupcích, což zlepšuje výkon při analytických dotazech na velkých datových sadách.
   - **Grafové databáze:** Zaměřené na modelování a dotazování se na složité vztahy mezi daty, například vztahy v sociálních sítích.

2. **Příklad rozdílů:**
   - **Relace vs. Dokument:** V relačních databázích jsou data uložena v tabulkách s pevně danou strukturou, zatímco v dokumentových databázích mohou mít dokumenty různou strukturu a obsahovat složitější hierarchie.

### Grafové databáze

1. **Datový model:**
   - **Popis:** Grafová databáze ukládá data jako uzly (

entity) a hrany (vztahy). Tento model je výkonný pro aplikace, kde jsou data silně propojena a kde je třeba provádět složité dotazy na vztahy mezi entitami.
   - **Příklad:** Sociální síť, kde uzly reprezentují uživatele a hrany představují přátelství mezi nimi.

### Multi-model databáze a Polystore

1. **Rozdíly, výhody a nevýhody:**
   - **Multi-model databáze:** Tyto systémy podporují více datových modelů (např. dokumentový, grafový, relační) v rámci jednoho databázového systému. Umožňují ukládání a dotazování dat různými způsoby podle specifických potřeb aplikace.
   - **Polystore:** Integruje více různých databázových systémů a umožňuje provádění dotazů napříč těmito systémy, aniž by bylo nutné data migrovat do jednoho systému.

2. **Příklad multi-model dotazu:**
   - **Dotaz:** Umožňuje vyhledávat data z různých modelů v jednom dotazu, například kombinace relačních dat a dokumentových dat v jednom dotazu v rámci multi-model databáze.
   - **Možné problémy:** Složitost a snížení výkonu kvůli nutnosti kombinovat různé dotazovací mechanizmy, složitější optimalizace a ladění.