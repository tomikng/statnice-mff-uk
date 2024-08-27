---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka
### Sémantické popisování dat pomocí RDF Schema, Dublin Core a SKOS

#### RDF Schema (RDFS)
RDF Schema (RDFS) je rozšíření základního modelu RDF (Resource Description Framework) používaného pro reprezentaci sémantických dat na webu. RDFS umožňuje definovat ontologie, což jsou strukturované popisy pojmů a vztahů mezi nimi. RDF představuje data v podobě trojic (subjekt-predikát-objekt), kde subjekt a objekt jsou uzly a predikát je hrana, která je spojuje.

RDFS přidává schopnosti definovat třídy (`rdfs:Class`), vlastnosti (`rdfs:Property`), a hierarchické vztahy mezi nimi, jako například podtřídy (`rdfs:subClassOf`) a podvlastnosti (`rdfs:subPropertyOf`). Tímto způsobem můžete vytvořit sémantickou síť pojmů, které jsou logicky propojeny.

#### Dublin Core
Dublin Core je standardní slovník metadat, který poskytuje základní sadu popisných prvků pro širokou škálu zdrojů (dokumenty, obrázky, videa atd.). Obsahuje 15 základních prvků, jako je název (`dc:title`), autor (`dc:creator`), datum (`dc:date`) nebo popis (`dc:description`). Tento slovník lze použít v kombinaci s RDF k anotaci zdrojů na webu a jejich propojení s dalšími sémantickými daty. Dublin Core se často používá pro popis digitálních knihoven, archívů a dalších informačních zdrojů.

#### SKOS (Simple Knowledge Organization System)
SKOS je další slovník používaný pro sémantické popisování dat, zaměřený na organizaci znalostí. SKOS umožňuje popisování pojmových schémat (například tezaurů, klasifikačních schémat nebo taxonomií) v rámci RDF. SKOS poskytuje prostředky pro definování pojmů (`skos:Concept`), jejich hierarchických vztahů (`skos:broader`, `skos:narrower`), a asociativních vztahů (`skos:related`). Rovněž umožňuje přidání popisných štítků a anotací (`skos:prefLabel`, `skos:altLabel`, `skos:note`).

### Datový model Wikidata

Wikidata je volně dostupná znalostní báze, která slouží jako společný zdroj strukturovaných dat pro projekty Wikimedia, jako je Wikipedia, a pro další aplikace a služby. Datový model Wikidata je založen na RDF a umožňuje strukturované popisování entit a vztahů mezi nimi.

#### Základní komponenty datového modelu Wikidata:
- **Entity**: Všechny objekty v Wikidata jsou reprezentovány entitami, které mají unikátní identifikátory (např. Q42 pro Douglase Adamse). Entity mohou být tří typů:
  - **Položky (Items)**: Reprezentují konkrétní objekty, osoby, místa atd.
  - **Vlastnosti (Properties)**: Popisují atributy položek nebo vztahy mezi nimi (např. P31 pro "instance of").
  - **Lexémy (Lexemes)**: Slouží k reprezentaci slov a jazykových dat.
- **Prohlášení (Statements)**: Položky mají přidružené vlastnosti a hodnoty, které jsou reprezentovány jako prohlášení. Každé prohlášení může mít také kvalifikátory (doplňující informace) a reference (zdroje potvrzující pravdivost prohlášení).

#### Dotazování ve Wikidata
K dotazování ve Wikidata se používá dotazovací jazyk SPARQL (SPARQL Protocol and RDF Query Language). SPARQL umožňuje vyhledávat a získávat data z RDF grafu na základě konkrétních kritérií.

Příklad jednoduchého SPARQL dotazu:
```sparql
SELECT ?item ?itemLabel WHERE {
  ?item wdt:P31 wd:Q146 .  # Vyhledá položky, které jsou instance "kočky"
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
LIMIT 10
```
Tento dotaz vrátí prvních 10 položek, které jsou instancemi kočky (Q146), a jejich popisky v preferovaném jazyce.

Wikidata také nabízí SPARQL editor [Wikidata Query Service](https://query.wikidata.org/), který umožňuje uživatelům vytvářet a spouštět SPARQL dotazy a vizualizovat výsledky různými způsoby (např. grafy, mapy).

### Shrnutí
Sémantické popisování dat pomocí RDF Schema, Dublin Core a SKOS umožňuje vytvářet strukturované a propojené informace, které lze snadno integrovat a vyhledávat na webu. Wikidata používá tyto koncepty k vytváření obrovského, propojeného znalostního grafu, který je volně přístupný a může být dotazován pomocí SPARQL k získání specifických informací o světě kolem nás.