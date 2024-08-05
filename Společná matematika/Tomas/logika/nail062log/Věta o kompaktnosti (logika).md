---
tags:
  - nail062log
---
**(L9) Věta o kompaktnosti a její aplikace.**
- Teorie má model <=> Každá její konečná část má model
- Důkaz:
	- $\Leftarrow$: Model T je zjevně modelem každé její části: $M(T)\subseteq M(\varphi)$, $\varphi\in T$
	- $\Rightarrow$: obměnou: pokud T nemá model, existuje konečná část, která nemá model
		- T nemá model = je sporná = $T \vdash \bot$ (Věta o úplnosti)
		- existuje konečný tablo důkaz $\tau$ výroku $\bot$ z T
		- jeho konstrukce má konečný počet kroků, použili jsme konečně mnoho axiomů z $T$, které vyjádříme jako $T' \subseteq T$
		- => $T'$ je sporná konečná část $T$
- tldr: T nemá model = je sporná = lze najít konečný tablo důkaz sporu = vezměme použité v něm axiomy z T jako T': teorie má model => každá konečná část má model
- Aplikace:
	- Popíšeme vlastnost nekonečného objektu pomocí nekonečné výrokové teorie
	- Z konečné části sestrojíme objekt, který tuto vlastnost má
	- např. spočetně nekonečný graf je bipartitní <=> každý jeho konečný podgraf je bipartitní

Věta o kompaktnosti (kratší verze)
- Teorie má model <=> každá konečná část má model
- Důkaz:
	- Model celé teorie je modelem každé její části
	- Pokud nemá T model, je sporná a dokazuje spor $T \vdash \bot$
	- Sporné tablo zkonstruujeme konečným počtem axiomů $T' \subseteq T$