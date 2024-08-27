---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě poznamek

Shannonova věta o kódování zdrojů, také známá jako **Shannon’s source coding theorem**, je základní princip v teorii informace, který se zabývá efektivitou komprese dat. Tato věta je pojmenována po Claudu Shannonovi, který je považován za zakladatele moderní teorie informace.

> [!Video] Understand more intuitively
> [Video](https://www.youtube.com/watch?v=0GCGaw0QOhA)

### Význam Shannonovy věty o kódování zdrojů:

# Základní princip
   - Shannonova věta o kódování zdrojů uvádí, že existuje určitá minimální hranice, na kterou lze data komprimovat bezeztrátovým způsobem. Tato hranice je určena entropií zdroje, který generuje data.
   - **Entropie** je měřítko průměrné nejistoty nebo informace obsažené v symbolu z daného zdroje. Vyjadřuje, kolik bitů je zapotřebí k tomu, aby bylo možné jednoznačně popsat výstup zdroje (např. zprávy, soubory, signály).

# Matematické vyjádření
   - Pokud máme zdroj dat, který generuje symboly s určitou pravděpodobnostní distribucí, pak minimální počet bitů potřebných pro bezeztrátovou kompresi těchto dat na symbol je roven entropii tohoto zdroje.
   - V matematické podobě je to vyjádřeno jako:
     $$
     H(X) = -\sum_{i=1}^{n} P(x_i) \log_2 P(x_i)
     $$
     kde $H(X)$ je entropie zdroje $X$, $P(x_i)$ je pravděpodobnost výskytu symbolu $x_i$ a $n$ je počet různých symbolů, které zdroj může generovat.

# Význam pro kompresi dat
   - **Bezeztrátová komprese**: Shannonova věta o kódování zdrojů stanoví, že data generovaná zdrojem nemohou být bezeztrátově komprimována pod úroveň jejich entropie. To znamená, že žádná bezeztrátová komprese nemůže být efektivnější než komprese na úroveň entropie zdroje.
   - **Optimální kódování**: V praxi to znamená, že optimální kódovací schéma, které se blíží entropii zdroje, bude nejefektivnější z hlediska minimalizace délky komprimovaného datového souboru. Shannonova věta také inspiruje různé algoritmy, jako je Huffmanovo kódování nebo aritmetické kódování, které se snaží dosáhnout této optimální míry komprese.

# Příklady
   - Pokud máme zdroj, který generuje znaky 'A' a 'B' s pravděpodobností 0,5 každý, entropie tohoto zdroje bude 1 bit na symbol (protože \(H(X) = -0.5 \log_2 0.5 - 0.5 \log_2 0.5 = 1\)). To znamená, že ideálně by každý znak měl být kódován pomocí jednoho bitu.
   - Na druhou stranu, pokud zdroj generuje 'A' s pravděpodobností 0,9 a 'B' s pravděpodobností 0,1, entropie bude nižší než 1 bit (přesněji 0,469 bitu na symbol), což naznačuje, že můžeme dosáhnout efektivnější komprese než v prvním případě.

### Shrnutí
Shannonova věta o kódování zdrojů je základním teoretickým principem, který určuje, jak efektivně lze data komprimovat bezeztrátovým způsobem. V kontextu komprese dat nám tato věta říká, že existuje limit, jak malé mohou být komprimované soubory bez ztráty informací, a tento limit je určen entropií zdroje dat. Tento princip má zásadní význam pro navrhování efektivních kompresních algoritmů a pro pochopení limitů, které nelze překročit při bezeztrátové kompresi dat.