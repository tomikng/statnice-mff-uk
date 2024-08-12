## Architektury databázových systémů

### Konceptuální, logická a fyzická úroveň
1. **Konceptuální úroveň:**
   - **Popis:** Konceptuální úroveň představuje abstraktní pohled na data v databázi. Je to model, který reflektuje, jaké informace má systém uchovávat, ale nezabývá se detaily, jak budou data uložena či zpracovávána.
   - **Příklad:** Entitně-relační diagram (ERD), kde jsou entity a jejich vztahy modelovány bez ohledu na konkrétní implementaci.

2. **Logická úroveň:**
   - **Popis:** Logická úroveň se zaměřuje na strukturu databáze z pohledu, jak budou data organizována v relačních tabulkách. V této fázi se rozhoduje o definici tabulek, atributů, datových typů a relací mezi tabulkami.
   - **Příklad:** Relační schéma s tabulkami „Zákazníci“, „Objednávky“ a jejich atributy jako ID, jméno, datum objednávky.

3. **Fyzická úroveň:**
   - **Popis:** Fyzická úroveň se týká skutečné implementace databáze na hardwaru. Zde se rozhoduje o způsobu uložení dat, indexování, optimalizaci dotazů a dalších technických detailech.
   - **Příklad:** Použití konkrétního typu indexů pro rychlejší vyhledávání v tabulce, optimalizace dotazů pro zvýšení výkonu.
### Normální formy (Normal Forms)

#### 1. Normální forma (1NF)
**Podmínky:**
- Každá tabulka musí mít jednoznačný primární klíč.
- Všechny sloupce tabulky musí obsahovat pouze atomické (nedělitelné) hodnoty.

**Příklad porušení 1NF:**
- Tabulka „Employee“ obsahuje sloupec „Subordinate“, který obsahuje složený typ (seznam zaměstnanců), což porušuje 1NF:
```
| Id  | Name           | Subordinate             | Boss          |
|-----|----------------|-------------------------|---------------|
| 1   | John Goodman   | [Person1, Person2, ...] | Person5       |
```

**Oprava:**
- Rozdělit složené typy do samostatných tabulek:
```
Tabulka: Employee
| Id  | Name           | Boss       |
|-----|----------------|------------|
| 1   | John Goodman   | Person5    |

Tabulka: Subordinates
| EmployeeId | SubordinateId |
|------------|---------------|
| 1          | Person1       |
| 1          | Person2       |
```

#### 2. Normální forma (2NF)
**Podmínky:**
- Splňuje požadavky 1NF.
- Všechny neklíčové atributy musí být plně závislé na celém primárním klíči, nikoli pouze na části primárního klíče.

**Příklad porušení 2NF:**
- Tabulka „Company“ obsahuje atribut „HQ“, který je závislý pouze na části složeného klíče „Company“, nikoliv na celém klíči „Company, DB server“:
```
| Company    | DB server | HQ       | Purchase date |
|------------|-----------|----------|---------------|
| John's firm| Oracle    | Paris    | 1995          |
| John's firm| MS SQL    | Paris    | 2001          |
| Paul's firm| IBM DB2   | London   | 2004          |
```

**Oprava:**
- Rozdělit tabulku do dvou, aby byl odstraněn částečný závislý atribut „HQ“:
```
Tabulka: CompanyDBServer
| Company    | DB server | Purchase date |
|------------|-----------|---------------|
| John's firm| Oracle    | 1995          |
| John's firm| MS SQL    | 2001          |

Tabulka: CompanyHQ
| Company    | HQ       |
|------------|----------|
| John's firm| Paris    |
| Paul's firm| London   |
```

#### 3. Normální forma (3NF)
**Podmínky:**
- Splňuje požadavky 2NF.
- Žádný neklíčový atribut nesmí záviset na jiném neklíčovém atributu (transitivní závislost).

**Příklad porušení 3NF:**
- Tabulka „Company“ obsahuje atribut „HQ“, který je transitivně závislý na klíči „Company“ přes atribut „ZIPcode“:
```
| Company    | ZIPcode | HQ      |
|------------|---------|---------|
| John's firm| CZ 11800| Prague  |
| Paul's firm| CZ 70833| Ostrava |
```

**Oprava:**
- Rozdělit tabulku tak, aby byly odstraněny transitivní závislosti:
```
Tabulka: CompanyZIP
| Company    | ZIPcode  |
|------------|----------|
| John's firm| CZ 11800 |
| Paul's firm| CZ 70833 |

Tabulka: ZIPcodeHQ
| ZIPcode   | HQ      |
|-----------|---------|
| CZ 11800  | Prague  |
| CZ 70833  | Ostrava |
```

