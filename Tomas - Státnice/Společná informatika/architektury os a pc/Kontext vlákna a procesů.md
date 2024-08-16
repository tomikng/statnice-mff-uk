---
dg-publish: true
tags:
  - architektura_pc_a_os
  - spolecna_informatika
  - tomas
---

> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

**Kontext** je souhrn všech informací, které operační systém potřebuje k tomu, aby mohl pokračovat ve vykonávání procesu nebo vlákna po jeho přerušení. Tento kontext zahrnuje různé druhy informací, které se liší podle toho, zda se jedná o proces nebo vlákno.

#### 1. **Kontext Procesu**

Proces je samostatná instance programu, který běží v operačním systému. Každý proces má svůj vlastní kontext, který obsahuje následující informace:

- **Adresní prostor**: Každý proces má svůj vlastní adresní prostor, který zahrnuje kód programu, data, zásobník a dynamicky alokovanou paměť (heap).
- **Stav registrů procesoru**: To zahrnuje obsah všech registrů procesoru, jako jsou instrukční čítač (program counter), registr zásobníku a další, které určují stav procesu v daném okamžiku.
- **Otevřené soubory a I/O zařízení**: Seznam všech souborů a zařízení, ke kterým má proces přístup.
- **Tabulka stránek**: Informace o mapování mezi virtuální a fyzickou pamětí, což umožňuje procesu používat virtuální adresy.
- **Bezpečnostní atributy**: Informace o oprávněních a identitě uživatele, pod kterým proces běží.
- **Stav procesu**: Aktuální stav procesu, například zda je připraven k běhu, běží, blokován, nebo byl ukončen.

#### 2. **Kontext Vlákna**

Vlákno je lehčí jednotka vykonávání, která existuje uvnitř procesu. Všechna vlákna v procesu sdílejí jeho adresní prostor a systémové prostředky, ale každé vlákno má svůj vlastní kontext, který obsahuje:

- **Stav registrů procesoru**: Podobně jako u procesu, ale pouze pro dané vlákno. Zahrnuje obsah registrů specifických pro vlákno, jako je instrukční čítač a registr zásobníku.
- **Zásobník**: Každé vlákno má svůj vlastní zásobník, který obsahuje lokální proměnné a informace o volání funkcí.
- **Vlákno-specifické data**: Některé operační systémy umožňují každému vláknu mít svůj vlastní datový prostor pro uložení hodnot specifických pro vlákno.
- **Stav vlákna**: Aktuální stav vlákna, jako je běžící, připravené, blokované, apod.

### Rozdíly mezi Kontextem Procesu a Vlákna

- **Sdílené prostředky**: Všechna vlákna v jednom procesu sdílejí stejný adresní prostor a systémové prostředky, což umožňuje efektivnější komunikaci a spolupráci mezi vlákny. Naproti tomu každý proces má svůj vlastní oddělený kontext, což zajišťuje větší bezpečnost a izolaci mezi procesy.
  
- **Přepínání kontextu (context switching)**: Přepnutí mezi dvěma procesy je obvykle náročnější než přepnutí mezi dvěma vlákny, protože vyžaduje uložení a obnovení více informací, jako jsou tabulky stránek a adresní prostory. Přepnutí mezi vlákny v rámci jednoho procesu je rychlejší, protože většina těchto informací je sdílená.

### Příklad

Představme si aplikaci, která má jedno hlavní vlákno (hlavní program) a několik vedlejších vláken pro různé úlohy (např. zpracování dat, vykreslování uživatelského rozhraní, atd.). Každé vlákno má svůj vlastní zásobník a stav registrů, takže může nezávisle vykonávat své úkoly, ale všechna vlákna sdílejí stejný adresní prostor, což umožňuje snadnou spolupráci a komunikaci mezi nimi. Na druhou stranu, pokud spustíme dva různé procesy, každý z nich bude mít svůj vlastní, oddělený kontext, což zajistí, že nemohou přímo zasahovat do paměti a prostředků toho druhého.