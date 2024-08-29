---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Konstrukce pro obsluhu a propagaci výjimek v C#

Výjimky jsou mechanismem, který umožňuje řešení chyb během běhu programu. V C# můžete výjimky ošetřit (zachytit) a propagovat je výš pomocí následujících konstrukcí:

#### 1. **`try-catch` blok**
`try-catch` blok umožňuje zachytit výjimky, které nastanou během provádění kódu v bloku `try`.

**Příklad:**
```csharp
try
{
    // Kód, který může vyvolat výjimku
}
catch (Exception ex)
{
    // Kód, který se vykoná, pokud dojde k výjimce
    Console.WriteLine(ex.Message);
}
```

#### 2. **`finally` blok**
`finally` blok se vykoná bez ohledu na to, zda došlo k výjimce. Používá se pro uvolnění zdrojů nebo provedení úklidových prací.

**Příklad:**
```csharp
try
{
    // Kód, který může vyvolat výjimku
}
catch (Exception ex)
{
    Console.WriteLine(ex.Message);
}
finally
{
    // Kód, který se vždy vykoná
    Console.WriteLine("Uklízím zdroje...");
}
```

#### 3. **`throw`**
Konstrukce `throw` se používá k vyvolání výjimky. Můžete ji použít k znovu vyvolání chyby, která byla zachycena, nebo k vyvolání nové výjimky.

**Příklad:**
```csharp
try
{
    // Kód, který může vyvolat výjimku
}
catch (Exception ex)
{
    Console.WriteLine("Zachyceno: " + ex.Message);
    throw; // Propagace výjimky dále
}
```

#### 4. **Vlastní výjimky**
Vlastní výjimky umožňují vytvořit specializované výjimky pro konkrétní scénáře.

**Příklad:**
```csharp
public class MojeVlastniVyjimka : Exception
{
    public MojeVlastniVyjimka(string zprava) : base(zprava)
    {
    }
}

throw new MojeVlastniVyjimka("Nastala vlastní výjimka.");
```

### Shrnutí
- **`try-catch-finally`**: Konstrukce pro bezpečné zpracování chyb a uvolnění zdrojů.
- **`throw`**: Vyvolání a propagace výjimek.
- **Vlastní výjimky**: Pro tvorbu specifických chybových stavů v aplikaci.

