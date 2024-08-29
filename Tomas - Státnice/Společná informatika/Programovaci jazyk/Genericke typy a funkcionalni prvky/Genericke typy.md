---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Generické Typy v C#

Generické typy umožňují vytvářet třídy, rozhraní a metody, které pracují s libovolnými datovými typy, aniž by bylo nutné psát opakovaný kód pro různé typy. Generika poskytují způsob, jak psát typově bezpečný kód, který je zároveň flexibilní a znovupoužitelný.

#### Příklad: Generická Třída
```csharp
public class Uloziste<T>
{
    private T data;

    public void NastavData(T hodnota)
    {
        data = hodnota;
    }

    public T ZiskejData()
    {
        return data;
    }
}
```
V tomto příkladu je `T` generický typový parametr, který umožňuje `Uloziste` pracovat s libovolným datovým typem.

#### Příklad: Generická Metoda
```csharp
public void VypisData<T>(T vstup)
{
    Console.WriteLine(vstup);
}
```
Tato metoda může přijmout jakýkoli typ `T`, což ji činí velmi flexibilní.

### Výhody generických typů:
- **Typová bezpečnost**: Pomáhá předcházet chybám při běhu programu tím, že poskytuje kontrolu typů při kompilaci.
- **Výkon**: Vyhýbá se nutnosti boxingu a unboxingu pro hodnotové typy, čímž zvyšuje výkon.
- **Znovupoužitelnost**: Umožňuje psát univerzální kód, který může pracovat s různými typy bez nutnosti opakování kódu.