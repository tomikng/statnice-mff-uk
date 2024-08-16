---
tags:
  - architektura_pc_a_os
  - tomas
  - spolecna_informatika
dg-publish: true
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

### Příklady Použití Virtuální a Fyzické Adresy v Kódu

Rozlišení mezi použitím virtuálních a fyzických adres v kódu závisí na tom, jakým způsobem operační systém a hardware spravují paměť a jakým způsobem program přistupuje k datům. Níže uvedu několik příkladů kódu a vysvětlím, zda používají virtuální nebo fyzickou adresu.

#### Příklad 1: Jednoduchý Program v C

```c
#include <stdio.h>

int main() {
    int a = 10;
    int *p = &a;
    
    printf("Hodnota a: %d\n", a);
    printf("Adresa proměnné a: %p\n", p);
    
    return 0;
}
```

**Vysvětlení**:

- **Virtuální adresa**: Když tento program přistupuje k proměnné `a`, používá virtuální adresu. Operace `&a` získá adresu proměnné `a`, ale tato adresa je ve skutečnosti virtuální adresa v rámci virtuálního adresního prostoru procesu.
- **Proč virtuální?** Všechny adresy, se kterými program pracuje, jsou virtuální, protože procesor a operační systém používají systém virtuální paměti, aby zajistily izolaci a ochranu paměti. Při překladu virtuální adresy na fyzickou se stará operační systém pomocí MMU (Memory Management Unit).

V tomto kontextu program nikdy nepracuje přímo s fyzickými adresami. Adresa, kterou program zobrazí pomocí `%p` v `printf`, je virtuální adresa.

#### Příklad 2: Přístup na Úroveň Jádra (Kernel)

V operačních systémech, kde je třeba pracovat s fyzickými adresami (např. při vývoji ovladačů nebo v jádře systému), může být kód koncipován tak, aby získal přístup k fyzickým adresám. Příkladem je kód, který přistupuje k fyzické paměti přímo, což se běžně provádí v režimu jádra.

```c
void *phys_to_virt(unsigned long phys_addr) {
    // Převádí fyzickou adresu na virtuální adresu v rámci jádra
    return (void *)(phys_addr + PAGE_OFFSET);
}
```

**Vysvětlení**:

- **Fyzická adresa**: V tomto příkladu je `phys_addr` fyzická adresa v paměti RAM. Kód v jádře (kernel mode) může získat fyzickou adresu například při práci s hardwarovými zařízeními nebo při správě paměti.
- **Virtuální adresa**: Funkce `phys_to_virt` převádí fyzickou adresu na odpovídající virtuální adresu, kterou lze použít v jádře. Tento postup se používá, protože i jádro obvykle pracuje s virtuálními adresami, aby využívalo výhody virtuální paměti (např. ochrana paměti, stránkování).

V tomto kontextu kód pracuje s oběma typy adres: vstupem je fyzická adresa a výstupem je virtuální adresa.

#### Příklad 3: Přístup k Paměti ve Vestavěném Systému

Ve vestavěných systémech (embedded systems), kde se často nepoužívá složitý operační systém s virtuální pamětí, může kód přímo pracovat s fyzickými adresami.

```c
#define GPIO_BASE 0x40021000

void set_gpio() {
    volatile unsigned int *gpio_addr = (unsigned int *)GPIO_BASE;
    *gpio_addr = 0x1;  // Nastavení GPIO registru
}
```

**Vysvětlení**:

- **Fyzická adresa**: `GPIO_BASE` je přímo fyzická adresa konkrétního hardwarového registru (např. GPIO kontroler). V tomto příkladu program přímo přistupuje k paměti zařízení, což je typické pro vestavěné systémy, kde neexistuje virtuální paměť.
- **Proč fyzická?**: Vestavěné systémy často neimplementují složitou správu paměti, a proto adresy používané v kódu přímo odpovídají fyzickým adresám v paměti zařízení.

V tomto případě je adresa `GPIO_BASE` skutečná fyzická adresa, kterou procesor použije k přímému přístupu k hardwarovému registru.

### Shrnutí

- **Virtuální adresy** jsou používány ve většině aplikací běžících v uživatelském prostoru na moderních operačních systémech, jako jsou Windows, Linux, nebo macOS. Programátoři pracují s virtuálními adresami, které jsou následně překládány na fyzické adresy procesorem a operačním systémem.
  
- **Fyzické adresy** se používají především v režimu jádra (kernel mode), při vývoji ovladačů nebo v nízkoúrovňovém programování, kde je třeba přistupovat přímo k hardwaru. Fyzické adresy jsou také běžné ve vestavěných systémech, kde není implementována virtuální paměť.

Tímto způsobem se virtuální a fyzické adresy liší podle kontextu a typu aplikace, kterou programujete.