---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě. Na zaklade poznamek z prednasek 

**Data Provenance** označuje sledovatelnost a historii dat od jejich vzniku až po současnost. Tento koncept zahrnuje informace o **původu dat, jejich transformacích, zpracování a uchování.** Data Provenance je důležité pro zajištění důvěryhodnosti, kvality a reprodukovatelnosti dat, což je klíčové pro rozhodovací procesy v podnikání a výzkumu.

### **Příklad Data Provenance v reálném scénáři**

Představme si, že pracujete v e-commerce společnosti, která sleduje nákupní chování zákazníků. Data o nákupech, která shromažďujete, prochází několika fázemi zpracování, od získání přes různé transformace až po konečnou analýzu. Data Provenance vám umožňuje sledovat, odkud každá datová položka pochází, jak byla transformována a jak byla použita k vytvoření závěrečných analýz a reportů.

**Kroky zpracování:**
1. **Získání dat**: Data jsou získávána z několika zdrojů, například z webových stránek, mobilní aplikace a sociálních médií.
2. **Transformace dat**: Data jsou následně očištěna, agregována a normalizována, aby mohla být použita pro analýzu.
3. **Uložení dat**: Zpracovaná data jsou uložena do **datového skladu** pro budoucí použití.
4. **Analýza dat**: Data jsou analyzována pomocí statistických metod a výsledky jsou využity k optimalizaci marketingových kampaní.
5. **Publikace dat**: Na základě analýzy jsou vytvořeny reporty, které jsou sdíleny s vedením společnosti.

### **Využití PROV-O ontologie**

PROV-O je OWL ontologie, která je součástí standardů W3C a slouží k reprezentaci provenance informací na webu. PROV-O poskytuje formální model pro **popis entit, aktivit a agentů**, kteří se podíleli na vzniku dat.

**Klíčové prvky PROV-O:**
- **Entity (Entita)**: Jakýkoli objekt nebo data, která mají nějaký původ. V našem případě může entita reprezentovat například konkrétní sadu dat o nákupech.
- **Activity (Aktivita)**: Proces nebo událost, která transformuje entitu. Například proces čištění a normalizace dat je aktivita.
- **Agent (Agent)**: Osoba, organizace nebo software, které provádějí aktivity. Například datový analytik nebo automatický skript, který zpracovává data, jsou agenty.

**Příklad PROV-O modelu:**

```turtle
@prefix prov: <http://www.w3.org/ns/prov#> .
@prefix : <http://example.org/data#> .

:purchase_data a prov:Entity ;
    prov:wasGeneratedBy :data_collection_activity ;
    prov:wasAttributedTo :web_scraper .

:data_collection_activity a prov:Activity ;
    prov:used :web_source ;
    prov:wasAssociatedWith :data_analyst ;
    prov:generated :purchase_data .

:data_analyst a prov:Agent ;
    prov:type prov:Person ;
    prov:actedOnBehalfOf :ecommerce_company .

:web_scraper a prov:SoftwareAgent ;
    prov:actedOnBehalfOf :data_analyst .

:ecommerce_company a prov:Organization .
```

V tomto modelu:
- `:purchase_data` je entita reprezentující data o nákupech.
- `:data_collection_activity` je aktivita, která vytvořila data o nákupech.
- `:data_analyst` je agent, který prováděl aktivitu sběru dat.
## Domaci ukol

```python
import argparse
import sys

from rdflib import Graph, Literal, Namespace, URIRef, BNode
from rdflib.namespace import RDFS, FOAF, XSD, PROV, RDF

NSP = Namespace("https://example.com/provenance#")
NSR = Namespace("https://example.com/resources/")
dataset = URIRef(
    'https://www.czso.cz/documents/10180/165603907/13007221n01.xlsx/65344c95-18ed-4020-a866-868ba56e52e5?version=1.2')
creator = URIRef('https://github.com/tomikng')
org = URIRef('https://mff.cuni.cz')
czso = URIRef('https://www.czso.cz')


def add_entitities(result):
    data_cube = NSR.Population

    result.add((data_cube, RDF.type, PROV.Entity))
    result.add((data_cube, RDFS.label, Literal("Population data cube", lang="en")))
    result.add((data_cube, PROV.wasGeneratedBy, NSP.PopulationScript))
    result.add((data_cube, PROV.wasDerivedFrom, dataset))
    result.add((data_cube, PROV.wasAttributedTo, creator))

    result.add((dataset, RDF.type, PROV.Entity))
    result.add((dataset, PROV.wasAttributedTo, czso))
    result.add((dataset, RDFS.label, Literal("Population Dataset", lang='en')))


def add_agents(result):
    result.add((creator, RDF.type, PROV.Agent))
    result.add((creator, RDF.type, PROV.Person))
    result.add((creator, FOAF.name, Literal("Hai Hung Nguyen")))
    result.add((creator, PROV.actedOnBehalfOf, org))

    result.add((org, RDF.type, PROV.Agent))
    result.add((org, RDF.type, PROV.Organization))
    result.add((org, FOAF.name, Literal("MFF UK")))

    result.add((czso, RDF.type, PROV.Agent))
    result.add((czso, RDF.type, PROV.Organization))
    result.add((czso, FOAF.name, Literal("Czech statistical bureau", lang='en')))


def add_activities(result):
    activity = NSP.CreatePopulationDataCube
    result.add((activity, RDF.type, PROV.Activity))
    result.add((activity, PROV.used, NSP.PopulationDataset))
    result.add((activity, PROV.wasAssociatedWith, creator))
    result.add((activity, PROV.startedAtTime, Literal("2023-04-011T11:49:00", datatype=XSD.dateTime)))
    result.add((activity, PROV.endedAtTime, Literal("2023-04-011T11:55:00", datatype=XSD.dateTime)))

    bnode = BNode()
    result.add((activity, PROV.qualifiedUsage, bnode))
    result.add((bnode, RDF.type, PROV.Usage))
    result.add((bnode, PROV.entity, dataset))
    result.add((bnode, PROV.hadRole, NSR.role))


def add_roles(result):
    result.add((NSR.role, RDF.type, PROV.Role))


def crate_prov_graph() -> Graph:
    result = Graph(bind_namespaces="rdflib")

    add_entitities(result)
    add_agents(result)
    add_activities(result)
    add_roles(result)

    return result


def create_prov_document(output_path: str):
    data = crate_prov_graph()
    data.serialize(format="ttl", destination=output_path, encoding='UTF-8')


def get_args():
    parser = argparse.ArgumentParser(description='Create population data cube provenance')

    parser.add_argument('-o', '--out', dest='out', type=argparse.FileType('wb'),
                        help='Specify the file path to write the provenance.')

    args = parser.parse_args()
    return args


def main():
    args = get_args()
    create_prov_document(args.out)


if __name__ == '__main__':
    main()
```