---
tags:
  - nail062log
---
**(P23) Axiomatizovatelnost, konečná axiomatizovatelnost, otevřená axiomatizovatelnost.**
- Za jakých okolností lze popsat třídu modelů axiomy nějaké teorie
- Třída struktur $K \subseteq M_{L}$. $K$ je
	- **axiomatizovatelná** - existuje $T_{L}$ t.ž. $M_{L}(T)=K$
	- **konečně** - konečnou teorií
	- **otevřeně** - otevřenou teorií
- Teorie je konečně/otevřeně axiomatizovatelná, pokud o třídě modelů platí $K=M_{L}(T')$
- Je-li $K$ axiomatizovatelná, musí být uzavřená na elementární ekvivalenci
- Příklady:
	- Nekonečné grafy, ČU - konečně i otevřeně
	- Tělesa - konečně, ale ne otevřeně (až na charakteristiku 0)
	- [!] Konečné grafy nejsou axiomatizovatelné

 **(T14) Neaxiomatizovatelnost konečných modelů.**
- Teorie má libovolně velké konečné modely => má nekonečný model
- pak třída všech jejích konečných modelů není axiomatizovatelná
- Důkaz:
	- Pro jazyk bez rovnosti vezměme kanonický model pro bezespornou větev v tablu $T$ pro položku $F\bot$
		- $T$ je bezesporná, má libovolně velké konečné modely, tablo není sporné
		- kanonický model je nekonečný, protože jsme přidali spočetně nekonečně mnoho konstant
	- Pro jazyk s rovností
		- máme extenzi $T'$ teorie $T$ do jazyka rozšířeného o spočetně mnoho konstantních symbolů
		- $T' = T \cup \{\neg c_{i} = c_{j} | i \neq j \in \mathbb{N}\}$ - pro $k$ konstant umíme najít $(k+1)$-prvkový model $T$ a interpretovat konstanty jako navzájem různé prvky
		- každá konečná část $T'$ má model => $T'$ má model, ten je nutně nekonečný
		- jeho redukt na původní jazyk je nekonečným modelem $T$

**(T15) Věta o konečné axiomatizovatelnosti.**
- Pro třídu struktur $K \subseteq M_{L}$ a její doplněk $\overline{K} = M_{L} \backslash K$
- $K$ je konečně axiomatizovatelná <=> $K$ a $\overline{K}$ jsou axiomatizovatelné
- Důkaz:
	- $\implies$
		- je-li $K$ konečně axiomatizovatelná, je axiomatizovatelná $\varphi_{1},\dots,\varphi_{n}$ i konečně mnoha sentencemi (generální uzávěr)
		- lze axiomatizovat $\overline{K}: \psi=\neg(\varphi_{1} \wedge \dots \wedge  \varphi_{n})$
	- $\impliedby$
		- máme-li teorie $M(T)=K$, $M(S)=\overline{K}$, zvážme teorii $T \cup S$
		- ta je sporná, neboť $M(T \cup S)= M(T)\cap M(S) = K \cap \overline{K} = \emptyset$
		- dle věty o kompaktnosti existuje konečná podteorie $T'\subseteq T$ a $S'\subseteq S$, že jejích sjednocení je také sporné:$$\emptyset = M(T'\cup S') = M(T')\cap M(S')$$
		- $$M(T)\subseteq M(T') \subseteq \overline{M(S')}\subseteq \overline{M(S)}=M(T)$$
		- $M(T')$ a $M(S')$ jsou disjunktní, pak $M(T')$ a $\overline{M(S')}$ nejsou a mají průnik
		- $M(T)=M(T')$, teorie $T'$ je hledanou konečnou axiomatizací $K$
- Aplikace:
	- **(L16) Tělesa charakteristiky 0 nejsou konečně axiomatizovatelná.**
		- Charakteristika tělesa $p$ - nejmenší prvočíslo t.ž. $\mathcal{A}\models p1=0$, kde $p1$ je term $1+1+1\dots$ s $p$ jedničkami
		- Charakteristiky 0, pokud není charakteristický $p$ pro žádné prvočíslo $p$
		- Nechť $T$ je třída těles, pak třída těles charakteristiky p je konečně axiomatizována teorií $T= \cup \{p1=0\}$.
		- Pro charakteristiku 0 ale je taková teorie nekonečná: $$T_{0}=T \cup \{p1=0 | \text{p je prvočíslo}\}$$
		- tedy není konečně axiomatizovatelná
		- Důkaz:
			- Díky větě o konečné axiomatizovatelnosti stačí ukázat, že $\overline{K}$ (tělesa nenulové charakteristiky a netělesa) není axiomatizovatelná (sporem)
			- Nechť existuje teorie $S: M(S)=\overline{K}$
				- pak teorie $S'=S\cup T_{0}$ má model, protože každá konečná část má model (udělali jsme $S$ konečnou $S'$)
				- stačí vzít těleso charakteristiky větší než jakékoliv $p$ z $T_{0}$ ve tvaru $\neg p1=0$
			- Nechť $\mathcal{A}$ je model $S'$, pak $\mathcal{A}\in M(S)=\overline{K}$ a zároveň $\mathcal{A} \in M(T_{0})=K$, což je spor $\blacksquare$

**(L17) Kritérium otevřené axiomatizovatelnosti.**
- Teorie $T$ je otevřeně axiomatizovatelná <=> každá podstruktura modelu $T$ je také modelem $T$
- Důkaz ($\implies$)
	- Nechť $T'$ je otevřená axiomatizace $T$, tj. $K=M(T')$
	- Mějme model $\mathcal{A}\models T'$ a $\mathcal{B}\subseteq \mathcal{A}$
	- Pro každou $\varphi\in T'$ platí $\mathcal{B}\models \varphi$, protože $\varphi$ je otevřená (logicky platná), tedy i $\mathcal{B}\models T'$
- Příklad
	- DeLO není OA, žádná konečná podstruktura nemůže být hustá
	- Teorie těles není OA, $\mathbb{Z}\subseteq \mathbb{Q}$ není tělesem, nemá inverzní prvek vůči násobení k 2
	- Teorie grup je OA pro nejvýše $n$-prvkové grupy
