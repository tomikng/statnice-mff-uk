---
tags:
  - nail062log
---
**Podstruktura** (indukovaná strukturou)
- B je podstrukturou A - $\mathcal{B}\subseteq \mathcal{A}$:
	- $B \neq \emptyset$ - podmnožina domény je neprázdná
	- $R^{\mathcal{B}}=R^{\mathcal{A}}\cap B^{ar(R)}$ - relace jsou omezené na doménu B
	- $f^{\mathcal{B}}=f^{\mathcal{A}}\cap(B^{ar(f)}\times B)$ - restrikce vstupů a výstupů $f^{\mathcal{A}}$ na doménu B
		- $c^{\mathcal{B}}=c^{\mathcal{A}} \in B$ - B obsahuje všechny konstanty z A
	- B je **uzavřená** na všechny funkce a obsahuje všechny konstanty
		- $B \subseteq A$ je uzavřená na $f: A^{n}\to A$ <=> $\forall x_{i}\in B: f(x_{1},\dots,x_{n})\in B$
		- $\mathcal{A} \upharpoonright C$ - restrikce A na množinu C
	- Každá podstruktura modelu otevřené teorie T je také model T

**Generovaná podstruktura** množinou $X$
- Pro strukturu $\mathcal{A}=\langle A,\mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}} \rangle$ a neprázdnou množinu $X \subseteq A$
- $B$ je nejmenší uzavřená podmnožina $A$, která obsahuje $X$
	- $X \subseteq B \subseteq A$
	- $B$ uzavírá $X$
	- $\mathcal{A}$ je restrikce na uzávěr $X$
- $\mathcal{A} \langle X\rangle = \mathcal{A} \upharpoonright B$ je podstruktura generovaná množinou $X$
	- $\mathbb{Q}\langle \{1\}\rangle = \mathbb{N}$ - množina přirozených čísel je nejmenší uzávěr $\{1\}$

**Expanze a redukt** ($L'$-expanze a $L$-redukt)
- nové struktury změnou množin $\mathcal{R}, \mathcal{F}$
- Struktura $\mathcal{A}'_{L'}$ je expanzí $\mathcal{A}_{L}$ <=> $\mathcal{A}_{L}$ je reduktem $\mathcal{A}'_{L'}$, když:
	- $L \subseteq L'$
	- $A = A'$
	- Interpretace funkčních a relačních symbolů z $L$ je stejná v $\mathcal{A}'_{L'}$
