---
dg-publish: true
tags:
  - architektura_pc_a_os
  - spolecna_informatika
  - tomas
---
[[Example of Implementing Controller]]
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

**Rozhraní periferních zařízení a jejich obsluha** se týká způsobu, jakým počítač komunikuje s různými externími zařízeními, jako jsou myš, klávesnice, diskové jednotky, tiskárny atd. Tento proces zahrnuje jak hardware, tak software, a klíčovou roli v tomto hraje **řadič zařízení** a **přerušení**.

### 1. Roli řadiče zařízení při programem řízené obsluze zařízení (PIO)
Programem řízená obsluha zařízení, známá také jako **Programmed Input/Output (PIO)**, je způsob komunikace mezi procesorem a periferním zařízením, kde procesor přímo ovládá vstup a výstup dat z těchto zařízení.

- **Řadič zařízení (Device Controller)**:
    - Řadič zařízení je specializovaný hardware, který je zodpovědný za řízení a správu komunikace mezi procesorem a periferními zařízeními.
    - Je napojen na sběrnici (bus) systému a poskytuje rozhraní mezi systémovou sběrnicí a konkrétním zařízením.
    - Řadič má obvykle několik **vstupních a výstupních portů**, které se používají pro přenos dat mezi procesorem a zařízením. Tyto porty mají specifické adresy, které jsou pevně přidělené.
    - Procesor může číst data z těchto vstupních portů nebo zapisovat data do výstupních portů pomocí příslušných instrukcí (např. `IN` a `OUT` v x86 architektuře).
    - Procesor v režimu PIO provádí pravidelné čtení/zápisy do portů, aby přenesl data mezi zařízením a pamětí, což může být pomalé a neefektivní, protože procesor musí čekat na dokončení každé operace.

**Příklad: Programem řízená obsluha myši**
    - Myš je připojena k řadiči, který je mapován na určitou sadu adres v paměti.
    - Procesor pravidelně čte z adresy (např. vstupního portu) přiřazené myši, aby zjistil pohyb nebo kliknutí.
    - Pokud procesor detekuje nové údaje (např. pohyb), provede příslušné akce, např. aktualizuje kurzor na obrazovce.

### 2. Roli přerušení při programem řízené obsluze zařízení (PIO)
Přerušení jsou mechanismem, který umožňuje efektivnější správu komunikace mezi procesorem a periferními zařízeními.

- **Přerušení (Interrupts)**:
    - Přerušení je signál od periferního zařízení směrem k procesoru, který informuje, že zařízení vyžaduje pozornost.
    - Když zařízení potřebuje odeslat nebo přijmout data, místo toho, aby procesor neustále kontroloval stav zařízení (jak je tomu u polling), zařízení vyšle přerušení.
    - Procesor po přijetí přerušení pozastaví aktuální vykonávaný program a přepne se na tzv. **obsluhu přerušení** (Interrupt Service Routine - ISR), což je speciální část kódu, která zpracovává požadavek zařízení.
    - Po dokončení obsluhy přerušení se procesor vrátí k vykonávání původního programu.

**Reakce procesoru a operačního systému na přerušení**:
1. **Hardwarová reakce**:
    - Zařízení generuje signál přerušení, který je odeslán na procesor.
    - Procesor dokončí aktuálně prováděnou instrukci a poté pozastaví další instrukce.
    - Procesor uloží aktuální stav (kontext) na zásobník, aby mohl pokračovat tam, kde skončil.
    - Procesor identifikuje typ přerušení a volá příslušnou ISR.
2. **Softwarová reakce**:
    - Operační systém zajišťuje, že ISR je správně spustitelná a přiřazená danému přerušení.
    - ISR vykonává požadované akce, například načte data z řadiče zařízení nebo provede další potřebné úkony.
    - Po dokončení ISR, operační systém obnoví původní kontext a vrátí kontrolu nad CPU zpět do přerušené aplikace.

**Příklad: Přerušení u disku**
    - Disk po dokončení operace čtení/zápisu dat vyšle přerušení.
    - Procesor přepne na ISR, která zpracuje data a informuje operační systém, že operace byla dokončena.
    - Procesor pak pokračuje ve své původní činnosti.

Přerušení zajišťují, že procesor není zbytečně blokován čekáním na periferní zařízení a může efektivně využívat svůj čas k dalším úkolům.

