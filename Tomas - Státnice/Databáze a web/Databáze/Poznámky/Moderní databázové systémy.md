---
dg-publish: true
tags:
  - databaze
  - databaze_a_web
  - tomas
---
## Základní třídy moderních databázových systémů
### Databázové modely
-   První generace – navigační: Hierarchický model (stromy), Síťový
    model (grafy)
-   Druhá generace – relační
-   Třetí generace – post-relační
    -   Rozšíření relačního modelu – objektově-relační – objekty, třídy,
        dědičnost
    -   Nové modely navazující na populární technologie – objekty, XML,
        NoSql (key/value, column, document, graph, …) – Big Data
    -   Multi-model systém, NewSQL – zpátky k relacím
### Relační model
-   Ukládání objektů a jejich vzájemných asociací do <mark style="background: #FFF3A3A6;">tabulek</mark> (relací)
-   Řádek v tabulce (člen relace) = objekt/asociace, sloupec (atribut) =
    atribut objektu/asociace
-   Schéma tabulky (relace) = název schématu + seznam atributů a jejich
    typů
-   Základní omezení integrity – unikátní identifikace řádku, simple
    type atributy, hodnoty NULL (žádné "díry")
-   Optimální pro některé aplikace, ale: nepodporuje <mark style="background: #FFF3A3A6;">složité datové typy</mark>
    -   Normalizace dat do tabulkové podoby ovlivňuje výkon při
        vyhledávání rozsáhlých, <mark style="background: #FFF3A3A6;">složitých a hierarchicky strukturovaných  dat</mark>
    -   objevily se objektově orientované programovací jazyky – koncept uživatelsky definovaných tříd
### Hierarchický model
-   Data jsou uspořádána do záznamů, které se rekurzivně skládají z
    jiných záznamů
-   IBM’s IMS (Information Management System) - Jeden z prvních komerčně
    dostupných DBMS.
-   Les stromů – vztahy typu 1:n
    -   První nezávislý = redundance – záznam nemůže být uložen ve 2
        různých stromech, aniž by se duplikoval
-   Zpracování dat: hierarchické, počínaje kořenem, hloubkové,
    procházení zleva doprava
    -   První ukládání na pásky – lineární přístup
    -   Později (příchod disků) přímý přístup díky technikám hashování a
        B-stromů
### Síťový model
-   Datové záznamy propojené binárními vztahy, blízko ER modelu
    -   Zpracování dat: navigační primitiva, podle kterých se k záznamům
        přistupuje, aktualizují se jeden po druhém; Relační
        dotazovací jazyky: množinová orientace
-   Uzly = typy záznamů – reprezentují entity reálného světa, mají
    atomická nebo složená pole, záznam = datová jednotka (má
    identifikátor)
-   Hrany = typy množin – typ vztahu 1:n, seznam záznamů = hlavní
    záznam + členové množiny

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
   - **Pseudokódu:**
```python
# Map Function
def map(key, value):
    # Perform some operation on the value to generate intermediate key-value pairs
    for element in process(value):
        emit(intermediate_key, intermediate_value)

# The framework automatically handles shuffling and sorting of intermediate key-value pairs

# Reduce Function
def reduce(intermediate_key, values):
    # Aggregate or process the list of values for each intermediate key
    result = aggregate(values)
    emit(intermediate_key, result)
```
- Příklad (Četnost slov)
```python
def map(key, value):
	for each word in value:
		emit(word, 1)

def reduce(key, values):
	sum = 0
	for each value in values:
		sum += value
	emit(key, sum)
```
   - **Výhody:** Škálovatelnost, odolnost vůči chybám díky distribuci dat a úkolů.
   - **Nevýhody:** Omezená flexibilita, komplexnost implementace pro některé typy analýz.

### NoSQL databáze

NoSQL databáze představují alternativu k tradičním relačním databázím, které se ukázaly být omezené při zpracování velkých objemů dat a různorodých datových struktur. NoSQL databáze jsou navrženy tak, aby byly škálovatelné a flexibilní, což je činí ideálními pro moderní aplikace, které pracují s obrovskými množstvími dat, často ve velmi rozdílných formátech.

### Typy NoSQL databází a jejich vlastnosti

1. **Dokumentové databáze**
   - **Vlastnosti:** Ukládají data ve formě dokumentů, které jsou obvykle ve formátu JSON, BSON nebo XML. Dokumenty mohou obsahovat strukturovaná data (složitější hierarchie) a nevyžadují jednotnou strukturu mezi dokumenty.
   - **Výhody:** Velká flexibilita, snadná správa struktury dat, dobré pro aplikace s měnícími se požadavky na datový model.
   - **Nevýhody:** Může být obtížné spravovat vztahy mezi dokumenty, pokud jsou složité.
   - **Příklad:** MongoDB, CouchDB.

2. **Klíč-hodnota databáze**
   - **Vlastnosti:** Data jsou organizována jako páry klíč-hodnota, kde klíč je unikátní identifikátor a hodnota může být jakýkoliv datový typ (string, objekt, binární data atd.).
   - **Výhody:** Jednoduchý model, velmi rychlé dotazování díky přímému přístupu ke klíči, vhodné pro cache systémy nebo session storage.
   - **Nevýhody:** Omezené možnosti dotazování, neschopnost zpracovávat složitější dotazy bez nadstavbových systémů.
   - **Příklad:** Redis, DynamoDB.

