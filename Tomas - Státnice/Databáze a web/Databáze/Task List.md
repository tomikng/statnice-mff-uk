---
tags:
  - databaze
  - databaze_a_web
---
# Seznam úkolů: Plán studia databázových systémů

## 1. Architektura databázových systémů
[[Architektury databázových systémů]]
- [x] **Pochopit konceptuální, logickou a fyzickou úroveň:** ✅ 2024-08-12
  - Naučit se rozdíly mezi konceptuálním, logickým a fyzickým modelem databáze.
  - Studovat příklady každé úrovně, jako jsou ER diagramy, relační schémata a strategie indexování.

## 2. Normální formy
[[Tomas - Státnice/Databáze a web/Databáze/Poznámky/Normální formy|Normální formy]]
- [x] **1. Normální forma (1NF):** ✅ 2024-08-12
  - Pochopit koncept atomických hodnot.
  - Naučit se, jak transformovat tabulky, které nejsou v 1NF, na 1NF.
  
- [x] **2. Normální forma (2NF):** ✅ 2024-08-12
  - Studovat koncept plné funkční závislosti.
  - Procvičit převod tabulek, které porušují 2NF, na správné formy.
  
- [x] **3. Normální forma (3NF):** ✅ 2024-08-12
  - Naučit se, jak odstranit transitivní závislosti.
  - Procvičit normalizaci z 2NF na 3NF.
  
- [x] **Boyce-Coddova normální forma (BCNF):** ✅ 2024-08-12
  - Pochopit koncept superklíčů a kandidátních klíčů.
  - Studovat, jak převést tabulky do BCNF.

## 3. Konceptuální modelování
[[Architektury databázových systémů]]
- [x] **Entitně-relační diagram (ERD):** ✅ 2024-08-12
  - Procvičit návrh ERD pro různé systémy.
  - Naučit se identifikovat entity, atributy a vztahy.
  
- [x] **Převod na logický model:** ✅ 2024-08-12
  - Procvičit převod ERD na relační schémata.
  - Naučit se definovat tabulky, klíče a vztahy na základě ERD.

## 4. Transakční zpracování
[[Transakční zpracování]]
- [x] **ACID vlastnosti:** ✅ 2024-08-13
  - Studovat ACID vlastnosti: Atomicita, Konzistence, Izolace, Trvalost.
  - Pochopit reálné příklady dodržování ACID vlastností v databázových systémech.
  
- [x] **Vlastnosti rozvrhů:** ✅ 2024-08-13
  - Naučit se o serializovatelnosti a zotavitelnosti v rozvrzích transakcí.
  - Co je uspořádatelnost
  
- [x] **Uzamykací protokoly:** ✅ 2024-08-13
  - Studovat dvoufázový uzamykací protokol (2PL).
  - Pochopit, jak uzamykací protokoly zabraňují konfliktům při souběžném provádění transakcí.
  
- [x] **Řešení blokování:** ✅ 2024-08-13
  - Naučit se, co způsobuje blokování a jak mu předcházet nebo jej řešit.
  - Studovat detekci blokování a strategie rollbacku.

## 5. Zvládnutí SQL
[[SQL]]
- [x] **Základy SQL dotazů:** ✅ 2024-08-14
  - Procvičit psaní základních SQL dotazů pomocí `SELECT`, `FROM`, `WHERE`, `GROUP BY` a `ORDER BY`.
  - Pochopit účel každé klauzule v SQL dotazu.
  
- [x] **Pokročilé techniky SQL:** ✅ 2024-08-14
  - Naučit se provádět agregaci dat pomocí funkcí jako `COUNT`, `SUM`, `AVG`.
  - Procvičit psaní složitých SQL dotazů s joiny a poddotazy.
  
- [x] **Práce s hodnotami NULL:** ✅ 2024-08-14
  - Pochopit, jak testovat hodnoty NULL v SQL.
  - Procvičit psaní dotazů, které správně pracují s hodnotami NULL.
## 6. Moderní databázové systémy
[[Moderní databázové systémy]]
- [x] Vyjmenovat základní třídy moderních databázových systémů a krátce popsat jejich specifické vlastnosti. Pomocí jednoduchého příkladu srovnat jejich vlastnosti s tradičními (SQL) databázemi. ✅ 2024-08-14

- [x] Vysvětlit pojem Big Data, alespoň čtyři základní vlastnosti a jejich význam. Specifikovat alespoň dva příklady zdrojů velkých dat. Vysvětlit nové výzvy a problémy pro tradiční databázové systémy. ✅ 2024-08-14

- [ ] Vysvětlit princip MapReduce a zapsat v pseudokódu jednoduchý příklad jeho aplikace na konkrétní úlohu. Popsat výhody a nedostatky tohoto principu, zmínit alternativní přístupy. 

- [ ] Specifikovat typy, vlastnosti, výhody a nevýhody NoSQL databází. Ukázat rozdíly příslušných modelů na jednoduchém příkladu. 

- [ ] Specifikovat datový model grafové databáze, vytvořit jednoduchý příklad. Specifikovat třídy grafových dotazů, uvést jednoduché příklady použití.

- [x] Specifikovat rozdíly, výhody a nevýhody multi-model databáze. Jednoduchý příklad ✅ 2024-08-14