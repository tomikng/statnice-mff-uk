---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Destruktory
Destruktory v C# jsou speciální metody, které jsou volány, když je objekt uvolněn z paměti. Destruktor je implementován pomocí symbolu tilda (`~`) a má stejný název jako třída. Destruktory se používají k uvolnění nepaměťových zdrojů, ale nejsou příliš často používány, protože .NET framework používá garbage collector (GC), který automaticky spravuje paměť.

**Příklad:**
```csharp
public class Osoba
{
    // Destruktor
    ~Osoba()
    {
        // Kód pro uvolnění zdrojů
        Console.WriteLine("Destruktor volán.");
    }
}
```
Destruktor není volán explicitně; je volán automaticky garbage collectorem před uvolněním paměti obsazené objektem.

#### Finalizátory
Finalizátory jsou obdobou destruktorů, ale jejich implementace je obvykle vázána na explicitní uvolňování prostředků, které nelze spravovat garbage collectorem. V C# se destruktory používají jako finalizátory, ale jejich použití je omezeno, protože finalizace může být nákladná z hlediska výkonu.

**Důležité body:**
- **Garbage Collector**: Automaticky spravuje paměť a volá destruktory při uvolňování objektů.
- **Nevýhody Destruktorů**: Destruktory mohou způsobit neefektivnost, protože GC musí provést další kroky k uvolnění objektu.

### Shrnutí
Destruktory a finalizátory v C# jsou metody pro správu uvolňování zdrojů a paměti. Jsou volány GC a používají se hlavně k uvolnění nepaměťových zdrojů, ale jejich použití je zřídka nutné díky automatizované správě paměti v .NET prostředí.