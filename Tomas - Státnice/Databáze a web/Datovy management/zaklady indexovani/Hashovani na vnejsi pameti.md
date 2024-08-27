---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Holubovy

# Externí Hashovací Algoritmy

Externí hashování je metoda používaná k organizaci a přístupu k datům uloženým na sekundární paměti, jako jsou disky. Na rozdíl od interního hashování, které operuje v rámci omezení hlavní paměti, musí externí hashování efektivně spravovat větší datové sady, které se nevejdou do RAM. Níže jsou uvedena podrobná vysvětlení a příklady různých externích hashovacích algoritmů.

## Faginovo Dynamické Hashování

### Princip
Faginovo dynamické hashování je technika, která umožňuje dynamické přizpůsobení hashovací struktury na základě růstu nebo zmenšování množství dat. Tento přístup eliminuje nutnost předem znát velikost dat a zabraňuje penalizaci výkonu při přidávání nových záznamů.

### Klíčové koncepty
- **Adresářová struktura (Directory-Based Structure):** Adresář uchovává ukazatele na jednotlivé stránky (buckets), kde jsou data uložena. Adresář umožňuje dynamické změny velikosti na základě potřeby.
  - **Globální hloubka (dG):** Počet bitů potřebných k odlišení záznamů ve všech stránkách.
  - **Lokální hloubka (dL):** Počet bitů společných pro všechny záznamy v dané stránce.
- **Hashovací funkce:** Vrací řetězec bitů, který určuje, do které stránky bude záznam uložen.

### Příklad
Představte si, že máte adresář s globální hloubkou dG = 3. Pokud je stránka plná a nelze do ní přidat další záznam, stránka se rozdělí, což může vést k rozšíření adresáře.

**Adresář:**
```
000 -> Stránka A
001 -> Stránka B
010 -> Stránka C
011 -> Stránka D
100 -> Stránka E
101 -> Stránka F
110 -> Stránka G
111 -> Stránka H
```

Pokud stránka B (001) přeteče, dojde k jejímu rozdělení a aktualizaci adresáře.

### Výhody a Nevýhody
- **Výhody:** Dynamické přizpůsobení velikosti datové struktury a udržení konstantního výkonu.
- **Nevýhody:** Velikost adresáře může růst, což může vést k problémům s pamětí a výkonem.

## Larson & Kajla's Perfektní Hashování

### Princip
Perfektní hashování podle Larsona a Kajly je technika statického hashování, která vyžaduje předem znalost velikosti dat. Používá dvě sady hashovacích funkcí: jednu pro generování adresy stránky a druhou pro generování signatur.

### Klíčové koncepty
- **Dvojice hashovacích funkcí:** 
  - **hi(k):** Generuje sekvenci adres stránek, kam může být záznam vložen.
  - **si(k):** Generuje d-bitové řetězce (signatury), které musí být menší než určitý separator pro vložení do stránky.
- **Separator:** Určuje maximální hodnotu signatury, kterou může stránka obsahovat. Záznamy jsou v rámci stránky seřazeny podle signatury.

### Příklad
Pokud máte klíč `ab` s hodnotami hashovací funkce `h1(ab) = 10` a signaturou `s1(ab) = 1011`, tento záznam bude vložen do příslušné stránky za předpokladu, že signatura je menší než separator.

**Struktura Stránek:**
```
Stránka 10:
od-0100 (separator: 1000)
Stránka 46:
ef-0100, gh-1000 (separator: 1001)
Stránka 95:
kl-0100, mn-1001 (separator: 1111)
```

### Výhody a Nevýhody
- **Výhody:** Optimalizace pro čtení dat a prevence přetečení.
- **Nevýhody:** Potřeba předem definované velikosti dat a složitost implementace.

## Cormackovo Perfektní Hashování

### Princip
Cormackovo perfektní hashování se zaměřuje na minimalizaci kolizí pomocí sady nezávislých hashovacích funkcí. Tato metoda vyžaduje pevně danou velikost adresáře a používá dvojúrovňový systém hashování.

### Klíčové koncepty
- **Primární hashovací funkce (h(k,s)):** Používá se pro výběr záznamu z adresáře.
- **Sekundární hashovací funkce (hi(k, r)):** Používá se pro řešení kolizí v rámci adresáře.
- **Úroveň přesměrování (Level of Indirection):** Adresář uchovává ukazatele na kolizní záznamy.

### Příklad
Představte si, že hashovací funkce `h(k) = k mod 7` generuje počáteční pozici v adresáři. Pokud dojde ke kolizi, použije se sekundární hashovací funkce k nalezení volného místa.

**Adresář:**
```
Pozice 0: prázdné
Pozice 1: prázdné
Pozice 2: klíč 14
Pozice 3: klíč 17
```

Pokud dojde ke kolizi, například mezi klíči 14 a 21, použije se další hashovací funkce k rozlišení těchto klíčů a umístění do volného místa.

### Výhody a Nevýhody
- **Výhody:** Efektivní řešení kolizí a minimalizace přetečení.
- **Nevýhody:** Potřeba přesného plánování velikosti adresáře a složitost výběru vhodných hashovacích funkcí.
