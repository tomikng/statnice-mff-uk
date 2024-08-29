---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
 #### 1. **Statická Alokace**
- **Co se děje v paměti**: Když deklarujete proměnnou nebo objekt jako `static`, jeho paměť je alokována v sekci paměti nazvané *statická oblast* (data segment). Tato paměť je alokována při startu programu a existuje po celou dobu běhu programu. Na konci programu je paměť uvolněna automaticky.
- **Životní cyklus**: Proměnné alokované staticky jsou inicializovány pouze jednou a zůstávají v paměti, dokud se program neukončí.

**Příklad:**
```csharp
static int globalniCislo = 10;
```
- Zde je `globalniCislo` uloženo v statické oblasti paměti a bude existovat po celou dobu běhu programu.

#### 2. **Alokace na Zásobníku (Stack Allocation)**
- **Co se děje v paměti**: Lokální proměnné a argumenty funkcí jsou uloženy na zásobníku. Zásobník je organizován jako LIFO (Last-In, First-Out), což znamená, že poslední proměnná, která byla uložena, je první, která se uvolní.
- **Životní cyklus**: Paměť pro proměnné alokované na zásobníku je automaticky uvolněna, jakmile metoda nebo blok kódu skončí. To činí zásobník velmi efektivním pro krátkodobé ukládání dat.

**Příklad:**
```csharp
void Metoda()
{
    int lokalniPromenna = 5; // alokováno na zásobníku
}
```
- `lokalniPromenna` je uložena na zásobníku a bude automaticky uvolněna po ukončení metody `Metoda`.

#### 3. **Alokace na Haldě (Heap Allocation)**
- **Co se děje v paměti**: Haldová paměť se používá pro dynamicky alokované objekty, které mají delší životnost než zásobníkové proměnné. Paměť na haldě je spravována *garbage collectorem* (GC), který sleduje objekty a uvolňuje paměť, když už není potřeba.
- **Životní cyklus**: Když vytvoříte nový objekt, paměť je alokována na haldě. GC pravidelně prochází haldu a uvolňuje paměť pro objekty, ke kterým již neexistují žádné reference.

**Příklad:**
```csharp
class Osoba
{
    public string Jmeno;
}

void Metoda()
{
    Osoba osoba = new Osoba(); // alokováno na haldě
}
```
- Objekt `osoba` je vytvořen na haldě. Jakmile už na něj neexistuje žádná reference, GC jej může uvolnit.

### Garbage Collector (GC) v C#
- **Generace**: GC pracuje v tzv. generacích (0, 1, 2), kde nově vytvořené objekty jsou v generaci 0. Pokud objekt přežije několik GC cyklů, přesune se do vyšší generace. Objekty v generaci 2 jsou považovány za dlouho žijící.
- **Optimalizace**: GC je optimalizován tak, aby většinu času pracoval s generací 0, protože většina objektů je krátkodobých a brzy se stane nepotřebnou.

### Shrnutí
- **Statická alokace**: Paměť je alokována při startu programu a uvolněna při jeho ukončení.
- **Zásobník**: Efektivní pro krátkodobé proměnné, automaticky spravovaný, rychlý přístup.
- **Halda**: Používá se pro dynamické objekty, spravována GC, vhodná pro dlouho žijící data.

Tento systém správy paměti zajišťuje, že C# programy jsou efektivní a bezpečné, minimalizující riziko úniků paměti a zajišťující správné uvolňování zdrojů.