#### Boyce-Coddova normální forma (BCNF)
**Podmínky:**
- Splňuje požadavky 3NF.
- Každá determinantní závislost musí být kandidátní klíč.

**Příklad porušení BCNF:**
- Tabulka „Flights“ obsahuje závislost „Destination → Pilot“, kde „Destination“ není superklíčem:
```
| Destination | Pilot       | Plane  | Day     |
|-------------|-------------|--------|---------|
| Paris       | cpt. Oiseau | Boeing | Monday  |
| Berlin      | cpt. Vogel  | Airbus | Monday  |
```

**Oprava:**
- Rozdělit tabulku tak, aby byly odstraněny závislosti, kde determinant není superklíčem:
```
Tabulka: Destinations
| Destination | Pilot       |
|-------------|-------------|
| Paris       | cpt. Oiseau |
| Berlin      | cpt. Vogel  |

Tabulka: FlightDetails
| Destination | Plane  | Day     |
|-------------|--------|---------|
| Paris       | Boeing | Monday  |
| Berlin      | Airbus | Monday  |
```
### Konceptuální model
1. **Konceptuální model (ERD):**
   - **Zadání:** Např. systém pro správu knihovny.
   - **ERD:** 
     - Entity: Kniha, Autor, Čtenář, Půjčka.
     - Vztahy: Kniha má Autora, Čtenář může půjčit Knihu.

2. **Převod na logický model:**
   - ERD se převádí na tabulky. Např.:
```
Tabulka: Kniha
| KnihaID | Název | AutorID | Rok |

Tabulka: Autor
| AutorID | Jméno | Příjmení |

Tabulka: Čtenář
| ČtenářID | Jméno | Příjmení | Adresa |

Tabulka: Půjčka
| PůjčkaID | KnihaID | ČtenářID | DatumPůjčky | DatumVrácení |
```

## Transakční zpracování

### ACID
1. **Popis ACID vlastností:**
   - **Atomicity (Atomicita):** Transakce je buď zcela provedena, nebo vůbec neprovedena.
   - **Consistency (Konzistence):** Transakce převádí databázi z jednoho konzistentního stavu do jiného konzistentního stavu.
   - **Isolation (Izolace):** Transakce probíhají nezávisle na sobě.
   - **Durability (Trvalost):** Jakmile je transakce potvrzena, její výsledek je trvalý i při výpadku systému.

### Vlastnosti rozvrhů
1. **Uspořádatelnost (Serializability):**
   - **Popis:** Rozvrh je uspořádatelný, pokud jeho výsledky odpovídají nějakému serialnímu rozvrhu, tj. transakce lze uspořádat tak, že dávají stejný výsledek jako při jejich sekvenčním vykonávání.
   
2. **Zotavitelnost (Recoverability):**
   - **Popis:** Rozvrh je zotavitelný, pokud nedochází k trvalé ztrátě dat při chybě, a systém se může zotavit do konzistentního stavu.

### Uzamykací protokoly
1. **Popis uzamykacích protokolů:**
   - Uzamykací protokoly jsou pravidla, která zajišťují, že transakce při paralelním provádění nevedou ke konfliktním situacím, např. dvoufázový uzamykací protokol (2PL).

2. **Použití:**
   - **Příklad:** Transakce T1 si zamkne záznam, provede operaci, poté záznam uvolní.

### Blokování
1. **Popis:**
   - **Blokování (Deadlock):** Situace, kdy dvě nebo více transakcí čekají na uvolnění zdrojů držených jinými transakcemi, což vede k nekonečnému čekání.
   - **Řešení:** Použití detekce blokování a rollbacku jedné z transakcí.

## Přehled SQL

### Význam
1. **Význam jednoduchého SQL dotazu:**
   - SQL dotazy umožňují získávat, aktualizovat, vkládat a mazat data v databázích. Např. dotaz `SELECT * FROM Zákazníci WHERE Jméno = 'Jan'` získá všechny záznamy o zákaznících se jménem Jan.

### Klauzule
1. **Popis účelu klauzulí:**
   - **SELECT:** Vybere data.
   - **FROM:** Určuje tabulky, ze kterých se data vybírají.
   - **WHERE:** Filtruje data podle podmínky.
   - **GROUP BY:** Seskupuje data.
   - **ORDER BY:** Řadí data.

