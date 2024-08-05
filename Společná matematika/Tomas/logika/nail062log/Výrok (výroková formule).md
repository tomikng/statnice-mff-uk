---
tags:
  - nail062log
---
**Výrok** $\varphi$
- prvek induktivně definované množiny $VF_\mathbb{P}$ v jazyce $\mathbb{P}$
	- do VF patří každý prvovýrok p jazyka P
	- a jeho negace ~p
	- a pro každé dva výroky z VF patří i jejích spojení $\varphi \ \square \ \psi$
- $\top = (p \vee \neg p)$ = pravda
- $\bot = (p \wedge \neg p)$ = spor
- $Var(\varphi)$ = množina prvovýroků z $\varphi$

Strom výroku $Tree(\varphi)$
- zakořeněný induktivně definovaný uspořádaný strom
	- je-li $\varphi$ prvovýrok p, obsahuje jediný vrchol s labelem p
	- je-li $\varphi$ ve tvaru negace $\neg\varphi'$, obsahuje vrchol s labelem $\neg$ a synem je kořen $\varphi'$
	- je-li $\varphi$ ve tvaru $\varphi' \square \varphi''$, v kořenu je label $\square$ , levý syn je $\varphi'$ a pravý je $\varphi''$
		- $\square \in \{\wedge , \vee ,\rightarrow, \leftrightarrow\}$

**Sémantické pojmy výroku v jazyce**
- pravdivý (tautologie, platí) - platí v každém modelu jazyka $$M_{\mathbb{P}}(\varphi) = M_\mathbb{P}$$
	- $\top$
- lživý (sporný) - neplatí v žádném modelu jazyka $$M_{\mathbb{P}}(\varphi) = \emptyset$$
	- $\bot$
- nezávislý - platí v nějakém a neplatí v nějakém jiném modelu, ani pravdivý, ani lživý $$\emptyset \subset  M_{\mathbb{P}}(\varphi) \subset  M_{\mathbb{P}}$$
	- je mezi prázdnou množinou a celou množinou modelů exklizivně
	- $p$
- splnitelný
	- má nějaký model $$ M_{\mathbb{P}}(\varphi)\neq \emptyset$$
	- pravdivé a nezávislé modely jsou splnitelné, není lživý
- ekvivalentní výroky - mají shodné množiny modelů
	- $$\varphi\sim \psi \Leftrightarrow  M_{\mathbb{P}}(\varphi)= M_{\mathbb{P}}(\psi)$$
	- $p \sim p \vee p$

**Sémantické pojmy výroku $\varphi$ v teorii $T$**
- **pravdivý** (důsledek $T$, platí v $T$) - $T \models \varphi$ - platí v každém modelu teorie $$ M_{\mathbb{P}}(T)\subseteq M_{\mathbb{P}}(\varphi)$$
- lživý (**sporný**) - neplatí v žádném modelu $T$: $$ M_{\mathbb{P}}(\varphi)\cap  M_{\mathbb{P}}(T) =  M_{\mathbb{P}}(T,\varphi) = \emptyset$$
- **nezávislý** - platí v nějakém modelu teorie a neplatí v jiném $$\emptyset \subset  M_{\mathbb{P}}(T,\varphi) \subset  M_{\mathbb{P}}(T)$$
- **splnitelný** (konzistentní) - platí v nějakém modelu $T$, není lživý $$ M_{\mathbb{P}}(T, \varphi)\neq \emptyset$$
- ekvivalentní (**T-ekvivalentní**) výroky - platí ve stejných modelech teorie: $$\varphi\sim_{T} \psi \Leftrightarrow  M_{\mathbb{P}}(T,\varphi)= M_{\mathbb{P}}(T,\psi)$$