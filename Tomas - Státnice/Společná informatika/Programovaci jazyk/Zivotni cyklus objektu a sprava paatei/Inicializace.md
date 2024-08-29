---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
#### Konstruktory
Konstruktory jsou speciální metody, které se volají při vytváření instance třídy (objektu). Konstruktory slouží k inicializaci objektu, nastavení počátečních hodnot jeho vlastností a mohou provádět další potřebné operace.

**Příklad:**
```csharp
public class Osoba
{
    public string Jmeno;

    // Konstruktor
    public Osoba(string jmeno)
    {
        Jmeno = jmeno;
    }
}

Osoba osoba = new Osoba("Tomáš");
```
V tomto příkladu je konstruktor `Osoba` volán s parametrem `jmeno`, který inicializuje vlastnost `Jmeno`.

#### Výchozí Konstruktory
Pokud třída nemá definovaný žádný konstruktor, kompilátor automaticky vytvoří výchozí konstruktor bez parametrů. Tento konstruktor nastaví všechny vlastnosti na jejich výchozí hodnoty (např. `null` pro referenční typy, `0` pro číselné typy atd.).

**Příklad:**
```csharp
public class Pes
{
    public string Jmeno;
}

// Výchozí konstruktor bude automaticky vytvořen
Pes pes = new Pes(); // Jmeno bude null
```

#### Zděděné Konstruktory
Při dědičnosti třídy v C# je možné volat konstruktor základní třídy pomocí klíčového slova `base`. Konstruktory podřízené třídy mohou být navrženy tak, aby volaly specifické konstruktory základní třídy a přidávaly další inicializační logiku.

**Příklad:**
```csharp
public class Zivocich
{
    public string Typ;

    // Konstruktor základní třídy
    public Zivocich(string typ)
    {
        Typ = typ;
    }
}

public class Pes : Zivocich
{
    public string Jmeno;

    // Konstruktor podřízené třídy, který volá konstruktor základní třídy
    public Pes(string typ, string jmeno) : base(typ)
    {
        Jmeno = jmeno;
    }
}
```
V tomto příkladu třída `Pes` dědí od třídy `Zivocich` a její konstruktor volá konstruktor základní třídy pomocí `base(typ)`.

#### Konstrukční řetězení
Třídy mohou mít více konstruktorů, které mohou volat jeden druhý pomocí klíčového slova `this`. To umožňuje zjednodušit inicializační logiku, když různé konstruktory sdílejí společné kroky.

**Příklad:**
```csharp
public class Auto
{
    public string Barva;
    public string Model;

    public Auto(string model) : this(model, "Neznámá barva") { }

    public Auto(string model, string barva)
    {
        Model = model;
        Barva = barva;
    }
}

Auto auto = new Auto("Škoda"); // Volá se konstruktor s jedním parametrem, který následně volá druhý konstruktor
```

### Shrnutí
- **Konstruktory** jsou speciální metody pro inicializaci objektů.
- **Výchozí konstruktor** je automaticky generován, pokud není explicitně definován.
- **Volání zděděných konstruktorů** pomocí `base` umožňuje podřízené třídě volat konstruktor základní třídy.
- **Konstrukční řetězení** umožňuje volání jednoho konstruktoru z jiného, což zjednodušuje inicializační logiku.

