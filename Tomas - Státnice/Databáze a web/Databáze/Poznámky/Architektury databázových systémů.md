---
tags:
  - databaze
  - databaze_a_web
  - tomas
dg-publish: true
---
### Konceptuální, logická a fyzická úroveň

[[Exercise]]
1. **Konceptuální úroveň**:
	- **Popis:** Konceptuální úroveň představuje <mark style="background: #FFF3A3A6;">abstraktní pohled</mark> na data v databázi. Je to model, který reflektuje, jaké informace má systém uchovávat, <mark style="background: #FFF3A3A6;">ale nezabývá se detaily, jak budou data uložena či zpracovávána.</mark>
		1. **Analýza požadavků:**
	        - **Identifikace typů entit:** Identifikace hlavních entit, které systém bude obsahovat.
	        - **Identifikace typů vztahů:** Určení vztahů mezi těmito entitami.
	        - **Identifikace charakteristik:** Definice atributů a vlastností jednotlivých entit a vztahů.
		2. **Modelování identifikovaných typů:**
	        - **Volba modelovacího jazyka:** Výběr vhodného modelovacího jazyka, např. <mark style="background: #BBFABBA6;">ERD nebo UML</mark>.
	        - **Vytvoření konceptuálního schématu:** Vytvoření diagramů, které zachycují entity, vztahy a atributy.
	    3. **Iterativní přizpůsobení:**
	        - **Přizpůsobení schémat:** Schémata se postupně upravují, jak se mění požadavky.
	- **Příklad:** Entitně-relační diagram (ERD), kde jsou entity a jejich vztahy modelovány bez ohledu na konkrétní implementaci.
2. **Logická úroveň:**
	![[Pasted image 20240812113553.png]]
   - **Popis:** Logická úroveň definuje, <mark style="background: #FFF3A3A6;">jak jsou konceptuální entity a vztahy z konceptuálního modelu převedeny do konkrétních datových struktur, které lze použít v databázovém systému</mark>. Tato struktura zahrnuje definice tabulek, sloupců, datových typů, primárních a cizích klíčů, a další prvky nezbytné pro ukládání a přístup k datům.

   **Kroky logického modelování:**
	   1. **Výběr vhodného logického modelu:**
	      - **Popis:** Na základě požadavků na přístup k datům se rozhoduje, <mark style="background: #FFB8EBA6;">který logický model bude použit</mark>. Například pro <mark style="background: #BBFABBA6;">relační databáze</mark> se používá <mark style="background: #BBFABBA6;">relační model</mark>, pro ukládání <mark style="background: #BBFABBA6;">hierarchických dat</mark> může být použit <mark style="background: #BBFABBA6;">XML</mark> model, a pro <mark style="background: #BBFABBA6;">navigační přístup</mark> k datům je vhodný <mark style="background: #BBFABBA6;">objektový model</mark>.
	   2. **Převod konceptuálního modelu na logický model:**
	      - **Popis:** Konceptuální model je převeden do logického schématu. Tento krok zahrnuje definici <mark style="background: #BBFABBA6;">primárních klíčů, cizích klíčů</mark> a dalších integritních omezení.
	      - **Příklad:** 
		  ![[Pasted image 20240812114130.png]]
		![[Pasted image 20240812114156.png]]   
		![[Pasted image 20240812114214.png]]
		   ![[Pasted image 20240812114414.png]]
	   3. **Vytváření logického schématu:**
	      - **Popis:** Výsledné schéma zahrnuje detailní strukturu tabulek, včetně sloupců, klíčů a jejich vztahů. Tento krok zajišťuje, že databázová struktura je připravena pro fyzickou implementaci.
	      - **Příklad:** V UML diagramu může být třída `Person` převedena na tabulku `Person`, která bude obsahovat sloupce jako `personID`, `personalNumber`, `name`, a `email`.

3. **Fyzická úroveň:**
   - **Popis:** Fyzická úroveň se týká skutečné implementace databáze na hardwaru. Zde se rozhoduje o způsobu uložení dat, indexování, optimalizaci dotazů a dalších technických detailech.
   - **Příklad:** Použití konkrétního typu indexů pro rychlejší vyhledávání v tabulce, optimalizace dotazů pro zvýšení výkonu. SQL definice, viz [[#Přehled SQL [🔗](https //www.sql-practice.com/)]]
![[Pasted image 20240812103348.png]]
