---
tags:
  - databaze
  - databaze_a_web
  - tomas
---
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
