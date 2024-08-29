---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Třídy (Classes)
Třída v C# je základní konstrukce pro vytváření objektů. Třídy obsahují metody, vlastnosti (properties), události (events), a datové položky (fields). Každá třída může být instancována jako objekt.

**Příklad:**
```csharp
public class Auto
{
    public string Barva { get; set; }
    public void Nastartovat()
    {
        Console.WriteLine("Auto je nastartováno.");
    }
}
```
V tomto příkladu třída `Auto` má vlastnost `Barva` a metodu `Nastartovat`.

#### Rozhraní (Interfaces)
Rozhraní definují smlouvu, kterou musí implementovat třídy nebo struktury. Rozhraní obsahují pouze signatury metod, vlastností, událostí nebo indexerů.

**Příklad:**
```csharp
public interface IAuto
{
    void Nastartovat();
}
public class OsobniAuto : IAuto
{
    public void Nastartovat()
    {
        Console.WriteLine("Osobní auto je nastartováno.");
    }
}
```
Třída `OsobniAuto` implementuje rozhraní `IAuto`, což znamená, že musí obsahovat metodu `Nastartovat`.

#### Metody (Methods)
Metody v C# jsou bloky kódu, které vykonávají určitou operaci. Metody mohou vracet hodnoty nebo být typu `void`, pokud nevrací nic.

**Příklad:**
```csharp
public void Zrychlit()
{
    Console.WriteLine("Auto zrychluje.");
}
```

#### Datové položky (Fields)
Fields jsou proměnné deklarované uvnitř třídy. Obvykle se používají k ukládání stavu nebo dat objektu.

**Příklad:**
```csharp
public class Auto
{
    private int rychlost;
}
```

#### Dědičnost (Inheritance)
Dědičnost umožňuje jedné třídě (potomkovi) převzít vlastnosti a metody jiné třídy (rodiče). V C# je dědičnost implementována pomocí klíčového slova `:`, což značí, že jedna třída dědí od jiné.

**Příklad:**
```csharp
public class OsobniAuto : Auto
{
    public void PouzitKlimatizaci()
    {
        Console.WriteLine("Klimatizace je zapnuta.");
    }
}
```
Třída `OsobniAuto` dědí vlastnosti a metody z třídy `Auto` a přidává vlastní metodu `PouzitKlimatizaci`.

#### Viditelnost (Visibility)
Viditelnost určuje, kdo má přístup k členům třídy. Hlavní modifikátory jsou `public`, `private`, `protected`, a `internal`.

**Příklad:**
```csharp
public class Auto
{
    private string VIN;
    protected string Barva { get; set; }
    public void Nastartovat()
    {
        Console.WriteLine("Auto je nastartováno.");
    }
}
```
- `VIN` je přístupné pouze uvnitř třídy `Auto`.
- `Barva` je přístupná uvnitř třídy `Auto` a jejích potomků.
- `Nastartovat` je přístupné z jakékoliv části kódu, která má přístup k objektu `Auto`.

Tyto konstrukty jsou základem pro vytváření objektově orientovaných programů v C#. Mohou být kombinovány a využívány k dosažení abstrakce, zapouzdření a polymorfismu.