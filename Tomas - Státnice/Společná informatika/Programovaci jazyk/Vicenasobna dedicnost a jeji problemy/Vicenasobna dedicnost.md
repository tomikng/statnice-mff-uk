---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Vícenásobná dědičnost a její problémy (Detailní příklad)

**Vícenásobná dědičnost** umožňuje třídě dědit od více než jedné základní třídy, což může vést ke komplikacím, jako je **diamantový problém**. Tento problém nastává, když dvě základní třídy mají stejnou metodu a odvozená třída neví, kterou verzi metody použít.
![[Pasted image 20240828114520.png]]
#### Příklad:

Představte si, že máte dvě základní třídy `TřídaA` a `TřídaB`, obě mají metodu `Zobrazit`. Třída `TřídaC` dědí od obou:

```csharp
public class TřídaA
{
    public void Zobrazit()
    {
        Console.WriteLine("Z Třídy A");
    }
}

public class TřídaB
{
    public void Zobrazit()
    {
        Console.WriteLine("Z Třídy B");
    }
}

// C# nepodporuje následující konstrukci přímo, protože by došlo ke konfliktu:
public class TřídaC : TřídaA, TřídaB
{
    // Kterou metodu Zobrazit použít?
}
```

V C# není vícenásobná dědičnost povolena, protože by C# kompilátor nevěděl, kterou metodu `Zobrazit` by měl `TřídaC` použít. Tento problém je řešen používáním **rozhraní (interfaces)**, kde odvozená třída implementuje konkrétní metody a rozhoduje, jakou logiku použít.

#### Řešení v C# pomocí rozhraní:
```csharp
public interface ITřídaA
{
    void Zobrazit();
}

public interface ITřídaB
{
    void Zobrazit();
}

public class TřídaC : ITřídaA, ITřídaB
{
    void ITřídaA.Zobrazit()
    {
        Console.WriteLine("Z Třídy A");
    }

    void ITřídaB.Zobrazit()
    {
        Console.WriteLine("Z Třídy B");
    }
}
```
V tomto příkladu třída `TřídaC` explicitně implementuje metody obou rozhraní a rozhoduje, kterou verzi metody `Zobrazit` použít v daném kontextu.

Pokud chcete pokračovat s dalším tématem, dejte vědět!