---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka
### RDF Schema (RDFS)

[[Modely a formáty pro grafová data - RDF a Labeled Property Graph|RDF Schema (RDFS)]] poskytuje mechanismy pro definování tříd a vlastností, které umožňují sémantickou klasifikaci a organizaci dat v rámci RDF. Pomocí RDFS lze vytvářet hierarchie tříd a vlastností, což umožňuje modelovat vztahy mezi různými entitami a koncepty v doméně.

Základní prvky RDFS zahrnují:
- **rdfs:Class**: Definuje třídu, což je kolekce objektů, které sdílejí společné vlastnosti. Například `foaf:Person` může být třídou, která zahrnuje všechny osoby.
- **rdfs:subClassOf**: Umožňuje definovat hierarchii tříd. Například `foaf:Student` může být podtřídou `foaf:Person`, což znamená, že každý student je osoba.
- **rdfs:Property**: Definuje vlastnost, což je vztah mezi dvěma zdroji (subjekt-předmět). Například `foaf:name` je vlastnost, která přiřazuje jméno osobě.
- **rdfs:subPropertyOf**: Umožňuje hierarchii vlastností, kde například `foaf:givenName` může být podvlastností `foaf:name`.

RDFS tedy umožňuje nejen strukturovat data, ale také jim přiřadit sémantiku, což je klíčové pro interpretaci dat počítači a jejich využití v propojených datech.

### Dublin Core

Dublin Core je sémantický slovník, který poskytuje sadu základních metadatových prvků pro popis různých zdrojů, jako jsou dokumenty, obrazy, videa nebo webové stránky. Mezi základní prvky Dublin Core patří:
- **dc:title**: Název zdroje.
- **dc:creator**: Autor nebo tvůrce zdroje.
- **dc:subject**: Téma nebo klíčová slova, která popisují obsah zdroje.
- **dc:date**: Datum vytvoření nebo publikace zdroje.
- **dc:type**: Typ zdroje (například text, obraz, zvuk).

Dublin Core je široce využíván pro jeho jednoduchost a flexibilitu při popisu různých typů zdrojů.

### SKOS (Simple Knowledge Organization System)

[[SKOS]] je další sémantický slovník, který je určený pro reprezentaci znalostních organizací, jako jsou tezaury, klasifikace nebo taxonomie. SKOS umožňuje reprezentovat koncepty a jejich vztahy, což je užitečné při organizaci znalostí v různých doménách.

Základní prvky SKOS zahrnují:
- **skos:Concept**: Definuje základní jednotku v SKOS, což je koncept, například „Pes“ nebo „Matematika“.
- **skos:broader** a **skos:narrower**: Umožňují definovat hierarchické vztahy mezi koncepty, kde jeden koncept je obecnější (broader) nebo specifičtější (narrower) než druhý.
- **skos:related**: Umožňuje definovat asociativní vztahy mezi koncepty, které nejsou hierarchické, ale jsou jiným způsobem propojené.

### Datový model Wikidata

Wikidata je otevřená znalostní báze, která používá strukturovaná data pro popis různých entit. Datový model Wikidata je postaven na bázi RDF a zahrnuje několik základních komponent:
- **Položky (Items)**: Každá položka představuje entitu (např. osoba, místo, událost) a je identifikována jedinečným identifikátorem, například Q42 pro Douglase Adamse.
- **Vlastnosti (Properties)**: Vlastnosti popisují vztahy mezi položkami, například `P31` (instance of) označuje typ entity, nebo `P569` (date of birth) označuje datum narození.
- **Prohlášení (Statements)**: Prohlášení jsou tvořena položkou, vlastností a hodnotou (další položkou, datem, číslem atd.). Například "Q42 (Douglas Adams) P569 (datum narození) 1952-03-11".
- **Kvalifikátory (Qualifiers)** a **Referencemi (References)**: Kvalifikátory umožňují přidat dodatečné informace k prohlášením, jako například časové období, a reference slouží k citování zdrojů, které potvrzují dané prohlášení.

### Dotazování ve Wikidata

Pro dotazování ve Wikidata se používá jazyk SPARQL, který je standardem pro dotazování nad RDF daty. SPARQL umožňuje psát dotazy, které vyhledávají konkrétní informace v databázi Wikidata.

Například, chcete-li získat seznam spisovatelů a jejich data narození, můžete použít následující SPARQL dotaz:

```sparql
SELECT ?writer ?writerLabel ?birthDate WHERE {
  ?writer wdt:P106 wd:Q36180;  # P106 (occupation) Q36180 (writer)
          wdt:P569 ?birthDate.  # P569 (date of birth)
  SERVICE wikibase:label { bd:serviceParam wikibase:language "[AUTO_LANGUAGE],en". }
}
ORDER BY ?birthDate
```

Tento dotaz vyhledává všechny položky, které mají povolání "spisovatel" a vrací jejich jména a data narození.

Díky těmto technologiím a nástrojům je možné efektivně popisovat, strukturovat a dotazovat se na sémantická data, což podporuje lepší sdílení a propojení informací na internetu.