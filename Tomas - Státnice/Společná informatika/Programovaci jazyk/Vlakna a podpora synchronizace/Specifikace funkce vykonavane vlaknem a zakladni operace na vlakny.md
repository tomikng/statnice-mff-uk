---
dg-publish: true
tags:
  - tomas
  - spolecna_informatika
  - programovaci_jazyky
---
Tento příklad demonstruje použití několika operací s vlákny, včetně `Start`, `Join`, `Sleep`, `Interrupt`, a dalších.

```csharp
using System;
using System.Threading;

class Program
{
    static void Main()
    {
        // Vytvoření vlákna s metodou bez parametrů
        Thread vlakno1 = new Thread(PraceVlaken);
        // Vytvoření vlákna s metodou s parametrem
        Thread vlakno2 = new Thread(new ParameterizedThreadStart(PraceVlakenSParametrem));

        // Nastavení priority vlákna
        vlakno1.Priority = ThreadPriority.Highest;
        vlakno2.Priority = ThreadPriority.Lowest;

        // Spuštění vláken
        vlakno1.Start(); // Spustí vlakno1
        vlakno2.Start(5000); // Spustí vlakno2 a předá parametr

        // Pozastavení hlavního vlákna na 2 sekundy
        Thread.Sleep(2000);
        Console.WriteLine("Hlavní vlákno čeká, dokud se vlakno1 nedokončí.");

        // Čekání na dokončení vlakno1
        vlakno1.Join();

        // Kontrola, zda je vlakno2 stále aktivní
        if (vlakno2.IsAlive)
        {
            Console.WriteLine("Vlakno2 stále běží, přerušení vlákna...");
            vlakno2.Interrupt(); // Přeruší vlakno2, pokud je ve stavu čekání
        }

        // Čekání na dokončení vlakno2
        vlakno2.Join();
        Console.WriteLine("Všechna vlákna dokončena.");
    }

    static void PraceVlaken()
    {
        Console.WriteLine("Vlákno 1 začalo pracovat.");
        try
        {
            // Simulace práce vlákna
            for (int i = 0; i < 10; i++)
            {
                Console.WriteLine($"Vlákno 1 běží: Iterace {i + 1}");
                Thread.Sleep(500); // Pozastavení vlákna na 0,5 sekundy
            }
        }
        catch (ThreadInterruptedException)
        {
            Console.WriteLine("Vlákno 1 bylo přerušeno.");
        }
        Console.WriteLine("Vlákno 1 dokončeno.");
    }

    static void PraceVlakenSParametrem(object delay)
    {
        Console.WriteLine("Vlákno 2 začalo pracovat.");
        try
        {
            // Pozastavení vlákna o dobu zadanou v parametru
            Thread.Sleep((int)delay);
            Console.WriteLine("Vlákno 2 dokončeno po zpoždění.");
        }
        catch (ThreadInterruptedException)
        {
            Console.WriteLine("Vlákno 2 bylo přerušeno.");
        }
    }
}
```

### Co Dělá Tento Kód:

1. **Vytváření Vláken**: Dvě vlákna jsou vytvořena, jedno bez parametrů (`vlakno1`) a jedno s parametrem (`vlakno2`).
2. **Nastavení Priority**: `vlakno1` má nejvyšší prioritu, zatímco `vlakno2` má nejnižší prioritu.
3. **Start**: Obě vlákna jsou spuštěna, přičemž `vlakno2` dostane parametr zpoždění.
4. **Sleep a Join**: Hlavní vlákno čeká (`Sleep`) a poté čeká (`Join`), dokud se `vlakno1` nedokončí.
5. **Kontrola Stavu a Přerušení**: Pokud je `vlakno2` stále běžící (`IsAlive`), je přerušeno (`Interrupt`).
6. **Zpracování Přerušení**: Obě vlákna mají `try-catch` blok pro zpracování výjimky `ThreadInterruptedException`.

### Výstup:
Tento program demonstruje různé stavy vláken, jejich spuštění, zpracování přerušení a synchronizaci s hlavním vláknem.