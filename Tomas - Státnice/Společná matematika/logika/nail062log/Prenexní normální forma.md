---
tags:
  - nail062log
---
**(P21) Prenexní normální forma, Skolemova varianta.**
- Formule je v **PNF**, když všechny kvantifikátory jsou před výrazem:$$(Q_{1\dots n} x_{1\dots n}) \varphi'$$
	- $\varphi'$ je otevřené jádro, zbytek je kvantifikátorový prefix
	- Ke každé formuli $\varphi$ existuje ekvivalentní v PNF: $$\begin{aligned} \neg(Q x) \varphi & \sim(\bar{Q} x) \neg \varphi \\ (Q x) \varphi \wedge \psi & \sim(Q x)(\varphi \wedge \psi) \\ (Q x) \varphi \vee \psi & \sim(Q x)(\varphi \vee \psi) \\ (Q x) \varphi \rightarrow \psi & \sim(\bar{Q} x)(\varphi \rightarrow \psi) \\ \psi \rightarrow(Q x) \varphi & \sim(Q x)(\psi \rightarrow \varphi)\end{aligned}$$
		- po vytknutí antecedentu musíme změnit kvantifikátor, viz $a \rightarrow b \Leftrightarrow \neg a \vee b$
- **Skolemova varianta**
	- Pro $L$-sentenci $\varphi$ v PNF s různými vázanými proměnnými
	- Nechť existenční kvantifikátory z prefixu jsou $(\exists y_{1}),\dots,(\exists y_{n})$
	- Nechť pro každé $i$ jsou $(\forall x_{1}),\dots,(\forall x_{n_{i}})$ všechny univerzální kvantifikátory předcházejícíc $(\exists y_{i})$
	- $L'$ je rozšíření $L$ o nových $f_{1},\dots,f_{n}$ funkčních symbolů, kde $f_{i}$ je arity $n_{i}$
	- Skolemova varianta je $\varphi_{S}$, která vznikne z $\varphi$ pro každé $i=1,\dots,n$:
		- odstráníme z prefixu $(\exists y_{i})$
		- substitujeme $f_{i}(x_{1},\dots,x_{n})$ za proměnnou $y_{i}$
	- Lemma: $\varphi=(\forall x_{1}),\dots,(\forall x_{n})(\exists y)\psi$, $\varphi'=(\forall x_{1}),\dots,(\forall x_{n})\psi(y/f(x_{1},\dots,x_{n}))$
		- $L$-redukt každého modelu $\varphi'$ je modelem $\varphi$
		- každý model $\varphi$ lze expandovat na model $\varphi'$
		- Důkaz:
			- Redukt $\mathcal{A'}\models \varphi'$ na model $\mathcal{A}$ splňuje $\varphi$, protože $\mathcal{A}\models \psi[e(y/a)]$ platí pro každé ohodnocení $e$, včetně $a=f(x_{1},\dots,x_{n})^\mathcal{A'}[e]$
			- Model $\mathcal{A} \models \varphi$ lze expandovat na $\mathcal{A}'$ funkcí $a=f^{A}: A^{n}\to A$, která splňuje každé ohodnocení $\mathcal{A}\models \psi[e(y/a)]$
		- Důsledek:
			- $\varphi$ a $\varphi_{S}$ jsou ekvisplnitelné

**(T9) Skolemova věta.**
- Každá teorie má otevřenou konzervativní extenzi
- Důkaz:
	- Máme $T_{L}$, každý axiom nahradíme generálním uzávěrem, není-li už sentence a převedeme do PNF => Máme ekvivalentní $T'_{L}$.
	- Nahradíme každý axiom Skolemovou variantou => Máme ekvisplnitelnou $T''_{L'}$.
	- Z lemmatu $L$-redukt každého modelu $T''$je modelem $T'$ a každý model $T'$ lze expandovat do $L'$ => je konzervativní
	- Odstraníme-li univerzální sentence z $T''$, máme otevřenou ekvivalentní $T'''$, tedy konzervativní extenzi $T$
- Důsledek:
	- Ke každé teorii najdeme skolemizací ekvisplnitelnou otevřenou teorii
