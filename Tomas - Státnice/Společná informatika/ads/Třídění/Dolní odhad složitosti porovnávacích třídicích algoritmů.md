## Dolní odhad složitosti porovnávacích třídicích algoritmů

Dolní odhad složitosti porovnávacích třídicích algoritmů, který se často zmiňuje v souvislosti s obecnými porovnávacími třídicími algoritmy, je $O(n \log n)$. Tento odhad je založen na faktu, že každý porovnávací třídicí algoritmus musí v nejhorším případě provést určité minimální množství porovnání, aby správně seřadil všechny prvky.

### Důvod pro dolní odhad $O(n \log n)$:

1. **Počet permutací:** Pokud máte $n$ prvků, existuje $n!$ různých možných uspořádání těchto prvků.

2. **Strom rozhodnutí:** Porovnávací třídicí algoritmus lze modelovat jako binární strom rozhodnutí, kde každý vnitřní uzel představuje jedno porovnání a každý list odpovídá jednomu z možných uspořádání vstupu.

3. **Výška stromu:** Aby algoritmus byl schopen určit správné uspořádání pro jakékoliv z $n!$ možných pořadí, musí strom rozhodnutí mít alespoň $n!$ listů. Minimální výška binárního stromu s $n!$ listy je $\log_2(n!)$.

4. **Logaritmus faktoriálu:** Pomocí Stirlingova vzorce lze odhadnout $\log_2(n!)$ jako přibližně $n \log_2 n$, což dává dolní hranici počtu porovnání jako $\Omega(n \log n)$.

Tento dolní odhad znamená, že žádný porovnávací třídicí algoritmus (jako je například QuickSort, MergeSort nebo HeapSort) nemůže v průměrném případě nebo v nejhorším případě běžet rychleji než $O(n \log n)$, co se týče počtu porovnání.
