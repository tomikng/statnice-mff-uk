---
tags:
  - tomas
  - architektura_pc_a_os
  - spolecna_informatika
dg-publish: true
---
Podrobněji [[Virtuální vs Fyzická paměť]].

> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

V tomto příkladu si podrobně vysvětlíme, jak se skládá virtuální adresa a jak je přeložena na fyzickou adresu pomocí čísla stránky, čísla rámce a offsetu.
#### **Příklad:**

Předpokládejme, že máme následující systém:
- **Velikost stránky**: 4KB (4096 bajtů).
- **Virtuální adresní prostor**: 32bitový (4 GB).
- **Fyzická paměť**: 64KB, což odpovídá 16 rámcům (každý rámec má velikost 4KB).

#### **Virtuální Adresa**

Virtuální adresa je rozdělena do dvou hlavních částí:
1. **Číslo stránky**: Identifikuje specifickou stránku ve virtuální paměti.
2. **Offset**: Udává konkrétní pozici (offset) v rámci této stránky.
![[Pasted image 20240816171247.png]]

##### **Příklad Virtuální Adresy:**
Virtuální adresa: `0x00032005` (v šestnáctkové soustavě)

- **Číslo stránky**: Virtuální adresa má 32 bitů. Protože velikost stránky je 4KB, což odpovídá 12 bitům (2^12 = 4096), číslo stránky je reprezentováno zbývajícími 20 bity. V našem příkladu je tedy číslo stránky `0x00032` (v binární podobě `0000 0000 0011 0010`).
  
- **Offset**: Offset je spodních 12 bitů adresy, což v našem příkladu odpovídá `0x005` (v binární podobě `0000 0000 0000 0101`).

#### **Stránkovací Tabulka a Fyzická Adresa**

Stránkovací tabulka mapuje číslo stránky na číslo rámce ve fyzické paměti. Fyzická adresa se skládá z:
1. **Čísla rámce**: Určuje, který rámec ve fyzické paměti obsahuje danou stránku.
2. **Offsetu**: Stejný jako u virtuální adresy, určuje konkrétní pozici v rámci rámce.

##### **Příklad Stránkovací Tabulky:**

| Číslo Stránky | Číslo Rámce |
|---------------|-------------|
| 0x00032       | 3           |

##### **Překlad na Fyzickou Adresu:**

- **Číslo Rámce**: Stránka `0x00032` je mapována na rámec `3`.
- **Výpočet Fyzické Adresy**: Fyzická adresa se vypočítá jako základní adresa rámce `3` plus offset z virtuální adresy.

Předpokládejme, že rámec `3` je umístěn na adrese `0x3000` ve fyzické paměti.

- **Fyzická Adresa**: `0x3000 + 0x005 = 0x3005`.

### **Význam Komponent:**

1. **Číslo Stránky (Virtuální Adresa)**:
   - **Úloha**: Identifikuje konkrétní stránku ve virtuálním adresním prostoru procesu. Je klíčové pro přístup k správné části dat procesu.
   - **Příklad**: Číslo stránky `0x00032` identifikuje 50. stránku ve virtuální paměti.

2. **Číslo Rámce (Fyzická Adresa)**:
   - **Úloha**: Určuje, do kterého rámce ve fyzické paměti je stránka mapována. Toto číslo umožňuje operačnímu systému efektivně využívat fyzickou paměť.
   - **Příklad**: Rámec `3` ve fyzické paměti obsahuje stránku s číslem `0x00032` z virtuální paměti.

3. **Offset**:
   - **Úloha**: Offset udává přesnou pozici uvnitř stránky (nebo rámce), kde se nacházejí požadovaná data. Je použit jak u virtuální, tak u fyzické adresy, což umožňuje rychlý a přesný přístup k datům.
   - **Příklad**: Offset `0x005` určuje konkrétní byte uvnitř rámce `3`, což odpovídá fyzické adrese `0x3005`.

Tímto způsobem virtuální adresa využívá číslo stránky a offset k identifikaci dat v paměti, zatímco stránkovací tabulka překládá virtuální číslo stránky na fyzické číslo rámce, kde jsou data skutečně uložena v RAM.