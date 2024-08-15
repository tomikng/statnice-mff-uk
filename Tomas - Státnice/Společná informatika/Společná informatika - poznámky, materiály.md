---
tags:
  - tomas
  - spolecna_informatika
dg-publish: true
---
## Architektura počítačů a operačních systémů
Struktura byla převzata od [Tomáše Slámy](slama.dev) a přizpůsobeno na 2023/2024.
- [Poznámky z Principu počítačů od Tomáše Slámy](https://slama.dev/poznamky/principy-pocitacu/)
- [Počítačové systémy](https://cdn.tom-nguyen.dev/ps.pdf)

- Základní architektura počítače. [🔗](https://slama.dev/poznamky-z-prednasky/principy-pocitacu/#zjednodu%C5%A1en%C3%A9-sch%C3%A9ma-po%C4%8D%C3%ADta%C4%8De) [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=24)
	- reprezentace a přístup k datům v paměti, adresa, adresový prostor [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=57)
    - ukládání jednoduchých a složených datových typů [🔗](https://cdn.tom-nguyen.dev/Architektura%20poc%CC%8Ci%CC%81tac%CC%8Cu%CC%8A%20a%20operac%CC%8Cni%CC%81ch%20syste%CC%81mu%CC%8A.pdf#page=2)
	    - Float [🔗](https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/)
    - základní aritmetické a logické operace
- Instrukční sada, vazba na vyšší programovací jazyky. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=29)
- Podpora pro běh operačního systému. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=97)
	- privilegovaný a neprivilegovaný režim procesoru
    - jádro operačního systému
- Rozhraní periferních zařízení a jejich obsluha. [🔗](https://slama.dev/poznamky-z-prednasky/principy-pocitacu/#otro%C4%8Dina) [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=105) [[Rozhraní periferních zařízení a jejich obsluha]]
	- Popsat roli řadiče zařízení při programem řízené obsluze zařízení (PIO), pro zadané adresy a funkce vstupních a výstupních portů implementovat programem řízenou obsluhu zadaného zařízení (myš, disk)
    - Popsat roli přerušení při programem řízené obsluze zařízení (PIO), na úrovni vykonávání instrukcí popsat reakci procesoru (hardware) a operačního systému (software) na žádost o přerušení
- Základní abstrakce, rozhraní a mechanizmy OS pro běh programů, sdílení prostředků a vstup/výstup. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=97)
	- neprivilegované (uživatelské) procesy
    - sdílení procesoru
	    - procesy, vlákna, kontext procesu a vlákna
        - přepínání kontextu, kooperativní a preemptivní multitasking
        - plánování běhu procesů a vláken, stavy vlákna
    - sdílení paměti
	    - Vysvětlit rozdíl mezi virtuální a fyzickou adresou a identifikovat, zda se v zadaném kontextu či fragmentu kódu používá virtuální nebo fyzická adresa
        - Na zadaném příkladu identifikovat a vysvětlit význam komponent virtuální a fyzické adresy (číslo stránky, číslo rámce, offset)
        - Pro konkrétní adresy a obsah jednoúrovňové stránkovací tabulky řešit úlohy překladu adres
        - Vysvětlit roli virtuálních adresových prostorů v ochraně paměti procesů a vláken
    - sdílení úložného prostoru
	    - soubory, analogie s adresovým prostorem
        - abstrakce a rozhraní pro práci se soubory
- Paralelismus, vlákna a rozhraní pro jejich správu, synchronizace vláken. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=112)
	- časově závislé chyby (race conditions)
    - kritická sekce, vzájemné vyloučení
    - základní sychronizační primitiva, jejich rozhraní a použití
	    - zámky
        - aktivní a pasivní čekání
## Autogramy
- [[Autogramy - materiály]]