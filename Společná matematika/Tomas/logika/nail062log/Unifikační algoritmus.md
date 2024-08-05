---
tags:
  - nail062log
---
**Substituce**
- konečná množina $\sigma=\{x_{1}/t_{1},\dots x_{n}/t_{n}\}$, kde $x_{i}$ jsou navzájem různé proměnné a term $t_{i} \neq x_{i}$
	- **Základní** - všechny termy $t_{i}$ jsou konstantní
	- **Přejmenování proměnných** - všechy termy $t_{i}$ jsou navzájem různé proměnné
- **Instance** výrazu (termu/literálu) $E$ při substituci $\sigma$
	- $E \sigma = \{E \sigma| E \in S\}$ vznikne simultánním nahrazením všech výskytů $x_{i}$ termy $t_{i}$
		- nahrazujeme naraz, aby nedošlo k rekurzi
	- $S$ je množina výrazů
- **Skládání substitucí** $\sigma=\{x_{1}/t_{1},\dots\}$, $\tau=\{y_{1}/s_{1},\dots\}$
	- $\sigma \tau = \{x_{i}/t_{i} \tau | x_{i}\in X, x_{i} \neq t_{i} \tau\} \cup \{y_{j}/s_{j}|y_{j} \in Y \backslash X\}$ - nejdřív aplikujeme $\sigma$, pak $\tau$
	- není komutativní, záleží na pořadí
	- je asociativní, nezáleží na uzávorkování
	- $(E \sigma)\tau = E(\sigma \tau)$
	- $(\sigma \tau)\rho = \sigma(\tau \rho)$

**Unifikace**
- místo substituování všech základních termů je lepší najít vhodnou substituci
- Substituce $\sigma$ p ro konečnou množinu výrazů $S=\{E_{1},\dots,E_{n}\}$, t.ž. $E_{1} \sigma = E_{2} \sigma =\dots=E_{n} \sigma$, neboli $S \sigma$ obsahuje jediný výraz
	- Unifikovatelná množina výrazů - existuje taková substituce
- **Nejobecnější unifikace** - pokud pro každou unifikaci $\tau$ pro $S$ existuje substituce $\lambda: \tau= \sigma \lambda$
	- zbytek substitucí lze získat z nejobecnější
- **Unifikační algoritmus**
	- Postupuje od začátku výrazu a postupně aplikuje substituce t.ž. výrazy se stávaly víc podobné
	- $p$ - první, nejlevější pozice. na které se dva výrazy z $S$ líší
	- $D(S)$ - **neshoda**, množina všech podvýrazů začínajících na pozici $p$ výrazů z $S$
	- Vstup: konečná množina výrazů $S \neq \emptyset$
	- Výstup: nejobecnější unifikace $\sigma$ pro $S$ nebo informace, že $S$ není unifikovatelná
	1. Nastav $S_{0}:=S$, $\sigma_{0}:= \emptyset, k:= 0$
	2. Pokud $|S_{k}|=1$, vrať  $\sigma=\sigma_{0}\sigma_{1},\dots \sigma_{k}$
	3. Zjisti, zda v $D(S_{k})$ existuje proměnná $x$ a term $t$ neobsahující $x$
		- Ano: nastav $\sigma_{k+1} := \{x/t\}$, $S_{k+1}:= S_{k} \sigma_{k+1}$, $k:=k+1$, jdi na (1)
		- Ne: $S$ není unifikovatelná 
- Korektnost:
	- V každém kroku $k$ eliminujeme nějakou proměnnou - je konečný
	- Pokud skončí neúspěchem, nelze unifikovat $S_{k}$, pak ani $S$
	- Pokud odpoví $\sigma=\sigma_{0}\sigma_{1},\dots \sigma_{k}$, jde o unifikaci
	- Je nejobecnější = lze z ní získat libovolnou jinou unifikaci:
		- (indukcí) $0 \leq i \leq k$: $$\tau=\sigma_{0}\sigma_{1}\dots \sigma_{i}\tau$$
		- Pro $i=1$, $\sigma_{0}=\emptyset$, $\tau=\sigma_{0} \tau$ platí
		- Pro $i+1$: nechť $\sigma_{i+1}=\{x/t\}$, stačí dokázat, že pro libovolnou proměnnou $u$ platí: $$u \sigma_{i+1} \tau=u \tau$$
			- je-li $u\neq x$, pak $u \sigma_{i+1}=u$, tedy $u \sigma_{i+1}\tau=u \tau$
			- je-li $u=x$, $u \sigma_{i+1}=x \sigma_{i+1} = t$
				- $\tau$ unifikuje množinu $S_{i} = S \sigma_{1}\dots \sigma_{i}$ a proměnná $x$ a term $t$ jsou v neshodě, $\tau$ je musí unifikovat: $t \tau = x \tau$, tedy $u \sigma_{i+1} \tau = u \tau$ $\blacksquare$
