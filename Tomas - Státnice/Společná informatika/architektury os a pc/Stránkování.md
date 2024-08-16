---
dg-publish: true
tags:
  - architektura_pc_a_os
  - tomas
  - spolecna_informatika
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě naučených vědomostí z přednášek pc systému 

**Stránkování** je technika správy paměti, která eliminuje potřebu spojitého přidělování fyzické paměti. Místo toho jsou virtuální adresní prostor i fyzická paměť rozděleny na stejně velké bloky, které nazýváme **stránky** (v případě virtuální paměti) a **rámce** (v případě fyzické paměti).

![[Pasted image 20240816163536.png]]

#### **Základní Pojmy Stránkování:**

1. **Stránky a Rámce:**
   - **Stránka**: Blok virtuální paměti o pevné velikosti.
   - **Rámec**: Blok fyzické paměti o stejné velikosti jako stránka.

   Virtuální paměť je rozdělena na stránky, zatímco fyzická paměť je rozdělena na rámce. Když se proces spouští, jeho stránky jsou načteny do dostupných rámců paměti.

2. **Stránkovací Tabulka:**
   - Každý proces má svou **stránkovací tabulku**, která mapuje virtuální stránky na fyzické rámce. Stránkovací tabulka obsahuje základní adresy jednotlivých stránek ve fyzické paměti.

3. **Překlad Adres:**
   - Procesor generuje **virtuální adresu**, která je rozdělena na dvě části: **číslo stránky** a **offset**. Číslo stránky se používá k indexování do stránkovací tabulky, aby se našlo odpovídající číslo rámce. K základní adrese rámce se přičte offset a vznikne tak fyzická adresa.

![[Pasted image 20240816163837.png]]

#### **Příklad: Stránkování v Práci**

Představme si příklad se základním scénářem:

- Máme systém s virtuálním adresním prostorem 16 stránek, přičemž každá stránka má velikost 1KB. Fyzická paměť má velikost 64KB a je rozdělena na 16 rámců.

- **Struktura Virtuální Adresy**:
  - Číslo stránky: 4 bity (protože máme 16 stránek, a 2^4 = 16)
  - Offset: 10 bitů (protože každá stránka má 1KB, a 2^10 = 1024 bajtů)

Předpokládejme, že proces má následující stránky načteny v paměti:

| Virtuální Stránka | Fyzický Rámec |
|-------------------|---------------|
| 0                 | 5             |
| 1                 | 10            |
| 2                 | 3             |
| 3                 | 8             |

Pokud proces generuje virtuální adresu `0x0205` (což je v šestnáctkové soustavě a přeloží se do binární podoby jako `0000 0010 0000 0101`):

1. **Číslo Stránky**: První 4 bity (`0000`) odpovídají stránce `2`.
2. **Offset**: Dalších 10 bitů (`0000 0101`) je offset v rámci této stránky.

Pomocí stránkovací tabulky systém zjistí, že virtuální stránka `2` je mapována na fyzický rámec `3`. Konečná fyzická adresa je základní adresa rámce `3` plus offset `5`, což se přeloží do skutečné adresy v RAM.

#### **Výhody Stránkování:**

- **Odstranění Externí Fragmentace**: Díky tomu, že stránky a rámce mají pevnou velikost, nedochází k externí fragmentaci.
- **Efektivní Využití Paměti**: Stránky mohou být načteny do libovolného dostupného rámce paměti, což umožňuje efektivní využití paměti.

#### **Stránkovací Chyby (Page Faults):**
**Stránkovací chyba** nastane, když se proces pokusí přistoupit na stránku, která není aktuálně mapována na fyzický rámec (tj. stránka není v RAM). Operační systém pak musí načíst požadovanou stránku z sekundárního úložiště (např. disku) do paměti.

**Příklad Stránkovací Chyby:**
Pokud se proces pokusí přistoupit na stránku, která nebyla načtena do RAM (např. virtuální stránka 4 v našem příkladu), procesor vyvolá stránkovací chybu. Operační systém pak provede následující kroky:
1. Najde dostupný rámec ve fyzické paměti.
2. Načte požadovanou stránku z disku do tohoto rámce.
3. Aktualizuje stránkovací tabulku tak, aby odrážela nové mapování.

Po zpracování stránkovací chyby proces pokračuje, jako by k chybě nedošlo.