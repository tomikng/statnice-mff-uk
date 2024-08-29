---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Typy Reprezentující Funkce v C# – Detailní Přehled

V C# existují tři hlavní typy, které umožňují práci s funkcemi jako s objekty: **delegáti (delegates)**, **akce (Action)**, a **funkce (Func)**. Tyto typy jsou klíčové pro implementaci callbacků, událostí, a funkcionálního programování v C#. Podívejme se na každý z nich podrobněji:

#### 1. **Delegáti (Delegates)**
Delegáti jsou datové typy, které obsahují odkazy na metody. Jsou silně typované, což znamená, že delegát může odkazovat pouze na metody, které odpovídají jeho signatuře. Delegáti jsou základem pro události a callback metody v C#.

**Příklad:**
```csharp
public delegate void MojeFunkce(int cislo);

public class Program
{
    public static void Vypis(int cislo)
    {
        Console.WriteLine(cislo);
    }

    public static void Main()
    {
        MojeFunkce mojeFunkce = Vypis;
        mojeFunkce(42); // Výstup: 42
    }
}
```
V tomto příkladu delegát `MojeFunkce` odkazuje na metodu `Vypis`, která přijímá celé číslo a nic nevrací.

**Pokrocily Priklad**
```csharp
public delegate void ZpravaHandler(string zprava);

public class Operace
{
    public void ProvedOperaci(ZpravaHandler callback)
    {
        // Provedení nějaké operace
        string vysledek = "Operace dokončena";
        
        // Volání callbacku s výsledkem operace
        callback(vysledek);
    }
}

public class Program
{
    public static void Main()
    {
        Operace operace = new Operace();
        
        // Callback metoda
        void ZpracujZpravu(string zprava)
        {
            Console.WriteLine("Zpráva: " + zprava);
        }
        
        // Volání metody s callbackem
        operace.ProvedOperaci(ZpracujZpravu);
    }
}

```

#### 2. **Akce (Action)**
`Action` je vestavěný delegát, který umožňuje reprezentovat metody bez návratové hodnoty. `Action` může mít 0 až 16 parametrů. Používá se tam, kde potřebujete předat metodu jako parametr, ale nevyžadujete návratovou hodnotu.

**Příklad:**
```csharp
Action<int, int> secti = (a, b) => Console.WriteLine(a + b);
secti(3, 4); // Výstup: 7
```
Tady `Action<int, int>` představuje metodu, která přijímá dvě celá čísla a nevrací žádnou hodnotu.

#### 3. **Funkce (Func)**
`Func` je dalším vestavěným delegátem, který představuje metody s návratovou hodnotou. `Func` může mít 0 až 16 vstupních parametrů, přičemž poslední typový parametr je návratový typ.

**Příklad:**
```csharp
Func<int, int, int> secti = (a, b) => a + b;
int vysledek = secti(3, 4); // Výstup: 7
Console.WriteLine(vysledek);
```
V tomto příkladu `Func<int, int, int>` představuje metodu, která přijímá dvě celá čísla a vrací celé číslo.

### Použití v praxi
- **Delegáti**: Používají se pro callbacky a při definování vlastních událostí.
- **Action**: Používá se, když potřebujete vykonat metodu, která nic nevrací, např. při zpracování kolekcí.
- **Func**: Používá se, když potřebujete vykonat metodu, která vrací hodnotu, např. při výpočtech nebo filtrování kolekcí.

Tyto koncepty jsou důležité pro vytváření flexibilního, znovupoužitelného a typově bezpečného kódu v C#.