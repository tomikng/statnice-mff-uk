---
tags:
  - nail062log
---
Normální forma výroku
- ekvivalentní tvar, buď konjunkce disjunkcí (CNF) nebo disjunkce konjunkcí (DNF)
- literál - prvovýrok nebo jeho negace
	- opačný literál - literál s opačnou pravdivostní hodnotou ($l=p \rightarrow\bar{l}=\neg p$)
	- $p^{0}=\neg p$
	- $p^{1}=p$
- Obecná konjunkce $\wedge$ = 1, pokud všechny prvky jsou 1
	- $\top$ pro prázdnou množinu
- Obecná disjunkce $\vee$ = 1, pokud alespoň jeden prvek je 1
	- $\bot$ pro prázdnou množinu
- CNF
	- klauzule - disjunkce literálů
	- jednotková klauzule má jeden literál
	- prázdná klauzule je $\bot$ (odpovídá obecné disjunkci)
	- prázdný CNF výrok je vždy $\top$ (odpovídá obecné konjunkci)
	- je pravdivý (platí v libovolném modelu) <=> každá klauzule obsahuje dvojici opačných literálů
- DNF
	- elementární konjunkce je konjunkce literálů
	- jednotková EK má jeden literál
	- prázdná EK je $\top$ (odpovídá obecné konjunkci)
	- prázdný DNF výrok je vždy $\bot$ (odpovídá obecné disjunkci)
	- je pravdivý (platí v libovolném modelu) <=> alespoň 1 klauzule neobsahuje dvojici opačných literálů

Dualita
- záměna 0/1 a $\vee$/$\wedge$
- Duální booleovské funkce $f(\neg x) = \neg g(x)$
- Pro $\varphi$ a duální k němu $\psi$ platí $\psi \sim \neg\varphi$ (modely $\psi$ jsou nemodely $\varphi$)
	- funkce $f_{\varphi, \mathbb{P}}, f_{\psi, \mathbb{P}}$ jsou navzájem duální
- DNF je duální k CNF
- pravdivý je duální k nesplnitelný

**(L1) Množinu modelů nad konečným jazykem lze axiomatizovat výrokem v CNF, výrokem v DNF.**
- Máme konečný jazyk $\mathbb{P}$ a libovolnou podmnožinu modelů jazyka $M \subseteq M_{\mathbb{P}}$
- Chceme dokázat existenci $\varphi_{DNF}$ a $\varphi_{CNF}$ t.ž. $$M=M_{\mathbb{P}}(\varphi_{DNF})=M_{\mathbb{P}}(\varphi_{CNF})$$
- Intuice - DNF tvoří modely, CNF nemodely
	- EK v DNF určují povolené model (platí $v$ nebo $w$)
	- klauzule v CNF určijí zakázané modely (jsou zakázané $v$ a $w$)
- Důkaz
	1. $\varphi_{DNF}$ - Každá elementární konjunkce popisuje jeden model, sjednotíme EK pro každý model.
	2. $\varphi_{CNF}$ - Z duality víme, že výrok CNF je duální k výroku DNF a modely DNF jsou nemodely CNF. Sestrojíme $M'=\overline{M}$ a vytvoříme z nich klauzule CNF.
		- $C_{v}=\bigvee_{p\in \mathbb{P}} p^{1-v(p)}$ - klauzule zakazuje model $v$ tím, že neguje každou jeho proměnnou
		- $M_{C}=M_{\mathbb{P}}\backslash \{v\}$ $\blacksquare$
- Důsledky
	- Každý výrok je ekvivalentní nějakému v CNF a DNF
		- Nekonečný jazyk pořád má konečné výroky, $\mathbb{P}'=Var(\varphi)$
		- $\varphi\sim \varphi_{DNF} \sim \varphi_{CNF}$