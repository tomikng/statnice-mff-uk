---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Dynamický polymorfismus
Dynamický polymorfismus v C# umožňuje volání metod objektu během běhu programu, a to i když je typ objektu určen až v době běhu (runtime). Je implementován pomocí virtuálních metod, abstraktních metod, a rozhraní.

**Příklad:**
```csharp
public class Zivocich
{
    public virtual void VydatZvuk()
    {
        Console.WriteLine("Neznámý zvuk");
    }
}

public class Pes : Zivocich
{
    public override void VydatZvuk()
    {
        Console.WriteLine("Haf Haf");
    }
}
```
V tomto příkladu metoda `VydatZvuk` je virtuální, což znamená, že může být přepsána v odvozené třídě `Pes`. Když voláme `VydatZvuk` na objektu typu `Zivocich`, ale přiřazeném k instanci `Pes`, runtime použije přepsanou verzi metody.

### Statically Typed Languages
Staticky typované jazyky jsou ty, kde je typ proměnné znám v době kompilace. To znamená, že programátor musí určit typ každé proměnné, nebo jazyk nabízí [[#^7e8187|typovou inferenci]], kde systém sám odvodí typ proměnné. Výhodou je, že mnoho chyb může být odhaleno již při kompilaci, což zvyšuje stabilitu a spolehlivost kódu.

>[!NOTE]
>**Typová inference** (nebo také odvození typu) je schopnost programovacího jazyka automaticky odvodit typ proměnné na základě hodnoty, která jí je přiřazena, bez nutnosti explicitního uvedení typu programátorem. To znamená, že kompilátor dokáže sám rozhodnout, jaký typ má proměnná být, aniž by to bylo přímo napsáno v kódu. ^7e8187
>
> > [!Example]-  **Příklad v C#:**
> >```csharp
> > var cislo = 10; // Kompilátor odvodí, že cislo je typu int
> >```
> >Zde `var` umožňuje kompilátoru odvodit, že `cislo` je typu `int` na základě přiřazené hodnoty.

**Příklad:** C, C++, Java, Rust, Go

### Dynamically Typed Languages
Dynamicky typované jazyky určují typy během běhu programu, ne v době kompilace. Programátoři mohou psát rychleji, protože nemusí specifikovat typy. Nevýhodou může být obtížnější ladění, protože chyby v typu se projeví až při běhu programu.

**Příklad:** Python, JavaScript, Ruby

