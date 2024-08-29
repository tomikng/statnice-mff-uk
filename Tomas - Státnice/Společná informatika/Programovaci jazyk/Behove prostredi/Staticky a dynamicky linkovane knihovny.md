---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Statické linkování v C\#

V C# je koncept statického linkování trochu odlišný od tradičních kompilovaných jazyků jako C nebo C++. V C# se většina referencí řeší při kompilaci a výsledný assembly obsahuje metadata o všech závislostech.

1. **Příklad použití statické třídy:**

```csharp
public static class MatematickeOperace
{
    public static int Scitani(int a, int b)
    {
        return a + b;
    }
}

class Program
{
    static void Main(string[] args)
    {
        int vysledek = MatematickeOperace.Scitani(5, 3);
        Console.WriteLine($"Výsledek: {vysledek}");
    }
}
```

V tomto případě je `MatematickeOperace` statická třída, která je "staticky linkována" do hlavního programu. Její kód bude součástí výsledného assembly.

2. **Vložení resource do assembly:**

```csharp
// Při kompilaci přidáme resource soubor
// csc /resource:MujResource.resx Program.cs

class Program
{
    static void Main(string[] args)
    {
        var rm = new System.Resources.ResourceManager("MujProjekt.MujResource", typeof(Program).Assembly);
        string text = rm.GetString("MujText");
        Console.WriteLine(text);
    }
}
```

Zde je resource soubor staticky linkován do assembly při kompilaci.

#### Dynamické linkování v C#

V C# se dynamické linkování často realizuje pomocí reflexe nebo dynamického načítání assembly.

1. **Dynamické načtení assembly a volání metody:**

```csharp
using System.Reflection;

class Program
{
    static void Main(string[] args)
    {
        // Dynamické načtení assembly
        Assembly assembly = Assembly.LoadFrom("MojeKnihovna.dll");

        // Získání typu z assembly
        Type typ = assembly.GetType("MojeKnihovna.MojeTrida");

        // Vytvoření instance
        object instance = Activator.CreateInstance(typ);

        // Volání metody
        MethodInfo metoda = typ.GetMethod("MojeMetoda");
        metoda.Invoke(instance, null);
    }
}
```

Tento příklad dynamicky načte assembly `MojeKnihovna.dll` a zavolá metodu `MojeMetoda` z třídy `MojeTrida`.

2. **Použití rozhraní pro pluginy:**

```csharp
// Definice rozhraní v hlavním programu
public interface IPlugin
{
    void Spustit();
}

class Program
{
    static void Main(string[] args)
    {
        string[] pluginSoubory = Directory.GetFiles("plugins", "*.dll");
        foreach (string soubor in pluginSoubory)
        {
            Assembly assembly = Assembly.LoadFrom(soubor);
            foreach (Type typ in assembly.GetTypes())
            {
                if (typeof(IPlugin).IsAssignableFrom(typ))
                {
                    IPlugin plugin = (IPlugin)Activator.CreateInstance(typ);
                    plugin.Spustit();
                }
            }
        }
    }
}

// V samostatném projektu (plugin):
public class MujPlugin : IPlugin
{
    public void Spustit()
    {
        Console.WriteLine("Plugin byl spuštěn!");
    }
}
```

Tento příklad demonstruje systém pluginů, kde hlavní program dynamicky načítá DLL soubory a hledá v nich třídy implementující rozhraní `IPlugin`.

Tyto příklady ukazují, jak C# pracuje s koncepty podobnými statickému a dynamickému linkování. Statické linkování v C# je většinou reprezentováno přímými referencemi na třídy a metody, zatímco dynamické linkování často využívá reflexi a dynamické načítání assembly.