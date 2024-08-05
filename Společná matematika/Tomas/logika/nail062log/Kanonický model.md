---
tags:
  - nail062log
---
## Výroková logika
**Kanonický model**
- je-li V bezesporná větev dokončeného tabla, pak je kanonický model definován pro $p \in \mathbb{P}$: $$v(p)=\begin{cases}1 \text{ pokud se na V vyskytuje Tp} \\
0 \text{ jinak}\end{cases}$$
- KM pro bezespornou dokončenou větev $V$ se s ní shoduje
	- Důkaz: 
	- shoduje se se všemi položkami P na větvi V indukcí dle struktury výroku v položce
	- Pro prvovýroky: základ indzkce, z definice
		- $P=Tp \Leftrightarrow v(p)=1$
		- $P=Fp \Leftrightarrow v(p)=0$
	- Pro složené výroky: z definice atomických tabel
		- $P=T \varphi \wedge \psi$ - na dokončené větvi jsou položky $T \varphi$ a $T \psi$, $v \models \varphi$ a $v \models \psi$
			- => $v \models \varphi \wedge \psi$
		- $P = F \varphi \wedge \psi$ - na dokončené větvi je buď $F \varphi$ nebo $F_\psi$, tedy $v \not\models \varphi$ nebo $v\not\models \psi$ 
			- => $v \not\models \varphi \wedge \psi$

## Predikátová logika
**Kanonický model** (PL)
- Teorie $T$ v jazyce $L=\langle \mathcal{F},\mathcal{R}\rangle$, $V$ je bezesporná větev dokončeného tabla
- Kanonický model je $L_{C}$ struktura $\mathcal{A}=\langle A, \mathcal{F}^{\mathcal{A}} \cup C^{\mathcal{A}}, \mathcal{R}^{\mathcal{A}}\rangle$ s novými konstantami=řetězcí
	- $A$ je množina všech konstantních $L_{C}$-termů
	- Pro každý $R \in \mathcal{R}$ a "s1",...,"sn" z $A$:
		- Termy jsou v relacy <=> relace leží na větvi $V$ s T
		- ("s1",...,"sn") jsou v relaci $R$ <=> na větvi $V$ je položka $T R(s_{1},\dots,s_{n})$
	- Pro každý $f \in \mathcal{F}$ a "s1",...,"sn" z $A$:
		- `f("a","b")="f(a,b)"`
		- $f^\mathcal{A}($"s1",...,"sn"$)$  <=> na větvi $V$ je položka $T f(s_{1},\dots,s_{n})$
		- $c^\mathcal{A}=$"c"
	- Pro jazyk s rovností, $\mathcal{B}$ pro $L$ bez rovnosti s  $=^{B}$
		- Pro každou formuli $$\varphi: \mathcal{B} \models \varphi \Leftrightarrow \mathcal{A}=\mathcal{B}/_{=^{B}}\models \varphi$$
		- "s1"$=^{B}$"s2" <=> na větvi $V$ je položka $Ts_{1}=s_{2}$
		- $\mathcal{A}=\mathcal{B}/_{=^{B}}$ je pak faktorstruktura, reprezentanti jsou termy s žádným/jedním výskytem $f$
			- `f(["d"])=["f(d)"]=f(["f(d)"])=["f(f(d))"]...`
		- pro jazyk bez rovnosti je spočetně nekonečný
		- pro jazyk s rovností musí být konečný