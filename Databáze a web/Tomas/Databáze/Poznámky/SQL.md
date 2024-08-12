---
tags:
  - databaze
  - databaze_a_web
  - tomas
---
## Přehled SQL [🔗](https://www.sql-practice.com/)

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
