---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Lambda Funkce
Lambda funkce jsou anonymní metody, které mohou být použity k vytvoření krátkých funkcí nebo výrazu bez nutnosti vytvářet samostatnou pojmenovanou metodu. Lambda výrazy se obvykle používají s delegáty, akcemi nebo funkcionálními rozhraními.

**Syntaxe:**
```csharp
(parametry) => výraz;
```

**Příklad:**
```csharp
Func<int, int, int> secti = (a, b) => a + b;
Console.WriteLine(secti(3, 4)); // Výstup: 7
```

Lambda výrazy mohou být použity jako zjednodušený zápis pro krátké funkce, často ve spojení s LINQ dotazy nebo při předávání metod jako parametrů.

#### Funkcionální Rozhraní
Funkcionální rozhraní jsou rozhraní, která mají jednu abstraktní metodu. Lambda výrazy mohou být přiřazeny těmto rozhraním, což umožňuje jednoduše implementovat chování bez nutnosti vytvářet konkrétní třídy.

**Příklad s vlastní funkcionálním rozhraním:**
```csharp
public interface IOperace
{
    int Proved(int a, int b);
}

public class Program
{
    public static void Main()
    {
        IOperace secti = (a, b) => a + b;
        Console.WriteLine(secti.Proved(3, 4)); // Výstup: 7
    }
}
```

Tento příklad ukazuje, jak můžete použít lambda funkci k implementaci funkcionálního rozhraní bez potřeby vytvářet další třídu.

### Použití Lambda Funkcí a Funkcionálních Rozhraní
Lambda funkce a funkcionální rozhraní jsou klíčové v moderním C# pro zjednodušení kódu, zejména při použití LINQ, přiřazení funkcí delegátům, a při implementaci rozhraní, kde je potřeba rychle definovat malé chování. Tyto nástroje zlepšují čitelnost a zkracují zápis kódu, což vede k efektivnějšímu vývoji softwaru.