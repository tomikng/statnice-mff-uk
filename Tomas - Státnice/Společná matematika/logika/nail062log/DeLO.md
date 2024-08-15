---
tags:
  - nail062log
aliases:
  - Husté lineární uspořádání
---
**DeLO\***
- husté [[Lineární uspořádání|lineární uspořádání]]
- axiom linearity $$ x \leq y \vee  y \leq x$$
- axiom hustoty $$ x \leq y \wedge \neg x = y \to (\exists z)(x \leq z \wedge z \leq y \wedge  \neg z =x \wedge \neg z=y)$$
	- Pokud $x$ je ostře menší $y$, pak mezi nimi existuje $z$
- netrivialita $$(\exists x)(\exists y)(\neg x = y)$$
	- zakazuje jednoprvkové modely

 **(L14) Kompletní jednoduché extenze DeLO*.**:
- $\varphi= (\exists x)(\forall y)(x \leq y)$ - existuje minimální prvek
- $\psi= (\exists x)(\forall y)(y \leq x)$ - existuje maximální prvek
- $DeLO=DeLO^{*} \cup \{\neg \varphi, \neg \psi\}$
- $DeLO^{+}=DeLO^{*} \cup \{\neg \varphi, \psi\}$
- $DeLO^{-}=DeLO^{*} \cup \{\varphi, \neg \psi\}$
- $DeLO^{\pm}=DeLO^{*} \cup \{\varphi, \psi\}$
- Důkaz:
	- vyplývá z kompletnosti všech čtyř teorií
	- také z toho, že jsou $\omega$-kategorické (mají jediný spočetný model až na izomorfismus)

**(L15) Existence spočetného algebraicky uzavřeného tělesa.**
- Těleso $\mathcal{A}$ je algebraicky uzavřené, pokud každý polynom nenulového stupně v něm má kořen
	- $\mathbb{R}$ není, protože $x^{2}+1$ nemá kořen v $\mathbb{R}$
	- $\mathbb{C}$ je, ale je nespočetné
	- Algebraická uzavřenost je vyjádřovatelná sentencemi: $$\psi_{n}=(\forall x_{n-1})\dots (\forall x_{0})(\exists y)(y^{n}+x_{n-1} \cdot y^{n-1}+\dots+x_{1} \cdot y + x_{0})=0$$
- Důsledek: existuje spočetné algebraicky uzavřené těleso
- Důkaz: existuje spočetně nekonečná struktura $\mathcal{A}$ elementárně ekvivalentní $\mathbb{C}$ z Löwenheim-Skolemové věty
	- je-li L spočetný jazyk s rovností, pak každá bezesporná L-teorie má spočetný model 