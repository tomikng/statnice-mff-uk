---
dg-publish: true
tags:
  - tomas
  - architektura_pc_a_os
  - spolecna_informatika
---
Více o stránkování [[Stránkování|zde]].

> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT
### **Řešení Úloh Překladu Adres**

Pojďme si ukázat konkrétní příklad překladu adres pomocí jednoúrovňové stránkovací tabulky.

**Příklad:**

Předpokládejme, že máme 32bitovou virtuální adresu a 1 úroveň stránkovací tabulky s následujícím nastavením:
- Velikost stránky: 4KB (tedy 12 bitů pro offset)
- Velikost paměti: 64KB (16 rámců po 4KB)
- Číslo stránky: 20 bitů (protože 32 bitů - 12 bitů pro offset = 20 bitů pro číslo stránky)

Stránkovací tabulka je následující:

| Číslo Stránky | Číslo Rámce |
|---------------|-------------|
| 0             | 3           |
| 1             | 7           |
| 2             | 5           |
| 3             | 2           |

**Příklad Virtuální Adresy:**
Virtuální adresa: `0x00032005`

1. **Rozklad Virtuální Adresy**:
   - Číslo stránky: `0x00032` (v binární soustavě `0000 0000 0011 0010`) -> 50 (v desetinné soustavě)
   - Offset: `0x005` (v binární soustavě `0000 0000 0000 0101`) -> 5 (v desetinné soustavě)

2. **Překlad Pomocí Stránkovací Tabulky**:
   - Číslo stránky `50` je mapováno na fyzický rámec `3`.

3. **Výpočet Fyzické Adresy**:
   - Fyzická adresa je základní adresa rámce `3` + offset `5`.
   - Pokud je rámec 3 na adrese `0x3000`, pak fyzická adresa je `0x3000 + 0x5 = 0x3005`.

Tímto způsobem můžete pomocí jednoúrovňové stránkovací tabulky přeložit virtuální adresy na fyzické.