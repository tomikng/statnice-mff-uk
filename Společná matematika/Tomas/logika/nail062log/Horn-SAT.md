---
tags:
  - nail062log
---
**Hornovský výrok**
- konjunkce hornovských klauzulí
- hornovská klauzule obsahuje max 1 pozitivní literál
- $$(\neg p_1 \vee \neg p_2 \vee \cdots \vee \neg p_n) \vee q \sim\left(p_1 \wedge p_2 \wedge \cdots \wedge p_n\right) \rightarrow q$$
- jednotková klauzule $l$
	- pozitivní - fakt
	- negativní - cíl
- pravidlo - hornerovský výrok s 1+ pozitivním a 1+ negativním literálem

**Jednotková propagace**
- jednotková klauzule - víme, jak má být ohodnocená (1) a můžeme zjednodušit zbytek
- Klauzule s pozitivním literálem odstráníme, negativní ze zbytku vynecháme: $$\varphi^{l}=\{C \backslash \{l\} \ | \ l \notin C \in \varphi\}$$
- $\varphi^{l}$ neobsahuje ani l, ani ~l
- $M_{\mathbb{P}}(\varphi) = M_{\mathbb{P}}(\{\varphi^{l},l\})$ - modely původního výroku odpovídají modelům výsledného, kde v $\mathbb{P}$ platí l

**Horn-SAT**
- řeši SAT hornovských výroků
- Algoritmus
	1. Pokud $\varphi$ má dvojici jednotkových klauzulí s opačnými literály, máme spor, výrok je nesplnitelný (vznikne prázdná klauzule)
	2. Dokud existuje jednotková klauzule, provedeme jednotkovou propagaci nastavením jejího literálu na 1, nahradíme $\varphi=\varphi^{l}$
	3. Nastavíme zbytek proměnných na 0
- Korektnost
	- Musíme nastavit literál jednotkové klauzule v propagaci jako 1 kvůli konjunkci
	- Výskyt opačných jednotkových klauzulí je spor
	- Nulové ohodnocení musí splnit zbytek <=> máme hornovské výroky s 2+ literály v klauzuli a nejvýš 1 pozitivní
