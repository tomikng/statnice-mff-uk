---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Proces Sestavení Programu
Sestavení programu v C# zahrnuje několik kroků:
1. **Překlad** (compilation): Překlad zdrojového kódu (C#) do meziproduktu (IL - Intermediate Language).
2. **Linkování**: Spojení všech meziproduktů, knihoven a závislostí do finálního spustitelného souboru (.exe nebo .dll).

#### Oddělený Překlad (Separate Compilation)
Oddělený překlad umožňuje překládat jednotlivé části programu (např. různé třídy nebo moduly) nezávisle na sobě. Každý modul je přeložen do vlastního IL souboru, který je později spojen při linkování.

**Výhody:**
- Urychluje sestavení tím, že nemusí být překládán celý projekt znovu při každé změně.
- Umožňuje lepší organizaci a modulárnost kódu.

#### Linkování
Linkování je proces, při kterém jsou různé přeložené moduly a knihovny spojeny dohromady do jednoho spustitelného souboru. V .NET prostředí je linkování součástí kompilace, kde všechny potřebné IL soubory a závislosti jsou zahrnuty do výsledného .exe nebo .dll souboru.

**Příklad:**
Pokud máte tři různé zdrojové soubory, nejprve jsou nezávisle přeloženy do IL a následně spojeny do jednoho výstupního souboru.

### Shrnutí
- **Proces sestavení**: Překlad C# kódu do IL a následné linkování.
- **Oddělený překlad**: Překlad jednotlivých částí programu samostatně, zlepšuje efektivitu.
- **Linkování**: Spojení všech přeložených částí do finálního spustitelného souboru.