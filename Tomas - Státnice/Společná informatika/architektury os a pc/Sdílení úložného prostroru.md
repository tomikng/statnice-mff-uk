
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě [prezentace](https://cdn.tom-nguyen.dev/05-os.pdf).

**Sdílení úložného prostoru:**
V operačních systémech sdílení úložného prostoru představuje způsob, jakým jsou fyzické hardwarové zdroje, konkrétně úložná zařízení (například pevné disky, SSD), spravovány a sdíleny mezi více aplikacemi a uživateli. Operační systém spravuje přístup k těmto úložným zařízením a poskytuje služby, které umožňují více procesům přístup k datům, přičemž zajišťuje ochranu a bezpečnost dat. Například při čtení nebo zápisu dat do souboru operační systém zajišťuje, aby různé procesy měly řízený přístup, což zabraňuje konfliktním operacím a zajišťuje integritu dat.

**Analogie s adresovým prostorem:**
Adresový prostor procesu v paměti může být srovnáván s organizací souborů v souborovém systému. Stejně jako je adresový prostor procesu rozdělen na segmenty nebo [[Stránkování|stránky]] (v závislosti na využívaném modelu správy paměti, například segmentace nebo stránkování), souborový systém organizuje data pomocí struktur, jako jsou adresáře a inody.

- **Adresářová struktura:** Adresáře v souborovém systému mohou být analogické segmentům v paměti, kde každý adresář obsahuje odkazy na soubory nebo podadresáře, stejně jako segmenty obsahují instrukce a data.
  
- **Inody a bloky:** Inody v souborových systémech jako ext2/ext3/ext4 obsahují metadata o souborech (například velikost, vlastník, přístupová práva) a ukazatele na datové bloky, kde jsou skutečně uložena data souboru. Tento přístup lze srovnat s tabulkami stránek, které v paměťovém managementu určují fyzické adresy odpovídající virtuálním adresám v procesu.

### Abstrakce a rozhraní pro práci se soubory

**Abstrakce pro práci se soubory:**
Operační systémy poskytují různé úrovně abstrakce, které usnadňují práci se soubory a umožňují aplikacím manipulovat s daty bez nutnosti znát detaily o fyzickém úložišti.

- **Soubory jako abstraktní jednotky dat:** Soubory jsou základní jednotkou organizace dat v souborovém systému. Každý soubor je abstraktním proudem dat (bajtů), který může být uložen na různých typech fyzických médií (pevné disky, SSD, síťová úložiště atd.). Operační systém nevyžaduje, aby aplikace rozuměly fyzickému formátu dat na disku; místo toho poskytuje jednotné rozhraní pro operace se soubory.

- **Souborové operace:** Mezi základní operace, které lze provádět se soubory, patří otevírání souborů (`open`), čtení dat ze souborů (`read`), zápis do souborů (`write`), přesouvání pozice v souboru (`lseek`), uzavírání souborů (`close`), vytváření nových souborů (`create`), mazání souborů (`delete`) a další. Tyto operace jsou obvykle realizovány prostřednictvím systémových volání (syscall) nebo standardních knihoven (např. v jazyce C `fopen`, `fread`, `fwrite`).

- **Rozhraní pro práci se soubory:** Pro každou operaci se souborem operační systém poskytuje rozhraní, které umožňuje aplikacím pracovat se soubory na vyšší úrovni abstrakce. Toto rozhraní skrývá detaily implementace a poskytuje standardizované funkce pro manipulaci se soubory.

- **Příklady souborových operací v různých prostředích:**
  - **Standardní knihovna v C:** Například `fopen`, `fseek`, `fgets`, `fclose` jsou funkce poskytované standardní knihovnou jazyka C pro práci se soubory.
  - **POSIX rozhraní:** `open`, `lseek`, `read`, `close` jsou příklady systémových volání dostupných v POSIX kompatibilních operačních systémech, které umožňují přímou práci se soubory.

- **Atributy souborů:** Soubory mají různé atributy, jako je velikost, čas poslední úpravy, vlastník, přístupová práva a další. Tyto atributy jsou spravovány operačním systémem a mohou být zobrazeny nebo změněny pomocí specifických příkazů, například `stat` v Unixových systémech.

- **Adresáře:** Adresáře v souborovém systému fungují jako sbírky souborů, což umožňuje jejich efektivní organizaci a snadné vyhledávání. Adresáře mohou obsahovat další podadresáře, čímž vzniká hierarchická struktura, která uživatelům umožňuje lepší navigaci a logické uspořádání dat.

- **Odkazy (Links):** Soubory mohou mít různé typy odkazů, například tvrdé odkazy (hard links), které umožňují více adresářovým položkám odkazovat na stejný fyzický soubor, nebo symbolické odkazy (symlinks), které jsou speciálními soubory, jejichž obsah odkazuje na jinou cestu k souboru.

- **Soubory v síti a virtuální soubory:** Operační systémy také podporují práci se soubory přes síť nebo využití virtuálních souborů, které poskytují další systémové funkce, jako jsou `/dev/null`, `/dev/urandom`, `/proc/cpuinfo` a další.

Tato komplexní sada abstrakcí a rozhraní umožňuje aplikacím a uživatelům pracovat se soubory a adresáři způsobem, který je jednoduchý a nezávislý na specifikách fyzického úložiště nebo hardwarové architektury.