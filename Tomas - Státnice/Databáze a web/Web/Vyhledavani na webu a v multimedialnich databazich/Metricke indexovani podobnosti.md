---
dg-publish: true
tags:
  - tomas
  - databaze_a_web
  - web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek

# Metrické Indexování Podobnosti

## Úvod do metrického indexování
Metrické indexování podobnosti se zaměřuje na zefektivnění vyhledávání v databázích, kde se podobnost mezi objekty měří pomocí metrických vzdáleností. Tyto metody umožňují rychlé a efektivní vyhledávání objektů, které jsou podobné zadanému dotazu, přičemž základní myšlenkou je využití metrického prostoru a vlastností metrické vzdálenosti (reflexivita, symetrie, trojúhelníková nerovnost).

## Metrické metody přístupu (MAM - Metric Access Methods)
Metrické metody přístupu zahrnují různé techniky indexování, které využívají vlastností metrických prostorů k urychlení dotazů na podobnost.

### Pivotní tabulky (Pivot Tables)

#### Příklad: Hledání Podobných Přátel podle Zájmu

**Scénář:** Představte si, že máte skupinu přátel a chcete zjistit, kdo má podobné zájmy jako vy. Vyberete jednoho z přátel, například "Alice," jako pivot.

**Kroky:**
1. Vypočítáte vzdálenost (rozdílnost zájmů) každého přítele od Alice.
2. Použijete tyto vzdálenosti k filtrování přátel, kteří mají podobné zájmy.

**Tabulka Vzdáleností:**

| Přítel  | Vzdálenost od Alice |
|---------|---------------------|
| Bob     | 2                   |
| Charlie | 1                   |
| Diana   | 3                   |

**Vizualizace:**
```
+--------+
|  Alice |
+--------+
```
```
+--------+-----------------+---------+
| Přítel | Vzdálenost od A | Zahrnout?|
+--------+-----------------+---------+
| Alice  | 0               | Ano     |
| Bob    | 2               | Ne      |
| Charlie| 1               | Ano     |
| Diana  | 3               | Ne      |
+--------+-----------------+---------+
```

### Hierarchické struktury

Hierarchické struktury používají k organizaci dat stromové struktury, které rozdělují metrický prostor na menší, spravovatelné oblasti.

#### Příklad: Organizace Přátel podle Zájmu v Hierarchii

**Scénář:** Představte si, že rozdělíte své přátele do skupin podle jejich zájmů, a tyto skupiny pak dále rozdělíte na menší podskupiny. Tímto způsobem vytváříte hierarchii, kde každá úroveň reprezentuje stále detailnější rozdělení přátel.

**Kroky:**
1. Nejprve rozdělíte přátele do velkých skupin podle hlavních zájmů.
2. Každou skupinu dále rozdělíte na podskupiny podle dalších zájmů.

**Vizualizace Hierarchie:**
```
              Všichni Přátelé
                    |
         +----------+----------+
         |                     |
     Fotbal                Technologie
         |                     |
    +----+----+            +----+----+
    |         |            |         |
 Lego      Gadgets      IT       Star Wars
```

### Hašované indexy

Hašované indexy používají speciální funkce, které přiřazují objekty do segmentů (bucketů) na základě jejich podobnosti, měřené pomocí pivotů.

#### Příklad: Hašování Přátel na Základě Zájmu

**Scénář:** Rozdělíte své přátele do různých skupin (bucketů) podle toho, jak jsou jejich zájmy podobné určitému pivotu (například "Fotbal").

**Kroky:**
1. Každého přítele přiřadíte do určitého bucketu na základě toho, jak moc se jeho zájmy shodují se zájmy určitého pivotu.
2. Pokud má přítel zájmy, které se výrazně liší, může být zařazen do speciální skupiny (exclusion set).

**Vizualizace Hašování:**
```
Pivot: Fotbal
Bucket 0: [Přítel A, Přítel B]
Bucket 1: [Přítel C]
Exclusion Set: [Přítel D, Přítel E]
```

### Hybridní indexy

Hybridní indexy kombinují různé přístupy metrického indexování pro dosažení maximální efektivity.

#### Příklad: Kombinace Hierarchie a Pivotních Tabulek

**Scénář:** Představte si, že vytvoříte hierarchii přátel podle jejich zájmů, a v každé úrovni hierarchie použijete pivoty k dalšímu filtrování.

**Kroky:**
1. Nejprve rozdělíte přátele do skupin podle zájmů.
2. V každé skupině zvolíte pivot a vypočítáte vzdálenosti ostatních přátel k tomuto pivotu.
3. Použijete tyto vzdálenosti k filtrování a dalšímu rozdělení skupin.

**Vizualizace Hybridního Indexu:**
```
Hierarchická Struktura:
  - Skupina Fotbal: Pivot - Alice
  - Skupina Technologie: Pivot - Bob

Pivotní Tabulky:
  - Fotbal (Alice): [Bob (2), Charlie (1)]
  - Technologie (Bob): [Alice (2), Diana (1)]
```

## Měření výkonu

### Výpočetní náklady

- **Počet výpočtů vzdáleností (DC):** Měří, kolik výpočtů je potřeba provést pro nalezení podobných objektů.
  
### I/O náklady

- **Přístup na disk:** Zohledňuje počet přístupů na disk, což je důležité při práci s velkými databázemi.

### Interní náklady

- **Složitost algoritmů:** Zahrnuje složitost algoritmů a datových struktur, které se používají k udržení indexu.

