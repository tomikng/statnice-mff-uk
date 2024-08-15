---
tags:
  - nail062log
aliases:
  - Výroková funkce
---
## Výroková logika
Pravdivostní hodnota
- 0/1, přiřazuje se prvovýroku (výrokové proměnné)

**Pravdivostní funkce**
$$f_{\varphi,\mathbb{P}}: \{0,1\}^{|\mathbb{P}|}\to \{0,1\}$$
- $f_{\neg}(x)=1-x$
- $f_{\square}(x,y)$
- induktivně definovaná funkce výroku $\varphi$, má na vstupu vyhodnocení proměnných jazyka a na výstupu jednu pravdivostní hodnotu
	- je-li $\varphi$ i-tý prvovýrok, vrátí jeho vyhodnocení $$f_{\varphi,\mathbb{P}}(x_{0},\dots,x_{n-1})=x_{i}$$
	- je-li $\varphi$ ve tvaru $\neg \varphi'$, pak $$f_{\varphi,\mathbb{P}}(x_{0},\dots,x_{n-1}) =f_{\neg}(f_{\varphi',\mathbb{P}}(x_{0},\dots,x_{n-1}))$$
	- je-li $\varphi$ ve tvaru $\varphi' \square \varphi''$, pak $$f_{\varphi,\mathbb{P}}(x_{0},\dots,x_{n-1})=f_{\square}(f_{\varphi', \mathbb{P}}(x_{0},\dots,x_{n-1}),f_{\varphi'', \mathbb{P}}(x_{0},\dots,x_{n-1}))$$
- Výsledek závisí pouze na proměnných použitých ve výroku $Var(\varphi)\subseteq \mathbb{P}$ => Můžeme uvažovat i nad nekonečným jazykem

## Predikátová logika
**Hodnota termu** $t^{\mathcal{A}}[e]$
- term $t$, $L$-struktura $\mathcal{A}=\langle A,\mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}} \rangle$
- **termová funkce** - hodnota termu závisí pouze na ohodnocení proměnných:$$f_{t}^{\mathcal{A}}: A^{k}\to A$$, kde $k$ je počet proměnných
- induktivně:
	- $x^{\mathcal{A}}[e]=e(x)$ pro proměnnou $x\in Var$, 
	- $c^{\mathcal{A}}[e]=c^{\mathcal{A}}$ pro konstantu $c\in \mathcal{F}$
	- $t=f(t_{1,\dots}t_{n})$, pak rekurzivně $$t^{\mathcal{A}}[e]=f^{\mathcal{A}}(t_{1}^{\mathcal{A}}[e],\dots,t_{n}^{\mathcal{A}}[e])$$

**Pravdivostní hodnota** formule $PH^{\mathcal{A}}(\varphi)[e]$
- [[Formule (logika)|formule]] $\varphi$ v jazyce $L$
- [[Model jazyka (logika)#Predikátová logika|struktura]] $\mathcal{A}\in M_{L}$
- ohodnocení $e: Var \to A$
- induktivně
	- Pro atomickou formuli $\varphi=R(t_{1},\dots t_{n})$ $$PH^{\mathcal{A}}(\varphi)[e]=\begin{cases}1 & (t_{1}^{\mathcal{A}}[e], \dots,t_{n}^{\mathcal{A}}[e])\in R^{\mathcal{A}}\\0 & \text{jinak}\end{cases}$$
		- 1, pokud výsledné prvky termů jsou v relaci
	- Pro negaci $$PH^{\mathcal{A}}(\neg\varphi)[e]=f_{\neg}(PH^{\mathcal{A}}(\varphi)[e]) = 1-PH^{\mathcal{A}}(\varphi)[e]$$
		- viz pravdivostní hodnota ve VL
	- Pro spojky $$PH^{\mathcal{A}}(\varphi \square \psi)[e]=f_{\square}(PH^{\mathcal{A}}(\varphi)[e],PH^{\mathcal{A}}(\psi)[e])$$
	- Pro kvantifikátory $$\begin{align*}
PH^{\mathcal{A}}((\forall x )\varphi)[e] = \min_{\alpha\in A}(PH^{\mathcal{A}}(\varphi)[e(x/a)])\\PH^{\mathcal{A}}((\exists x )\varphi)[e] = \max_{\alpha\in A}(PH^{\mathcal{A}}(\varphi)[e(x/a)])
\end{align*}$$
		- změnou ohodnocení $x$ za prvek domény, $e(x/a)(x)=a$ postupně nastavíme hodnotu pro všechny prvky $a$ a chceme, ať je vždy 1 (min 1) nebo alespoň jednou (max 1)
		- konjunkce/disjunkce přes všechny prvky struktury
