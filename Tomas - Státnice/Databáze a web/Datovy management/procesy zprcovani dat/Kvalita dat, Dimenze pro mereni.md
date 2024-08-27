---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT. Na zaklade poznamek z prednasek.

# Datova kvalita
**Datová kvalita** se vztahuje k tomu, jak dobře data splňují požadavky na jejich použití. Neexistuje jednotná definice kvality dat, protože to, co je považováno za kvalitní data, může záviset na konkrétním kontextu a účelu, pro který jsou data používána. Kvalita dat zahrnuje několik dimenzí, které mohou zahrnovat přesnost, konzistenci, úplnost, aktuálnost a dostupnost dat.

**Význam pro uživatele:**
Kvalita dat je zásadní pro uživatele dat, protože přímo ovlivňuje jejich schopnost provádět přesné analýzy, vyvozovat správné závěry a přijímat informovaná rozhodnutí. Špatná kvalita dat může vést k chybám, zvýšeným nákladům, ztrátě času a dokonce k poškození pověsti organizace .

# Dimenze a jejich mereni
1. **Přesnost (Accuracy)**
   - **Definice:** Přesnost odkazuje na míru, do které jsou data správná, spolehlivá a certifikovaná. Hodnoty dat uložené v databázi by měly odpovídat skutečným hodnotám.
   - **Měření:** Přesnost lze měřit například tím, že se porovnají uložená data s ověřenými zdroji nebo skutečnými hodnotami. V praxi to může zahrnovat kontrolu, zda jsou adresy správně zadané nebo zda čísla odpovídají danému počtu desetinných míst.

2. **Úplnost (Completeness)**
   - **Definice:** Úplnost se týká toho, do jaké míry jsou data dostatečně podrobná a komplexní pro splnění konkrétního úkolu.
   - **Měření:** Úplnost se může měřit podle počtu chybějících záznamů nebo **nevyplněných polí v databázi**. Například v zákaznické databázi může být měřena úplnost podle toho, zda každý záznam obsahuje všechny požadované údaje.

3. **Konzistence (Consistency)**
   - **Definice:** Konzistence zajišťuje, že data nejsou v **rozporu s jinými daty nebo s definovanými sémantickými pravidly**.
   - **Měření:** Konzistence je často měřena **kontrolou**, zda nejsou v datech logické chyby, jako například zda **věk zákazníka není záporný** nebo zda stejná data nejsou v různých záznamech zapsána odlišně.

4. **Dostupnost (Availability)**
   - **Definice:** Dostupnost se vztahuje k tomu, jak snadno a rychle mohou být data přístupná a použita, když jsou potřebná.
   - **Měření:** Dostupnost se měří **jako procento času**, kdy jsou data přístupná ve srovnání s časem, kdy jsou nedostupná kvůli údržbě nebo technickým problémům.

5. **Aktuálnost (Timeliness)**
   - **Definice:** Aktuálnost odkazuje na to, jak **čerstvá jsou data a zda odrážejí aktuální situaci**.
   - **Měření:** Měření aktuálnosti může zahrnovat kontrolu, jak často jsou data aktualizována nebo jaký je časový odstup mezi sběrem dat a jejich dostupností pro uživatele.

6. **Srozumitelnost (Understandability)**
   - **Definice:** Srozumitelnost dat znamená, jak snadno mohou být data pochopena a interpretována uživateli.
   - **Měření:** Tato dimenze může být hodnocena například prostřednictvím zpětné vazby od uživatelů, kde se sleduje, jak dobře jsou schopni pochopit a využít data.

### Důležitost těchto dimenzí
Dimenze datové kvality jsou zásadní pro zajištění toho, aby data byla nejen spolehlivá a přesná, ale také snadno dostupná a použitelná pro různé analytické a operativní účely. Správná implementace těchto dimenzí pomáhá organizacím dosáhnout efektivnějšího rozhodování, lepšího řízení procesů a celkově vyšší konkurenceschopnosti na trhu .