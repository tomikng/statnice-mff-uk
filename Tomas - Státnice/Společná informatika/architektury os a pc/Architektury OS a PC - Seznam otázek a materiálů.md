---
dg-publish: true
tags:
  - architektura_pc_a_os
  - spolecna_informatika
  - tomas
---
## Materiály
- [Poznámky z Principu počítačů od Tomáše Slámy](https://slama.dev/poznamky/principy-pocitacu/)
- [Počítačové systémy](https://cdn.tom-nguyen.dev/ps.pdf)
- [Playlist na YTB ohledně OS](https://www.youtube.com/playlist?list=PLBlnK6fEyqRiVhbXDGLXDk_OQAeuVcp2O)
	- Užitečné poznámky a vysvětlení základních pojmů (interrupt) a základní chápání OS 
	
Podle mě je to složené tak 80 % **pc systémy** a 20 % **Principy PC**
## Otázky

> [!info]
> Jsou jen odkazy na části, o kterých jsem nevěděl moc dopodrobna. (Naštěstí je toho dost :D)
> Struktura byla převzata od [Tomáše Slámy](https://www.slama.dev) a přizpůsobeno na 2023/2024.

- Základní architektura počítače. [🔗](https://slama.dev/poznamky-z-prednasky/principy-pocitacu/#zjednodu%C5%A1en%C3%A9-sch%C3%A9ma-po%C4%8D%C3%ADta%C4%8De) [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=24)
	- reprezentace a přístup k datům v paměti, adresa, adresový prostor [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=57)
    - ukládání jednoduchých a složených datových typů [🔗](https://cdn.tom-nguyen.dev/Architektura%20poc%CC%8Ci%CC%81tac%CC%8Cu%CC%8A%20a%20operac%CC%8Cni%CC%81ch%20syste%CC%81mu%CC%8A.pdf#page=2)
	    - Float [🔗](https://www.geeksforgeeks.org/ieee-standard-754-floating-point-numbers/)
    - základní aritmetické a logické operace
- Instrukční sada, vazba na vyšší programovací jazyky. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=29)
- Podpora pro běh operačního systému. [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=97)
	- privilegovaný a neprivilegovaný režim procesoru
    - jádro operačního systému
-  [[Rozhraní periferních zařízení a jejich obsluha]] [🔗](https://slama.dev/poznamky-z-prednasky/principy-pocitacu/#otro%C4%8Dina) [🔗](https://cdn.tom-nguyen.dev/ps.pdf#page=105)
	- Popsat roli řadiče zařízení při programem řízené obsluze zařízení (PIO), pro zadané adresy a funkce vstupních a výstupních portů implementovat programem řízenou obsluhu zadaného zařízení (myš, disk)
    - Popsat roli přerušení při programem řízené obsluze zařízení (PIO), na úrovni vykonávání instrukcí popsat reakci procesoru (hardware) a operačního systému (software) na žádost o přerušení
- Základní abstrakce, rozhraní a mechanizmy OS pro běh programů, sdílení prostředků a vstup/výstup. [🔗](https://cunicz.sharepoint.com/:p:/s/NSWI170PCSystems/EcegExT3UclFiszQ0PLqWM4B26DDW76aqwy4UKHSlVGNkw?e=qMnjTx)
	- neprivilegované (uživatelské) procesy
    - sdílení procesoru
	    - procesy, vlákna, [[Kontext vlákna a procesů]]
        - [[Přepínání kontextu]], [[Kooperativní vs. Preemptivní Multitasking]]
        - [[Plánování procesů a vláken]]
    - sdílení paměti [📹](https://www.youtube.com/watch?v=A9WLYbE0p-I&t=450s)
	    - Vysvětlit rozdíl mezi [[Virtuální vs Fyzická paměť]] a [[Identifikace Virtuální vs Fyzické paměti|identifikovat, zda se v zadaném kontextu či fragmentu kódu používá virtuální nebo fyzická adresa]]
        - [[Identifikace a význam komponent virtuální a fyzické adresy|Na zadaném příkladu identifikovat a vysvětlit význam komponent virtuální a fyzické adresy (číslo stránky, číslo rámce, offset)]]
        - [[Překlad adres|Pro konkrétní adresy a obsah jednoúrovňové stránkovací tabulky řešit úlohy překladu adres]]
        - Vysvětlit roli virtuálních adresových prostorů v ochraně paměti procesů a vláken
    - [[Sdílení úložného prostroru]]
	    - soubory, analogie s adresovým prostorem
        - abstrakce a rozhraní pro práci se soubory
- [[Paralelní programování a synchronizace|Paralelismus, vlákna a rozhraní pro jejich správu, synchronizace vláken.]]
	- časově závislé chyby (race conditions)
    - kritická sekce, vzájemné vyloučení
    - základní sychronizační primitiva, jejich rozhraní a použití
	    - zámky
        - aktivní a pasivní čekání