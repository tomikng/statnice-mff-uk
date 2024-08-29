---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Životní cyklus objektů a správa paměti v C# – Detailní Přehled

#### 1. **Explicitní uvolňování objektů**
V C# není explicitní uvolňování paměti běžné, protože .NET framework obsahuje garbage collector (GC), který automaticky spravuje paměť. Nicméně, uvolnění zdrojů jako souborů nebo databázových připojení může být provedeno ručně pomocí metody `Dispose`, implementované z rozhraní `IDisposable`.

**Příklad:**
```csharp
using (var soubor = new StreamWriter("soubor.txt"))
{
    soubor.WriteLine("Nějaký text");
} // soubor.Dispose() je automaticky volán
```
Zde [[|`using`]] zajistí, že `Dispose` bude zavolán i při výskytu výjimky.

#### 2. **Reference Counting**
C# nepoužívá explicitní reference counting pro správu paměti, jak to dělají jazyky jako C++. Místo toho se spoléhá na garbage collector. Nicméně, reference counting může být konceptuálně pochopeno jako sledování počtu odkazů na objekt. Když žádná reference na objekt neexistuje, objekt je považován za způsobilý pro uvolnění.

#### 3. **Garbage Collector (GC)**
[📹](https://www.youtube.com/watch?v=c32zXYAK7CI)
Garbage Collector v C# spravuje paměť a zajišťuje, že objekty, které již nejsou potřebné, jsou automaticky uvolněny. GC je **generational** (generativní), což znamená, že objekty jsou tříděny do generací:

- **Generace 0**: Objekty právě alokované. Tyto objekty jsou první, které GC zkontroluje, když potřebuje uvolnit paměť.
- **Generace 1**: Objekty, které přežily alespoň jednu garbage kolekci.
- **Generace 2**: Objekty, které přežily více garbage kolekcí. Tato generace se čistí nejméně často.

#### Implementace a Detailní Správa Paměti

##### **Heaps a Garbage Collection**
V .NETu existují dva hlavní heapy:
1. **Small Object Heap (SOH)**: Pro malé objekty (méně než 85 000 B). Po každé garbage kolekci dochází ke kompaktování, což znamená, že přeživší objekty jsou přesunuty blíže k začátku heapu, aby se uvolnilo místo pro nové objekty.
2. **Large Object Heap (LOH)**: Pro velké objekty (větší než 85 000 B). Na tomto heapu se neprovádí kompaktování, což může vést k fragmentaci paměti.

**Fragmentace paměti** může nastat, když jsou v heapu "díry", kde se již neuvolněné objekty nevejdou. To může způsobit vyvolání `OutOfMemoryException`, i když je celkově dostatek paměti.

**Generační správa**:
- GC kontroluje generace a uvolňuje paměť postupně. Pokud generace 0 neuvolní dostatek paměti, pokračuje ke generaci 1, a pokud ani to nepomůže, pokračuje ke generaci 2.

**Velikost segmentů**:
- **Ephemeral segment**: Nejnovější segment, ve kterém probíhá GC. Když je plný, přidá se nový segment, a starý se přesune do generace 2.
- Velikost segmentů a kvant (např. 16 MB pro segmenty) může výrazně ovlivnit výkon a správu paměti.

#### **GC Class v C#**
Třída `GC` poskytuje metody pro interakci s garbage collectorem, například:
- `GC.Collect()`: Nutí GC provést kolekci. Použití této metody by mělo být poslední možností, protože GC je obvykle velmi efektivní při správě paměti.
- `GC.GetGeneration(objekt)`: Zjistí, v jaké generaci se objekt nachází.
- `GC.GetTotalMemory(false)`: Získá odhad množství paměti používané managed objekty.

#### **Problémy s Garbage Collection**
Navzdory efektivnímu GC mohou stále nastat problémy s únikem paměti, například když objekty zůstávají v paměti kvůli přihlášení k událostem nebo když anonymní metody obsahují odkazy na objekty, které nelze uvolnit.

### Shrnutí
- **Garbage Collector** je automatický správce paměti v C#, který minimalizuje potřebu manuálního uvolňování paměti.
- **Heaps**: Small Object Heap pro malé objekty, Large Object Heap pro velké objekty, každý má různé strategie správy paměti.
- **Fragmentace**: Může způsobit problémy s pamětí, zejména na LOH.
- **GC generace**: Efektivní správa paměti s tříděním objektů podle stáří.
- **Explicitní uvolňování** pomocí `Dispose` a `using` zajišťuje správné uvolnění nepaměťových zdrojů.