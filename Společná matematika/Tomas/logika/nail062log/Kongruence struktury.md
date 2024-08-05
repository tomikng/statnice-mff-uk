---
tags:
  - nail062log
---
**Kongruence**
- ekvivalence $\sim$ na množině $A$ je kongruencí:
- pro funkce $f:A^{n}\to A$
	- Pro všechna $a_{i},b_{i}\in A: a_{i}\sim b_{i} \Rightarrow f(\bar{a})\sim f(\bar{b})$
- pro relace $R \subseteq A^{n}$
	- Pro všechna $a_{i},b_{i}\in A: a_{i}\sim b_{i} \Rightarrow \bar{a}\in R \Leftrightarrow \bar{b}\in R$
- pro strukturu $\mathcal{A}$:
	- Je kongruencí pro všechny fce a relace $\mathcal{A}$
- "Ekvivalence, která se chová dobře vůči funkcím a relacím"

**Faktorstruktura** (podílová struktura)$\mathcal{A}/_{\sim}$
- Struktura $\mathcal{A}$ podle $\sim$
- Univerzum je množina rozkladových [[Ekvivalence|tříd ekvivalence]] $A$ podle $\sim$
- Funkce a relace jsou pomocí **reprezentantů**
	- $f^\mathcal{A / _{\sim}}([a_{1}]_{\sim},\dots,[a_{n}]_{\sim})=[f^\mathcal{A}(a_{1},\dots,a_{n})]_{\sim}$  - ekvivalenční třída výsledku funkce
	- $R^\mathcal{A /  _{\sim}}([a_{1}]_{\sim},\dots,[a_{n}]_{\sim})\Leftrightarrow R^\mathcal{A}(a_{1},\dots,a_{n})$ - konkrétní reprezentanti tříd $a_{1},\dots,a_{n}$
- Příklad
	- $\mathbb{Z}_{n}$ je faktorstrukturou $\mathbb{Z}$ podle $\equiv (\mod n)$, 2 je reprezentant celých čísel se zbytkem 2 po dělení n

**Axiomy rovnosti**
- V jazyce $L_{=}$ musí platit:
	- $x=x$
	- $x_{1}=y_{1} \wedge \dots \wedge  x_{n} = y_{n} \to f(x_{1},\dots,x_{n})=f(y_{1},\dots,y_{n})$ pro každý n-ární funkční symbol $f\in L_{=}$
	- $x_{1}=y_{1} \wedge \dots \wedge  x_{n} = y_{n} \to (R(x_{1},\dots,x_{n})\to R(y_{1},\dots,y_{n}))$ pro každý n-ární funkční symbol $R\in L_{=}$
		- vyplývá symetrie a tranzitivita