3. **Sloupcové databáze**
   - **Vlastnosti:** Ukládají data po sloupcích místo po řádcích. Tento přístup je výhodný pro analytické dotazy, které často potřebují přístup k velkému množství dat z jednoho sloupce.
   - **Výhody:** Vysoký výkon při čtení a analýze dat, efektivní uložení komprimovaných dat.
   - **Nevýhody:** Méně efektivní při zápisu dat nebo při práci s řádkově orientovanými operacemi.
   - **Příklad:** Cassandra, HBase.

4. **Grafové databáze**
   - **Vlastnosti:** Specializují se na ukládání a dotazování na data, která jsou propojena složitými vztahy, jako jsou například grafy (uzly a hrany).
   - **Výhody:** Vynikající pro modelování a dotazování na komplexní vztahy mezi daty, například v sociálních sítích, doporučovacích systémech nebo při analýze sítí.
   - **Nevýhody:** Může být obtížné pochopit a spravovat, omezený výkon při zpracování velkých objemů dat, které nejsou silně propojeny.
   - **Příklad:** Neo4j, Amazon Neptune.

### Ukázka rozdílů mezi jednotlivými modely na jednoduchém příkladu

Představme si situaci, kdy máme e-shop, který uchovává informace o produktech, zákaznících a jejich objednávkách.

1. **Dokumentová databáze:**
   - **Struktura:** Každý produkt je uložen jako dokument (např. JSON), který obsahuje název, cenu, popis a seznam recenzí. Recenze jsou vloženy přímo do dokumentu produktu jako pole.
   - **Výhoda:** Všechna data týkající se jednoho produktu jsou uložena pohromadě, což usnadňuje jejich načítání a práci s nimi.
   - **Nevýhoda:** Pokud by některé produkty měly obrovské množství recenzí, dokument by se mohl stát velmi velkým.

```json
{
 "product_id": "123",
 "name": "Laptop",
 "price": 1500,
 "reviews": [
   {"user": "Tomas", "rating": 5, "comment": "Great product!"},
   {"user": "Eva", "rating": 4, "comment": "Good, but could be better."}
 ]
}
```

2. **Klíč-hodnota databáze:**
   - **Struktura:** Každý produkt je uložen jako záznam s unikátním klíčem, například `product:123`, a hodnota může být jednoduchý JSON nebo serialized string.
   - **Výhoda:** Velmi rychlé načítání dat, vhodné pro jednoduché aplikace, kde je hlavním účelem rychlý přístup ke konkrétním produktům.
   - **Nevýhoda:** Omezené možnosti pokročilých dotazů.
   
```json
"product:123" : "{\"name\": \"Laptop\", \"price\": 1500, \"reviews\": [{\"user\": \"Tomas\", \"rating\": 5}]}"
```

3. **Sloupcová databáze:**
   - **Struktura:** Každý produkt může být reprezentován několika sloupci, například `product_id`, `name`, `price`, `reviews`, kde každý sloupec je uložen samostatně.
   - **Výhoda:** Efektivní dotazování na konkrétní vlastnosti (například cena všech produktů), zejména v případě velkého množství dat.
   - **Nevýhoda:** Méně intuitivní při práci s komplexními datovými strukturami, jako jsou recenze.

```yaml
Row key: product_id:123
Columns:
 name: "Laptop"
 price: 1500
 reviews: "[{\"user\": \"Tomas\", \"rating\": 5}]"
```

4. **Grafová databáze:**
   - **Struktura:** Produkty, zákazníci a objednávky by byly reprezentovány jako uzly, zatímco vztahy mezi nimi (např. "koupil", "hodnotil") by byly reprezentovány jako hrany.
   - **Výhoda:** Skvělé pro dotazování na komplexní vztahy, jako například "zákazníci, kteří koupili tento produkt, také hodnotili následující produkty".
   - **Nevýhoda:** Nevhodné pro jednoduché dotazování nebo pokud je většina dat bez silných vztahů.

```neo4j
   (Tomas)-[bought]->(Laptop)
   (Tomas)-[reviewed]->(Laptop)
   (Eva)-[bought]->(Phone)
```

### Grafové databáze

#### Datový model

Grafová databáze využívá datový model založený na grafech, kde data jsou reprezentována jako **uzly** (nodes) a **hrany** (edges). Tento model je ideální pro případy, kdy je důležité uchovávat a analyzovat složité vztahy mezi entitami. Grafy jsou výkonné pro dotazování na propojení a cesty mezi uzly, což je výhodné v mnoha reálných scénářích, jako jsou sociální sítě, doporučovací systémy, analýza sítí a další.

