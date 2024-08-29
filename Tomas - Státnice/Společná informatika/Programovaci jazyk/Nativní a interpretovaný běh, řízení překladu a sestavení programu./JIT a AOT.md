---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
![[Pasted image 20240828165526.png]]
#### Just-In-Time (JIT) Překlad
JIT kompilace překládá bytecode (IL) do nativního strojového kódu až při běhu aplikace. Když aplikace narazí na kód, který je potřeba vykonat, CLR přeloží IL do nativního kódu, který je poté spuštěn. Tento přístup umožňuje optimalizace během běhu aplikace.

**Výhody:**
- Optimalizace na základě běhového prostředí.
- Přenositelnost IL.

**Nevýhody:**
- Počáteční zpoždění při spuštění metody kvůli překladu.

#### Ahead-Of-Time (AOT) Překlad
AOT kompilace překládá bytecode (IL) do nativního kódu předem, ještě před spuštěním aplikace. Výsledkem je nativní binární soubor, který nevyžaduje JIT během běhu.

**Výhody:**
- Rychlejší start aplikace.
- Menší paměťová stopa, protože není potřeba JIT kompilátor.

**Nevýhody:**
- Méně runtime optimalizací.
- Závislost na specifických platformách.

### Shrnutí
- **JIT**: Překládá kód při běhu, umožňuje runtime optimalizace, ale zvyšuje počáteční zpoždění.
- **AOT**: Překládá kód předem, zlepšuje dobu spuštění, ale omezuje runtime optimalizace a flexibilitu.