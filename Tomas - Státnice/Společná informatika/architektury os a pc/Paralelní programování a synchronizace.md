---
dg-publish: true
tags:
  - architektura_pc_a_os
  - spolecna_informatika
  - tomas
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě [prezentace](https://cdn.tom-nguyen.dev/06-sync.pdf).

### 1. **Paralelismus a Vlákna**
   - **Paralelní výpočet:** Paralelismus zahrnuje provádění více výpočtů současně, což může být na úrovni bitů, instrukcí, dat nebo úkolů. Paralelní výpočet rozděluje úlohy mezi více procesorů, aby se urychlil výpočet a efektivně využily dostupné hardwarové zdroje.
   - **Vlákna:** Vlákno je nejmenší jednotka procesu, kterou může CPU naplánovat a vykonat. Více vláken může existovat v rámci jednoho procesu a sdílí stejný paměťový prostor. Toto sdílené prostředí může vést k problémům, jako jsou časově závislé chyby (race conditions), pokud nejsou správně řízena.

### 2. **Časově Závislé Chyby (Race Conditions)**
   - **Definice:** K časově závislým chybám dochází, když více vláken přistupuje k sdíleným datům v paměti současně a jejich výsledek závisí na pořadí nebo načasování jejich plánování.
   - **Příklad:** Představme si třídu `List`, která má metodu `PushFront`, jež přidává nový uzel na začátek seznamu. Pokud dvě vlákna současně zavolají tuto metodu, může dojít k chybě:

 ```cpp
 class List {
   private:
	 Node *root;

   public:
	 void PushFront(Node *n) {
	   n->next = root;
	   root = n;
	 }
 };

 List lst;
 ```
![[Pasted image 20240816181806.png]]
 Pokud vlákno 1 volá `lst.PushFront(A);` a vlákno 2 volá `lst.PushFront(B);` bez synchronizace, může dojít k situaci, kdy bude pořadí uzlů nejasné a výsledné pořadí může být nečekané.

   - **Strana v PDF:** Pro více informací a podrobnosti viz stranu 3 a 4 v PDF.

### 3. **Kritická Sekce a Vzájemné Vyloučení (Mutual Exclusion)**
   - **Definice:** Kritická sekce je část programu, kde se přistupuje k sdílenému zdroji, což může vést k [[#2. **Časově Závislé Chyby (Race Conditions)**|race condition]] chybám nebo dokonce k nedefinovanému chování, pokud není chráněna.
   - **Řešení:** Řešením je zajistit, aby kritická sekce byla chráněna pomocí mechanismů vzájemného vyloučení, což zajišťuje, že v daném okamžiku může být kritická sekce vykonávána maximálně jedním vláknem.
   - **Strana v PDF:** Viz stranu 5 v PDF pro více informací.

### 4. **Synchronizační Primitiva a Jejich Použití**
   - **Zámky:** Zámky (lock) jsou synchronizační mechanismy, které umožňují blokování [[#3. **Kritická Sekce a Vzájemné Vyloučení (Mutual Exclusion)**|kritické sekce]] tak, aby byla v daném okamžiku přístupná pouze jednomu vláknu.
     - **Spin-lock:** Používá se pro krátkodobé čekání, kde vlákno aktivně čeká (busy waiting), dokud není kritická sekce dostupná.
   - **Semaphore:** Je počítadlo chráněné zámkem, které umožňuje řízení přístupu k omezenému počtu zdrojů.
     - **Mutex:** Je speciální typ semaforu, který implementuje vzájemné vyloučení, kde je počet přístupů omezen na 1.
    ![[Pasted image 20240816182122.png]]
   - **Aktivní a Pasivní Čekání:**
     - **Aktivní čekání:** Vlákno aktivně testuje podmínku v cyklu, dokud není splněna.
     - **Pasivní čekání:** Vlákno je blokováno, dokud není podmínka splněna a přístup povolen.
   - **Strana v PDF:** Podrobnosti o těchto mechanismech najdete na stranách 7 až 9 v PDF.

Tyto koncepty jsou klíčové pro správnou správu vláken a zajištění toho, aby paralelní a souběžné programy běžely bez chyb. Pro hlubší pochopení doporučuji prostudovat zmíněné strany v PDF, kde jsou uvedeny i kódy a další podrobnosti.