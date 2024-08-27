---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě poznamek

SKOS (Simple Knowledge Organization System) je standard W3C pro reprezentaci a sdílení řízených slovníků, taxonomií, tezaurů a dalších typů znalostních organizací ve formátu, který je strojově čitelný a snadno použitelný na webu. SKOS umožňuje snadné vyjádření a výměnu základních struktur a obsahu řízených slovníků a taxonomií.

### Základní struktura SKOS

1. **SKOS Concept (`skos:Concept`)**
   - **Popis**: Hlavní stavební jednotka SKOS, která reprezentuje jednotlivé pojmy (koncepty) ve slovníku, taxonomii nebo tezauru. Každý `skos:Concept` je unikátní entita, která může být identifikována a popsána.
   - **Vlastnosti**:
     - **`skos:prefLabel`**: Preferovaný název pojmu (preferovaný termín).
     - **`skos:altLabel`**: Alternativní názvy nebo synonyma pojmu.
     - **`skos:hiddenLabel`**: Skrytý název, který není běžně zobrazen, ale může být použit pro vyhledávání.

2. **Hierarchické vztahy**
   - **`skos:broader`**: Vztah, který spojuje koncept s obecnějším konceptem. Tento vztah vytváří hierarchii, kde jeden koncept je podřízen jinému.
   - **`skos:narrower`**: Vztah, který spojuje koncept se specifičtějším konceptem. Tento vztah je opakem `skos:broader`.
   - **`skos:related`**: Vztah, který spojuje dva koncepty, které jsou sice odlišné, ale mají mezi sebou významovou souvislost (nejde však o hierarchický vztah).

3. **Popis konceptů**
   - **`skos:definition`**: Oficiální definice konceptu, která poskytuje podrobnější vysvětlení jeho významu.
   - **`skos:scopeNote`**: Poznámka k rozsahu použití konceptu, která může vysvětlit, v jakém kontextu by měl být koncept používán.
   - **`skos:example`**: Příklad použití konceptu, který pomáhá uživatelům lépe porozumět jeho aplikaci.

4. **Organizace konceptů**
   - **`skos:ConceptScheme`**: Kolekce `skos:Concept` objektů, které jsou společně organizovány a které sdílejí společný rámec nebo téma.
   - **`skos:hasTopConcept`**: Vztah, který označuje nejvyšší koncept (kořen) v daném `skos:ConceptScheme`.
   - **`skos:inScheme`**: Označuje, že koncept patří do určitého `skos:ConceptScheme`.

5. **Mapování mezi různými schématy**
   - **`skos:exactMatch`**: Označuje, že koncept v jednom schématu je přesně stejný jako koncept v jiném schématu.
   - **`skos:closeMatch`**: Označuje, že koncept v jednom schématu je velmi podobný (ale ne nutně totožný) konceptu v jiném schématu.
   - **`skos:broadMatch`**: Označuje, že koncept v jednom schématu je obecnější než koncept v jiném schématu.
   - **`skos:narrowMatch`**: Označuje, že koncept v jednom schématu je specifičtější než koncept v jiném schématu.

### Příklad použití SKOS

```turtle
@prefix skos: <http://www.w3.org/2004/02/skos/core#> .

<http://example.org/concept/c1> a skos:Concept ;
    skos:prefLabel "Apple"@en ;
    skos:altLabel "Malus domestica"@en ;
    skos:broader <http://example.org/concept/c2> ;
    skos:definition "A type of fruit from the species Malus domestica."@en ;
    skos:scopeNote "Commonly eaten raw or used in cooking."@en .

<http://example.org/concept/c2> a skos:Concept ;
    skos:prefLabel "Fruit"@en ;
    skos:narrower <http://example.org/concept/c1> ;
    skos:definition "The mature ovary of a flowering plant, typically containing seeds."@en .

<http://example.org/scheme> a skos:ConceptScheme ;
    skos:hasTopConcept <http://example.org/concept/c2> .
```

### Shrnutí
SKOS poskytuje jednoduchý, ale efektivní rámec pro reprezentaci a sdílení znalostních struktur, jako jsou taxonomie a tezaury. Základní jednotkou v SKOS je `skos:Concept`, který může být popsán, organizován do hierarchií a propojen s jinými koncepty v rámci nebo napříč schématy. SKOS umožňuje nejen tvorbu, ale také propojení různých znalostních organizací, což podporuje interoperabilitu a opakované využití znalostí na webu.