### Příklady
1. **Jednoduchý SQL dotaz:**
   - **Zadání:** Získat všechny objednávky od zákazníka "Novak".
   - **Dotaz:** 
     ```sql
SELECT * 
FROM Objednávky 
JOIN Zákazníci ON Objednávky.ZákazníkID = Zákazníci.ZákazníkID 
WHERE Zákazníci.Jméno = 'Novak';
     ```

#### Agregace dat
1. **Použití klauzulí pro seskupování a agregaci:**
   - **Příklad:** Počítat celkový počet objednávek za každý měsíc.
   - **Dotaz:**
     ```sql
SELECT COUNT(*) AS PocetObjednavek, MONTH(Datum) AS Mesic
FROM Objednávky
GROUP BY MONTH(Datum);
     ```

### Vnořené dotazy
1. **Použití vnořených dotazů a testy na NULL hodnotu:**
   - **Příklad:** Zjistit zákazníky, kteří nemají žádnou objednávku.
   - **Dotaz:**
     ```sql
SELECT Zákazníci.Jméno
FROM Zákazníci
WHERE ZákazníkID NOT IN (SELECT ZákazníkID FROM Objednávky);
     ```

## Moderní databázové systémy

### Základní třídy moderních databázových systémů
1. **Třídy a jejich specifické vlastnosti:**
   - **Relational Databases (RDBMS):** Strukturovaná data, SQL, tabulky.
   - **NoSQL Databases:** Neschematické nebo méně strukturované, flexibilní datové modely, např. dokumentové databáze.
   - **NewSQL

:** Kombinují výhody SQL a NoSQL.
   - **In-Memory Databases:** Data uložena v paměti pro rychlý přístup.
   
2. **Příklad srovnání:** 
   - **RDBMS vs. NoSQL:**
     - RDBMS ukládá data ve striktně definovaných tabulkách.
     - NoSQL může ukládat data ve formě dokumentů (např. JSON), což umožňuje větší flexibilitu při ukládání různorodých dat.

### Big Data
1. **Popis a vlastnosti:**
   - **Big Data:** Vysoký objem, vysoká rychlost, velká rozmanitost, a proměnlivost dat.
   - **Příklad zdrojů:** Sociální sítě, IoT senzory.
   
2. **Výzvy:** 
   - Tradiční databázové systémy nejsou optimalizovány pro zpracování tak velkého množství dat v reálném čase, což vede k potřebě nových technologií jako Hadoop.

### Princip MapReduce
1. **Princip a aplikace:**
   - **MapReduce:** Distribuovaný způsob zpracování velkých dat. Mapovací fáze rozdělí úkol do menších částí, Reduce fáze je pak spojí.
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

2. **Výhody a nedostatky:** 
   - **Výhody:** Škálovatelnost, odolnost vůči chybám.
   - **Nedostatky:** Komplexita implementace, omezená flexibilita.

### NoSQL databáze
1. **Typy a vlastnosti:**
   - **Dokumentové databáze:** Ukládají data jako dokumenty (např. MongoDB).
   - **Klíč-hodnota databáze:** Data jsou ukládána jako páry klíč-hodnota (např. Redis).
   - **Sloupcové databáze:** Ukládají data po sloupcích, nikoliv po řádcích (např. Cassandra).
   - **Grafové databáze:** Specializované na reprezentaci a zpracování grafových struktur (např. Neo4j).

2. **Příklad rozdílů:**
   - **Relace vs. Dokument:** Relace jsou pevně definované struktury, dokumenty mohou obsahovat různá pole pro různé záznamy.

### Grafové databáze
1. **Datový model:**
   - **Popis:** Grafová databáze ukládá data ve formě uzlů a hran, což umožňuje efektivní práci s komplexními vztahy mezi daty.
   
2. **Příklad:**
   - **Model pro sociální síť:** Uzly představují uživatele, hrany reprezentují přátelství mezi uživateli.
   - **Dotaz:** Najít všechny přátele přátel uživatele "Jan".

### Multi-model databáze a polystore
1. **Rozdíly, výhody a nevýhody:**
   - **Multi-model:** Umožňuje ukládat a dotazovat se na data v různých formátech (dokumenty, grafy, tabulky) v rámci jednoho systému.
   - **Polystore:** Integruje více různých databázových systémů a umožňuje provádění dotazů napříč těmito systémy.

2. **Příklad multi-model dotazu:**
   - **Dotaz:** Vyhledat data z tabulky a z dokumentové databáze v jednom dotazu.
   
   **Možné problémy:** Výkon může být nižší kvůli nutnosti kombinovat různé typy dotazovacích mechanizmů, může být složitější ladění a optimalizace.