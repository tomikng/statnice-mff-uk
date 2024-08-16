---
tags:
  - architektura_pc_a_os
  - tomas
  - spolecna_informatika
dg-publish: true
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

**Multitasking** v operačních systémech označuje schopnost systému provádět více úloh nebo procesů současně. Existují dva hlavní typy multitaskingu: **kooperativní multitasking** a **preemptivní multitasking**. Každý z těchto přístupů má svůj vlastní způsob, jak spravovat sdílení času procesoru mezi procesy. ^fd5c7f

> [!faq]- Jak se docílí multitaskingu pokud máme pouze 1 CPU? 
> CPU mění rychle jaké procesy bude vykonávat -> nikdy není v IDLE stavu. Dělá to tak rychle a často, že nám to dává iluzi, že to běží všechno současně
> > [!example] Máme VSCode, posloucháme při tom hudbu a zároveň nám běží v pozadí hra.

#### 1. **Kooperativní Multitasking**

**Kooperativní multitasking** spoléhá na to, že každý proces dobrovolně uvolní řízení procesoru, aby umožnil běh dalších procesů. To znamená, že proces musí pravidelně kontrolovat, zda by neměl uvolnit CPU, a následně explicitně zavolat systémovou funkci k předání řízení.

- **Jak to funguje**: V kooperativním multitaskingu rozhoduje běžící proces o tom, kdy předá řízení. Typicky to procesy dělají v určitých bodech, například po dokončení určité úlohy nebo když čekají na operace I/O.

- **Výhody**:
  - **Jednoduchost**: Operační systém nemusí aktivně řídit přepínání úloh, což snižuje složitost.
  - **Efektivita v dobře navržených systémech**: Pokud všechny procesy uvolňují CPU správně, může být kooperativní multitasking efektivní.

- **Nevýhody**:
  - **Riziko monopolizace procesorem**: Pokud proces neuvolní řízení (kvůli chybě nebo záměru), může monopolizovat CPU a způsobit, že systém přestane reagovat.
  - **Menší kontrola**: Operační systém má menší kontrolu nad plánováním úloh, spoléhá na "dobré chování" procesů.

- **Příklad**: Starší verze Mac OS (před Mac OS X) a Windows 3.x používaly kooperativní multitasking.

#### 2. **Preemptivní Multitasking**

**Preemptivní multitasking** je modernější a robustnější přístup, kde má operační systém plnou kontrolu nad CPU a může násilně přerušit běžící proces, aby přešel na jiný.

- **Jak to funguje**: Operační systém používá časovač k pravidelnému hodnocení, zda by měl aktuálně běžící proces být pozastaven. Pokud operační systém rozhodne, že jiný proces by měl běžet, může přerušit aktuální proces, uložit jeho stav a přepnout na jiný.

- **Výhody**:
  - **Větší kontrola**: Operační systém má větší kontrolu nad tím, který proces běží a kdy, což zlepšuje celkovou stabilitu systému.
  - **Ochrana proti monopolizaci**: Žádný proces nemůže monopolizovat CPU, protože operační systém může kdykoli přerušit jakýkoli proces.

- **Nevýhody**:
  - **Složitost**: Preemptivní multitasking vyžaduje složitější správu ze strany operačního systému, což může zvýšit náročnost na vývoj a údržbu.

- **Příklad**: Většina moderních operačních systémů, jako jsou Windows NT/XP a novější, Linux a macOS (od verze X), používá preemptivní multitasking.

### Příklady z praxe

- **Kooperativní multitasking**: Představte si starší verzi systému Windows 3.x, kde aplikace jako textový editor musí manuálně uvolnit procesor, aby mohl běžet jiný program, například kalkulačka. Pokud textový editor neuvolní procesor (např. zamrzne), kalkulačka se nespustí a systém může přestat reagovat.

- **Preemptivní multitasking**: Na moderním systému jako je Windows 10, pokud jedna aplikace, třeba internetový prohlížeč, zamrzne, operační systém ji automaticky přeruší a přepne se na jiný proces, například na emailového klienta, aniž by uživatel musel zasahovat.