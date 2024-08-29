---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
**Virtuální metody** v C# (a C++) umožňují přepsání metod v odvozených třídách, což podporuje dynamický polymorfismus. Když metoda je označena jako `virtual`, lze ji přepsat v podřízené třídě pomocí klíčového slova `override`. Při volání této metody na objektu, který je typu rodičovské třídy, ale obsahuje instanci podřízené třídy, se použije přepsaná verze.

**Nevirtuální metody** nelze přepsat a volají se vždy podle typu objektu, na kterém jsou volány, nikoli podle typu instance.

**Příklad:**

```csharp
public class Zviratko
{
    public virtual void Zvuk() // virtuální metoda
    {
        Console.WriteLine("Neznámý zvuk");
    }
}

public class Pes : Zviratko
{
    public override void Zvuk() // přepsání virtuální metody
    {
        Console.WriteLine("Haf Haf");
    }
}

public class Kocka : Zviratko
{
    public void Zvuk() // nevirtuální metoda
    {
        Console.WriteLine("Mňau");
    }
}

Zviratko mojeZvire = new Pes();
mojeZvire.Zvuk(); // Výstup: Haf Haf (použije se přepsaná metoda v Pes)

Zviratko mojeKocka = new Kocka();
mojeKocka.Zvuk(); // Výstup: Neznámý zvuk (použije se metoda z Zviratko, protože Zvuk v Kocka není virtuální)
```

- **Virtuální metody**: Umožňují přepsání v odvozených třídách.
- **Nevirtuální metody**: Jsou vázány na typ proměnné, nikoli instance.