- **Uzly (Nodes):** Uzly představují základní entity nebo objekty v databázi. Například v sociální síti by uzly představovaly uživatele.
- **Hrany (Edges):** Hrany reprezentují vztahy mezi uzly. Tyto vztahy mohou být například "přátelství", "sleduje", "pracuje v" apod.
- **Vlastnosti (Properties):** Oba uzly i hrany mohou mít vlastnosti, což jsou klíč-hodnota páry, které popisují charakteristiky entit a vztahů. Například uzel reprezentující uživatele může mít vlastnosti jako `jméno`, `věk` a `místo`, zatímco hrana může mít vlastnost `datum přátelství`.

#### Příklad datového modelu

Uvažujme jednoduchý příklad sociální sítě:

- **Uzly:**
  - Uživatel 1: `{"id": 1, "name": "Tomáš", "age": 30}`
  - Uživatel 2: `{"id": 2, "name": "Eva", "age": 25}`
  - Uživatel 3: `{"id": 3, "name": "Petr", "age": 28}`

- **Hrany:**
  - Přátelství mezi Tomášem a Evou: `{"from": 1, "to": 2, "relationship": "friends", "since": "2022-01-15"}`
  - Přátelství mezi Tomášem a Petrem: `{"from": 1, "to": 3, "relationship": "friends", "since": "2021-10-20"}`
  - Eva sleduje Petra: `{"from": 2, "to": 3, "relationship": "follows", "since": "2023-04-01"}`

Grafový model tohoto příkladu by mohl být znázorněn takto:

```plaintext
(Tomáš)-[:FRIENDS {since: "2022-01-15"}]->(Eva)
(Tomáš)-[:FRIENDS {since: "2021-10-20"}]->(Petr)
(Eva)-[:FOLLOWS {since: "2023-04-01"}]->(Petr)
```

#### Třídy grafových dotazů

Grafové databáze podporují různé typy dotazů, které jsou zaměřeny na zkoumání vztahů mezi uzly. Mezi hlavní třídy grafových dotazů patří:

1. **Dotaz na sousední uzly (Neighborhood Query):**
   - **Popis:** Tento dotaz vrací všechny uzly, které jsou přímo spojeny s daným uzlem jednou hranou.
   - **Příklad:** "Kdo jsou přátelé Tomáše?"
   - **Dotaz:** 
```plaintext
MATCH (Tomáš)-[:FRIENDS]->(friend)
RETURN friend
```

2. **Dotaz na cestu (Path Query):**
   - **Popis:** Tento dotaz hledá cestu nebo všechny cesty mezi dvěma uzly. Může být užitečný při zjišťování, zda existuje spojení mezi dvěma entitami.
   - **Příklad:** "Existuje cesta mezi Tomášem a Petrem přes jejich přátele?"
   - **Dotaz:** 
```plaintext
MATCH (Tomáš)-[:FRIENDS*]-(Petr)
RETURN path
```

3. **Dotaz na nejkratší cestu (Shortest Path Query):**
   - **Popis:** Tento dotaz hledá nejkratší cestu mezi dvěma uzly. Je užitečný pro optimalizaci různých procesů, jako je doporučování.
   - **Příklad:** "Jaká je nejkratší cesta přátelství mezi Tomášem a Petrem?"
   - **Dotaz:** 
```plaintext
MATCH p = shortestPath((Tomáš)-[:FRIENDS*]-(Petr))
RETURN p
```

4. **Dotaz na vzory (Pattern Matching):**
   - **Popis:** Tento dotaz umožňuje hledat složitější struktury a vzory v grafech, například komunitní struktury nebo cykly.
   - **Příklad:** "Najdi všechny trojúhelníky přátel (komunity tří lidí, kde každý je přítel s každým)."
   - **Dotaz:** 
```plaintext
MATCH (a)-[:FRIENDS]->(b)-[:FRIENDS]->(c)-[:FRIENDS]->(a)
RETURN a, b, c
```

5. **Centralita (Centrality Query):**
   - **Popis:** Tento dotaz měří, jak "centrální" je určitý uzel ve vztahu k ostatním uzlům. Centralita se často používá k nalezení nejvlivnějších nebo nejvýznamnějších uzlů v grafu.
   - **Příklad:** "Kdo je nejvlivnějším uživatelem na základě počtu přátel?"
   - **Dotaz:** 
```plaintext
MATCH (user)-[:FRIENDS]->(friends)
RETURN user, COUNT(friends) AS influence
ORDER BY influence DESC
```

### Multi-model databáze a Polystore

1. **Rozdíly, výhody a nevýhody:**
   - **Multi-model databáze:** Tyto systémy podporují více datových modelů (např. dokumentový, grafový, relační) v rámci jednoho databázového systému. Umožňují ukládání a dotazování dat různými způsoby podle specifických potřeb aplikace.
   - **Polystore:** Integruje více různých databázových systémů a umožňuje provádění dotazů napříč těmito systémy, aniž by bylo nutné data migrovat do jednoho systému.

2. **Příklad multi-model dotazu:**
   - **Dotaz:** Umožňuje vyhledávat data z různých modelů v jednom dotazu, například kombinace relačních dat a dokumentových dat v jednom dotazu v rámci multi-model databáze.
   - **Možné problémy:** Složitost a snížení výkonu kvůli nutnosti kombinovat různé dotazovací mechanizmy, složitější optimalizace a ladění.