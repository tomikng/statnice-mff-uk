---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---

#### Reference Typy
V C# [[Hodnotove a referencni typy#Referenční typy|referenční typy]], jako jsou třídy a pole, uchovávají odkazy na objekty uložené na haldě. Když dvě proměnné odkazují na stejný objekt, změny provedené prostřednictvím jedné proměnné ovlivní druhou, protože obě ukazují na stejný objekt v paměti.

**Příklad:**
```csharp
Osoba osoba1 = new Osoba();
Osoba osoba2 = osoba1; // oba odkazy ukazují na stejný objekt
osoba2.Jmeno = "Tomáš";
Console.WriteLine(osoba1.Jmeno); // Výstup: Tomáš
```

V tomto příkladu, když změníme `Jmeno` prostřednictvím `osoba2`, změní se i hodnota v `osoba1`, protože obě proměnné odkazují na stejný objekt.

#### Imutabilní Typy
Imutabilní typy jsou ty, které nelze po vytvoření změnit. Nejznámějším imutabilním typem v C# je `string`. Když změníte hodnotu stringu, ve skutečnosti se vytvoří nový objekt a starý zůstává nezměněn.

**Příklad:**
```csharp
string text = "Ahoj";
string novyText = text.ToUpper(); // vytváří nový string "AHOJ"
Console.WriteLine(text); // Výstup: Ahoj
```

Zde volání metody `ToUpper` nevytvoří změnu původního `text`, ale místo toho vrátí nový string.

#### Boxing a Unboxing
Boxing je proces převodu hodnotového typu (např. `int`) na referenční typ (`object`), což znamená, že se hodnotový typ zabalí do objektu, aby mohl být uložen na haldě. Unboxing je proces opačný, kde se zabalí objekt opět rozbalí zpět do hodnotového typu.

**Příklad:**
```csharp
int cislo = 42;
object box = cislo; // Boxing: zabalení hodnotového typu do objektu
int unbox = (int)box; // Unboxing: rozbalení zpět na hodnotový typ
```

Boxing a unboxing může mít vliv na výkon aplikace, protože přechod mezi zásobníkem (stack) a haldou (heap) může být časově náročný.

### Shrnutí:
- **Reference typy**: Ukládají odkaz na objekt, změny v jednom odkazu ovlivňují všechny odkazy na stejný objekt.
- **Imutabilní typy**: Nelze je změnit po vytvoření; změny vytvářejí nový objekt.
- **Boxing a Unboxing**: Převod mezi hodnotovými a referenčními typy; boxing může být nákladný z hlediska výkonu.

Pokud chcete pokračovat s dalším tématem, dejte vědět!