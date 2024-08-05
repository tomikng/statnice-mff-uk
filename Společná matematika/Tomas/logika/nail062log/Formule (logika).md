---
tags:
  - nail062log
---
**Atomická formule** jazyka $L$
- nápis $R(t_{1},\dots, t_{n})$, pro $n$-ární relační symbol $R$ (včetně =) a $t_{i}\in Term_{L}$
- často s infixovým zápisem ($=(x,y)$ jako $x = y$)
- je otevřená

**Formule** jazyka $L$
- induktivně:
	- každá atomická formule jazyka $L$ je formule
	- $\neg \varphi$ formule $\varphi$ je formule
	- $\varphi \square \psi$ formulí $\varphi,\psi$ je formule
	- $(Q x) \varphi$ formule $\varphi$ je formule, $Q \in \{\forall, \exists\}$
- Podformule - podřetězec, který je formulí
- $Tree(\varphi)$ - strom formule, kvantifikátor má stejnou prioritu jako negace (vyšší než ostatní spojky)
- **Výskyt proměnné** - list stromu formule
	- **vázaný** - je v podstromu kvantifikátoru, jinak je **volný**
	- proměnná je vázaná/volná v $\varphi$, pokud má takový výskyt v $\varphi$ (může být oboje zároveň)
	- $\varphi(x_{1},\dots,x_{n})$ - x1-xn jsou všechny volné proměnné $\varphi$
- **Otevřená formule** - neobsahuje kvantifikátor
	- kombinace atomických formulí pomocí spojek
- **Uzavřená formule** (**sentence**) - nemá volné proměnné
	- sentence má v konkrétní struktuře pravdivostní hodnotu

**Substituovatelnost** $\varphi(x/t)$ proměnné x za term t
- pokud nahrazením všech volných výskytů $x$ nevznikne vázaný výskyt proměnné z $t$
	- $t$ není substituovatelný za x v $\varphi$ <=> x má volný výskyt v podformuli $(Qy)\psi$, $y\in Var(t)$
- **instance** - formule po substituci
- **varianta** - formule $\varphi$ má podformuli $(Qx)\psi$
	- $y$ je substituovatelná za $x$ do $\psi$
	- $y$ nemá v $\psi$ volný výskyt (přejmenovávání proměnné)
	- také výsledek postupné variace ve více podformulích