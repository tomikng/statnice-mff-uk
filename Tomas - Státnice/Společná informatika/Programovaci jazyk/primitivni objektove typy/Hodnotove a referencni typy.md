---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
![[Pasted image 20240828135139.png]]

![[Pasted image 20240828135316.png]]
#### Hodnotové typy
Hodnotové typy v C# ukládají přímo data a jsou uloženy na zásobníku (stack). Mezi nejčastější hodnotové typy patří **čísla** (`int`, `double`, `float`, `decimal`) a **výčtové typy** (`enum`), které reprezentují pevně danou sadu konstant. Hodnotové typy jsou rychlé, protože práce se zásobníkem je obecně velmi efektivní.

**Příklad:**
```csharp
int cislo = 42;
enum Barva { Cervena, Zelena, Modra };
```

##### Přístup k Výčtovým Typům Pomocí Čísel
Výčtové typy (`enum`) v C# reprezentují sadu pojmenovaných konstantních hodnot. Každá hodnota ve výčtu je interně reprezentována jako číslo. Můžete přistupovat k hodnotám výčtu buď přímo podle názvu, nebo pomocí číselného ekvivalentu.

**Příklad:**
```csharp
enum Barva { Cervena = 1, Zelena = 2, Modra = 3 }

Barva maBarva = (Barva)2;
Console.WriteLine(maBarva); // Výstup: Zelena
```
V tomto příkladu `Barva` používá čísla pro přístup k hodnotám výčtu. Pokud je přiřazena hodnota `2`, odpovídá to `Zelena`.

###### Okrajové Případy
Existuje několik důležitých věcí, které je třeba mít na paměti při práci s výčtovými typy:

1. **Implicitní Hodnoty**: Pokud explicitně nepřiřadíte hodnoty členům výčtu, začnou automaticky od nuly.
   ```csharp
   enum Barva { Cervena, Zelena, Modra }
   Barva barva = (Barva)1;
   Console.WriteLine(barva); // Výstup: Zelena
   ```

2. **Mimo Rozsah**: Můžete přiřadit výčtu jakoukoliv hodnotu v rámci jeho podkladového datového typu (většinou `int`), i když hodnota neexistuje v definici výčtu.
   ```csharp
   Barva barva = (Barva)99;
   Console.WriteLine(barva); // Výstup: 99 (není to platná hodnota v rámci výčtu)
   ```

3. **Flags Attribute**: Pokud použijete atribut `[Flags]`, můžete kombinovat hodnoty výčtu jako bitová pole.
   ```csharp
   [Flags]
   enum Prava { Cist = 1, Psat = 2, Smazat = 4 }
   Prava prava = Prava.Cist | Prava.Psat;
   Console.WriteLine(prava); // Výstup: Cist, Psat
   ```

Tyto koncepty jsou důležité pro práci s výčtovými typy v C# a mohou výrazně ovlivnit způsob, jakým budete s výčty pracovat.
#### Referenční typy
Referenční typy ukládají odkaz (referenci) na skutečná data, která jsou uložena na haldě (heap). Typickými referenčními typy jsou **třídy** (`class`), **rozhraní** (`interface`), **delegáti** a **pole**. Práce s referenčními typy může být náročnější na výkon kvůli alokaci na haldě a nutnosti garbage collectoru pro správu paměti.

**Příklad:**
```csharp
string text = "Ahoj";
class Osoba { public string Jmeno; }
```

#### Klíčové rozdíly mezi hodnotovými a referenčními typy:
- **Hodnotové typy**: Data jsou uložena přímo, změny se provádějí na lokální kopii.
- **Referenční typy**: Data jsou uložena na haldě, změny prováděné na kopii ovlivňují původní objekt.