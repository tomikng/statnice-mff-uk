---
dg-publish: true
tags:
  - tomas
  - databaze_a_web
  - web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek
### Cíle, rozdíly a omezení hodnocení doporučovacích systémů

#### **Cíle hodnocení doporučovacích systémů**

Hodnocení doporučovacích systémů má několik klíčových cílů:

1. **Měření účinnosti:** Hlavním cílem je zjistit, jak efektivně doporučovací systém dokáže předvídat preference uživatelů, zvyšovat zapojení, spokojenost nebo konverze.
   
2. **Zjištění uživatelské spokojenosti:** Je důležité hodnotit, jak jsou uživatelé spokojeni s doporučeními, zda jim doporučené položky přinášejí hodnotu, a zda se zvyšuje pravděpodobnost, že si dané položky zakoupí nebo využijí.

3. **Zajištění relevance:** Systémy by měly poskytovat relevantní doporučení, která odpovídají zájmům a potřebám uživatelů, a to jak v krátkodobém, tak dlouhodobém horizontu.

4. **Zvýšení diverzity a serendipity:** Doporučení by měla nejen vycházet z dřívějších preferencí, ale měla by také zahrnovat nové, nečekané položky (serendipity) a různé typy položek (diverzita).

5. **Vyhodnocení obchodních cílů:** Doporučovací systémy by měly být hodnoceny i podle toho, jak přispívají k obchodním cílům, jako je zvyšování prodejů, zlepšování retence uživatelů nebo zvyšování počtu zhlédnutí na webu.

#### **Offline, online a uživatelské studie v hodnocení doporučovacích systémů**

1. **Offline hodnocení**
   - **Cíle:** Testování výkonu algoritmů na historických datech. Hlavním cílem je získat rychlý přehled o tom, jak algoritmus funguje bez potřeby skutečných uživatelů.
   - **Výhody:** Rychlé, levné, replikovatelné. Je možné provést rozsáhlé experimenty na různých algoritmech a nastaveních, aniž by bylo nutné ovlivňovat živé uživatele.
   - **Omezení:** Může vést k nepřesným výsledkům, protože chybí zpětná vazba od skutečných uživatelů a interakce nejsou dynamické. Z tohoto důvodu offline hodnocení často nadhodnocuje výkon systému.

2. **Online hodnocení (např. A/B testování)**
   - **Cíle:** Hodnocení systému v reálném čase s reálnými uživateli. Měří skutečný dopad doporučovacích systémů na uživatele a jejich chování.
   - **Výhody:** Poskytuje realistické výsledky, protože měří reakce skutečných uživatelů. Může poskytnout informace o tom, jak systém ovlivňuje obchodní cíle.
   - **Omezení:** Nákladné a časově náročné. Může ovlivnit uživatelskou zkušenost negativním způsobem, pokud systém není optimálně nastaven. Také může být obtížné replikovat výsledky v jiném prostředí nebo s jinými uživateli.

3. **Uživatelské studie**
   - **Cíle:** Zkoumání hlubšího pochopení toho, jak uživatelé interagují s doporučovacím systémem, jaké mají pocity, jaké jsou jejich subjektivní názory na doporučení.
   - **Výhody:** Umožňují získat kvalitativní zpětnou vazbu, kterou nelze získat z čistě kvantitativních měření. Pomáhají odhalit aspekty jako důvěra, srozumitelnost a spokojenost.
   - **Omezení:** Malá vzorková velikost, časově náročné, subjektivní bias. Je obtížné generalizovat výsledky z malé skupiny uživatelů na celou populaci.

#### **Typické hodnotící metriky**

1. **Relevance a přesnost:**
   - **Precision:** Měří přesnost, tedy podíl relevantních položek mezi všemi doporučenými položkami.
   - **Recall:** Měří úplnost, tedy podíl relevantních položek mezi všemi relevantními položkami, které měly být doporučeny.
   - **F1 Score:** Harmonický průměr mezi Precision a Recall, používaný k nalezení rovnováhy mezi těmito dvěma metrikami.

2. **Chybové metriky:**
   - **Mean Absolute Error (MAE):** Průměrná absolutní chyba mezi předpovězeným a skutečným hodnocením.
   - **Root Mean Squared Error (RMSE):** Kvadratický průměrný odhad chyby, který penalizuje větší chyby více než MAE.

3. **Hodnotící metriky založené na pořadí:**
   - **Normalized Discounted Cumulative Gain (nDCG):** Zohledňuje jak relevanci, tak pořadí položek v doporučovací sadě.
   - **Mean Average Precision (MAP):** Průměrná přesnost po každé úspěšné předpovědi, použitelné zejména pro hodnocení pořadí.

4. **Diverzita a serendipita:**
   - **Diverzita:** Měří, jak odlišné jsou doporučené položky navzájem.
   - **Serendipita:** Měří kombinaci relevance a neočekávanosti položek. Cílem je zajistit, aby uživatelé objevovali nové a zajímavé položky, které by jinak přehlédli.

5. **Uživatelská spokojenost a angažovanost:**
   - **Zvýšení konverzí:** Měření počtu nákupů nebo interakcí vyvolaných doporučeními.
   - **Doba strávená na webu:** Měří, jak dlouho uživatelé zůstávají na webu po interakci s doporučovacím systémem.
   - **Klikatelnost (Click-Through Rate, CTR):** Podíl kliknutí na doporučené položky oproti celkovému počtu zobrazených doporučení.

Tato komplexní sada metrik a přístupů umožňuje vyhodnocovat doporučovací systémy z různých perspektiv, aby bylo možné dosáhnout co nejlepších výsledků a uživatelského zážitku.
