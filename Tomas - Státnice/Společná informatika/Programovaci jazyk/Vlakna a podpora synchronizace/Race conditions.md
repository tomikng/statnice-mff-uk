---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
### Časově Závislé Chyby a Mechanizmy pro Synchronizaci Vláken v C#

#### Časově Závislé Chyby (Race Conditions)
[[Paralelní programování a synchronizace#2. **Časově Závislé Chyby (Race Conditions)**|Časově závislé chyby]], nebo **race conditions**, nastávají, když dvě nebo více vláken přistupuje k sdíleným datům současně, přičemž alespoň jedno z vláken tato data mění. To může vést k nekonzistentním nebo nečekaným výsledkům, protože pořadí operací není předem určeno.

**Příklad:**
```csharp
int pocitadlo = 0;

void ZvysitPocitadlo()
{
    for (int i = 0; i < 1000; i++)
    {
        pocitadlo++;
    }
}

Thread vlakno1 = new Thread(ZvysitPocitadlo);
Thread vlakno2 = new Thread(ZvysitPocitadlo);

vlakno1.Start();
vlakno2.Start();

vlakno1.Join();
vlakno2.Join();

Console.WriteLine(pocitadlo); // Výstup může být nekonzistentní kvůli race condition
```

V tomto případě dvě vlákna současně zvyšují hodnotu proměnné `pocitadlo`, což může vést k nekonzistentním výsledkům kvůli race condition.

#### Mechanizmy pro Synchronizaci Vláken

1. **`lock` Blok**:
   - `lock` blokuje přístup ke sdílenému zdroji, aby zajistil, že pouze jedno vlákno může provádět kritickou sekci kódu najednou.

   **Příklad:**
   ```csharp
   private static readonly object zamek = new object();

   void ZvysitPocitadloBezpecne()
   {
       lock(zamek)
       {
           for (int i = 0; i < 1000; i++)
           {
               pocitadlo++;
           }
       }
   }
   ```

   - `lock` zajišťuje, že jakmile jedno vlákno vstoupí do kritické sekce, ostatní vlákna musí počkat, dokud není tato sekce dokončena.

2. **`Monitor` a `Mutex`**:
   - `Monitor` je podobný `lock`, ale nabízí více funkcí, jako je explicitní čekání a signalizace.
   - `Mutex` (Mutual Exclusion) se používá pro synchronizaci vláken napříč různými procesy.

   **Příklad s `Monitor`:**
   ```csharp
   Monitor.Enter(zamek);
   try
   {
       // Kritická sekce
   }
   finally
   {
       Monitor.Exit(zamek);
   }
   ```

**Priklad s Mutex**
```csharp
using System;
using System.Threading;

class Program
{
    // Vytvoření globálního mutexu
    static Mutex mutex = new Mutex();

    static void Main()
    {
        Thread vlakno1 = new Thread(Pracuj);
        Thread vlakno2 = new Thread(Pracuj);

        vlakno1.Start();
        vlakno2.Start();

        vlakno1.Join();
        vlakno2.Join();

        Console.WriteLine("Obě vlákna dokončena.");
    }

    static void Pracuj()
    {
        Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} čeká na mutex...");
        mutex.WaitOne(); // Čeká na získání mutexu

        try
        {
            Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} získal mutex, pracuje...");
            Thread.Sleep(2000); // Simulace práce
        }
        finally
        {
            Console.WriteLine($"{Thread.CurrentThread.ManagedThreadId} uvolňuje mutex.");
            mutex.ReleaseMutex(); // Uvolnění mutexu
        }
    }
}

```

3. **`AutoResetEvent` a `ManualResetEvent`**:
   - Tyto třídy umožňují vláknům čekat, dokud nejsou signalizovány k pokračování.

   **Příklad:**
   ```csharp
   AutoResetEvent autoEvent = new AutoResetEvent(false);

   void Pracuj()
   {
       Console.WriteLine("Čekám na signál...");
       autoEvent.WaitOne(); // Čeká na signál
       Console.WriteLine("Pracuji po signálu");
   }

   // Spuštění vlákna
   Thread vlakno = new Thread(Pracuj);
   vlakno.Start();

   // Signalizace vlákna k pokračování
   autoEvent.Set();
   ```

### Shrnutí
- **Časově závislé chyby** vznikají, když více vláken přistupuje ke sdíleným datům bez správné synchronizace.
- **Mechanizmy pro synchronizaci** jako `lock`, `Monitor`, `Mutex`, `AutoResetEvent`, a `ManualResetEvent` jsou klíčové pro zajištění správného a bezpečného přístupu ke sdíleným prostředkům mezi vlákny.
