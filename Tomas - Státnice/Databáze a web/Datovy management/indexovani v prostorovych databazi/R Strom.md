---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka

### **R-strom**
![[Pasted image 20240823134546.png]]
#### **Struktura a Operace**

R-strom je výškově vyvážený strom, podobný B-stromu, navržený pro indexování více dimenzionálních informací, jako jsou geografické souřadnice, obdélníky a polygony.

- **Uzly:** 
  - Každý uzel představuje minimální ohraničující obdélník (MBR), který obklopuje všechny své podřízené uzly nebo datové objekty.
  - Uzel může obsahovat více záznamů. Každý záznam je buď MBR podřízeného uzlu, nebo datový objekt.
  - Strom je výškově vyvážený, což znamená, že všechny listové uzly jsou na stejné hloubce.

#### **Operace R-stromu**

##### **1. Vkládání (Insertion):**

1. **ChooseLeaf:** Algoritmus začíná u kořene a rekurzivně vybírá nejlepší listový uzel pro vložení nového objektu. Vybere se ten podřízený uzel, jehož MBR vyžaduje nejmenší zvětšení, aby obsahoval nový objekt. Při rovnosti se vybere uzel s nejmenší plochou.
```
	ChooseLeaf(T,L,E) 
	Input: R-tree with a root T, index record E 
	Output: leaf L 
	
	N ← T; 
	WHILE N ≠ leaf DO 
		chose such entry F from N whose F.I needs least enlargement to include 
		E.I, in case of tie choose F.I with smallest area; 
		N ← F.p;
	L ← N;
```
   
2. **Insert:** Pokud má vybraný listový uzel volné místo, nový objekt je vložen přímo do něj. Pokud je uzel plný, je třeba provést operaci dělení.

3. **SplitNode:** Když je uzel plný, je rozdělen na dva nové uzly. Cílem dělení je minimalizovat překryv a celkovou plochu výsledných MBR. Používají se různé algoritmy, jako kvadratický nebo lineární nákladový algoritmus, pro optimální rozdělení záznamů mezi dva nové uzly.
![[Pasted image 20240823134926.png]]
![[Pasted image 20240823134942.png]]

5. **AdjustTree:** Po rozdělení se změny propagují nahoru stromem. Pokud se v kořeni objeví nový uzel v důsledku rozdělení, je vytvořen nový kořenový uzel.

##### **2. Vyhledávání (Search):**
![[Pasted image 20240823134558.png]]
1. **Search_R:** Hledání v R-stromu začíná v kořeni a prochází stromem rekurzivně dolů. Pro každý uzel se kontroluje, zda jeho MBR protíná hledaný objekt nebo oblast. Pokud ano, algoritmus pokračuje prohledáváním jeho podřízených uzlů.

2. **Výsledek:** Výsledkem hledání je množina objektů, které protínají hledaný objekt nebo oblast. Vyhledávání může vyžadovat průchod více cestami od kořene k listům, což může vést k proměnlivému výkonu v nejhorším případě.

##### **3. Mazání (Deletion):**

1. **ChooseLeaf:** Podobně jako při vkládání začíná algoritmus mazání u kořene a rekurzivně vybírá listový uzel, který obsahuje objekt k odstranění.

2. **Remove:** Po nalezení uzlu s objektem je objekt odstraněn. Pokud odstranění způsobí, že uzel má méně než minimální počet záznamů, může být uzel spojen s jiným uzlem nebo může dojít k přeskupení.

3. **AdjustTree:** Změny po odstranění se propagují nahoru stromem, aby se aktualizovaly MBR, a v případě potřeby se provádí slučování uzlů.

#### **Výhody R-stromu:**
1. **Efektivita dotazů:** R-stromy umožňují rychlé vyhledávání a rozsahové dotazy v multidimenzionálních prostorech.
2. **Vyváženost:** Strom je výškově vyvážený, což zajišťuje, že hloubka stromu je logaritmická vzhledem k počtu záznamů.
3. **Flexibilita:** R-stromy mohou pracovat s více dimenzemi, což je výhodné pro širokou škálu aplikací.

#### **Nevýhody R-stromu:**
1. **Překrývání:** MBR mohou překrývat, což může zhoršit výkon dotazů, protože může být potřeba prozkoumat více cest.
2. **Dělení uzlů:** Při vkládání nových objektů mohou být uzly rozděleny, což vede ke zvýšení počtu MBR a potenciálně i k většímu překrývání.

### **R+-strom a R*-strom**

#### **R+-strom:**

- **Princip:** R+-strom se snaží minimalizovat překrývání mezi MBR tím, že umožňuje, aby jeden objekt byl uložen ve více uzlech, pokud je to nutné. Tento přístup eliminuje překrývání na úrovni uzlů, což může zlepšit výkon vyhledávání.
  
- **Výhody:** R+-stromy mají menší počet prozkoumaných cest během vyhledávání, což vede k rychlejším dotazům, zejména u bodových dotazů.

- **Nevýhody:** Tento přístup může vést k duplikaci objektů v různých uzlech, což zvyšuje náročnost na úložiště.

#### **R*-strom:**

- **Princip:** R*-strom optimalizuje standardní R-strom přidáním dalších kritérií, jako je minimalizace plochy, překrývání a obvodu MBR. Tento přístup zahrnuje i přeskupování objektů při vkládání, což zlepšuje uspořádání stromu.

- **Výhody:** R*-stromy poskytují lepší výkon pro dotazy díky kompaktnějším MBR a menšímu překryvu. Použití přeskupování objektů vede k lepší organizaci dat v dlouhodobém horizontu.

- **Nevýhody:** Složitější algoritmus pro vkládání a údržbu, což může být výpočetně náročnější.

### **Shrnutí**

R-strom, R+-strom a R*-strom jsou klíčové datové struktury pro správu multidimenzionálních dat. Zatímco R-strom je základní struktura vhodná pro většinu aplikací, R+-strom a R*-strom nabízejí optimalizace, které mohou výrazně zlepšit výkon dotazů v specifických scénářích. Výběr mezi těmito strukturami závisí na požadavcích aplikace, zejména na potřebě rychlého vyhledávání, efektivního využití paměti a správy překrývajících se oblastí.