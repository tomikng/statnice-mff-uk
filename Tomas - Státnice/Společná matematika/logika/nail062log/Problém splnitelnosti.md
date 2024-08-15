---
tags:
  - nail062log
aliases:
  - SAT
  - Satisfiability problem
---
## SAT solvery 
k-SAT
- má nejvýš $k$ literálů v každé klauzuli
- 3-SAT je NP-úplný, 2-SAT a Horn-SAT lze řešit polynomiálně

[[Silná souvislost grafu|Silně souvislá]] [[Komponenta souvislosti|komponenta]]
- každá dvojice vrcholu leží v orientovaném cyklu
- každý orientovaný cyklus leží uvnitř komponenty
- ohodnocení komponenty - nastavení stejné hodnoty na všechny literály
	- $(p_{1},\neg p_{2},p_{3}) = 1$ <=> $p_{1}=1, p_{2}=0, p_{3} =1$
 
**Implikační graf**
- řeší 2-SAT
- Algoritmus
	1. Sestrojíme DAG z $\varphi$
		- vrcholy - pozitivní a negativní literály $p, \neg p$ pro všechny proměnné výroku $p\in Var(\varphi)$
		- hrany - obě možné implikace $(\bar{l_{1}},l_{2}),(\bar{l_{2}}, l_{1})$ z každé klauzule $l_{1} \vee l_{2}$ a implikace $(\bar{l}, l)$ pro jednotkové klauzule
	2. Pokud komponenta obsahuje dvojici opačných literálů, výrok je nesplnitelný
	3. Jinak v topologickém pořádí ohodnotíme každou neohodnocenou komponentu jako 0 a její opak jako 1 - výsledkem je model $\varphi$
- Korektnost
	- Výskyt opačných literálů v 1 komponentě znamená nesplnitelnost výroku <=> Model musí ohodnostit lierály ze stejné komponenty stejnou hodnotou - jinak bychom měli implikaci 1->0 v cyklu
	- Ohodnocení bez opačných literálů je model - Hodnotíme komponenty v topologickém uspořádaní nejdřív 0 a pak 1 - nemůže nastat 1->0
		- Jednotková klauzule platí, protože máme hranu ~l->l
		- Klauzule (l1 v l2) platí, protože vždy splníme alespoň jeden literál:
			- pro ~l1->l2 musíme položit ~l1=0 (l1 platí, platí klauzule)
			- pro ~l2->l1 zase ~l2=0 (l2 platí, platí klauzule)
- Složitost
	- 2-SAT lze řešit lineárně - komponenty silné souvislosti lze nalézt v O(m+n) a [[Topologické uspořádání grafu|DAG]] postavíme také v O(m+n)

[[Horn-SAT]]

**Čistý výskyt literálu**
- literál l je ve výroku a jeho opačný ~l není
- můžeme ho nastavit na 1 a tím splnit všechny klauzule, které ho obsahují

**DPLL**
- řeší obecný SAT
- Algoritmus
	1. Dokud $\varphi$ obsahuje jednotkovou klauzuli {l}, nastav l=1, proveď jednotkovou propagaci a nahraď $\varphi=\varphi^{l}$
	2. Dokud $\varphi$ obsahuje literál l s čistým výskytem, nastav l=1 a odstraň klauzule obsahující l
	3. Pokud $\varphi$ neobsahuje žádnou klauzuli, je splnitelný
	4. Pokud $\varphi$ obsahuje prázdnou klauzuli, není splnitelný
	5. Jinak zvol neohodnocenou proměnnou a zavolej DPLL na $\varphi \wedge p$ a $\varphi \wedge \neg p$
- Korektnost
	- viz čistý výskyt a jednotková propagace
