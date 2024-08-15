---
tags:
  - nail062log
---
**(P22) Izomorfismus struktur, izomorfní spektrum, ω-kategorická teorie.**
- **Izomorfismus** struktur $\mathcal{A}, \mathcal{B}$ jazyka $L$:
	- Značíme $\mathcal{A} \simeq_{h} \mathcal{B}$
	- Bijekce $h: A \to B$:
		- Pro každý $f \in \mathcal{F}$ pro všechná $a_{i}\in A$ platí: $$h(f^\mathcal{A}(a_{1},\dots,a_{n}))=f^\mathcal{B}(h(a_{1}),\dots,h(a_{n}))$$
			- Speciálně $h(c^\mathcal{A})=c^\mathcal{B}$
		- Pro každý $R \in \mathcal{R}$ pro všechna $a_{i}\in A$ platí: $$R^{\mathcal{A}(a_{1},\dots,a_{n})}\Leftrightarrow R^\mathcal{B}(h(a_{1}),\dots,h(a_{n}))$$
- **Automorfismus** - izomorfismus $\mathcal{A}$ na $\mathcal{A}$
- Tvrzení (o skládání bijekce s ohodnocením):
	- Bijekce $h: A \to B$ je izomorfismus právě tehdy když:
		- Pro každý L-term $t$ a ohodnocení $e: Var \to A$: $$h(t^\mathcal{A}[e])=t^\mathcal{B}[e\circ h]$$
		- Pro každou L-formuli $\varphi$ a ohodnocení $e: Var \to A$: $$\mathcal{A} \models \varphi[e] \Leftrightarrow \mathcal{B}\models \varphi[e \circ h]$$
	- Důkaz:
		- je-li $h$ isomorfismus, lze dokázat indukcí dle struktury termu
		- je-li $h$ bijekce splňující tyto 2 vlastnosti, dosazením $f^\mathcal{A}$ a $R^\mathcal{A}$ dostaneme původní definici izomorfismu
	- Důsledek:
		- $\mathcal{A}\simeq \mathcal{B} \Rightarrow \mathcal{A}\equiv \mathcal{B}$
		- opačná implikace neplatí pro nekonečné struktury

**(T12) Vztah izomorfismu a elementární ekvivalence.**
- Pro $L_{=}$ a konečné struktury platí: $$\mathcal{A}\simeq \mathcal{B} \Leftrightarrow \mathcal{A}\equiv \mathcal{B}$$
- Důkaz ($\impliedby$):
	- Dokážeme, že existuje izomorfismus $\mathcal{A}$ na $\mathcal{B}$
	- Bijekce: díky rovnosti vyjádříme sentencí, že "existuje právě n prvků", tj. $|A|=|B|$
	- Expanzi $\mathcal{A}$ o jména prvků z $\mathcal{A}$ označíme $\mathcal{A}'$, přidáme konstantu pro každý prvek
	- Ukážeme, že $\mathcal{B}$ lze expandovat na L'-strukturu $\mathcal{B'}$, t.ž. $\mathcal{A}'=\mathcal{B}'$
	- Konkrétná prvek $a \in A$ zajišťuje platnost určitých sentencí, ty definují zobrazení $a \to B$
- Důsledek:
	- Pokud má kompletní teorie v $L_{=}$ konečný model, jsou všechny izomorfní

 **(L7) Vztah definovatelných množin a automorfismů.**
 - automorfismus je "přejmenování" prvků se zachováním vlastností (např. izolovaný vrchol na izolovaný)
 - Je-li $D \subseteq A^{n}$ definovatelná ve struktuře $\mathcal{A}$, pak pro každý automorfismus $h \in Aut(\mathcal{A})$ platí $h[D]=D$
	 - $h[D]=\{h(\bar{a})|\bar{a} \in D\}$ - množina všech výsledků bijekce pro každou n-tici struktury
 - Je-li $D$ definovatelná s parametry $\bar{b}$, platí totéž pro automorfismy identické na $\bar{b}$, tj. $h(\bar{b})=\bar{b}$
 - Důkaz:
	 - $D=\varphi^\mathcal{A, \bar{b}}(\bar{x},\bar{y})$, pak pro každé $\bar{a}\in A^{n}$ platí:
	 - <=> $\mathcal{A}\models \varphi[e(x/a,y/b)]$
	 - <=> $\mathcal{A}\models \varphi[(e \circ h)(x/a,y/b)]$ - z vlastností izomorfismu
	 - <=> $\mathcal{A}\models \varphi[(e)(x/h(a),y/h(b))]$
	 - <=> $\mathcal{A}\models \varphi[(e)(x/h(a),y/b)]$ - protože b je identita
	 - <=> $h(a) \in D$

**Izomorfní spektrum** teorie $T$, $\kappa$-kategoricita
- Počet $I(\kappa,T)$ modelů $T$ kardinality $\kappa$ až na izomorfismus pro každou kardinalitu $\kappa$
	- $\kappa$ - $|A|$, rozměr domény modelu
	- $I(\kappa,T)$ - počet modelů teorie s tímto rozměrem domény (až na izomorfismus)
- Teorie je $\kappa$-kategorická, pokud $I(\kappa,T)=1$
- $\kappa=\omega$ - teorie s jediným spočetně nekonečným modelem až na izomorfismus
- Tvrzení: DeLo\* je $\omega$-kategorická
	- Důkaz (indukcí):
		- Vezměme 2 spočetně nekonečné modely A,B a očíslujeme jejich prvky
		- Indukcí podle $n$ lze díky hustotě nalézt posloupnost prostých funkcí A->B, t.ž. zachováme uspořádání
		- Pak $\mathcal{A} \simeq \mathcal{B}$ via $h=\bigcup_{n\in \mathbb{N}}h_{n}$
	- Důsledek:
		- Izomorfní spektrum teorie DeLO\* je 0 pro $\kappa \in \mathbb{N}$ a 4 pro $\kappa=\omega$
		- Spočetné modely až na izomorfismus jsou např. $\mathbb{Q}=\langle Q, \leq \rangle \simeq$ restrukce na (0,1), na (0,1\], na \[0,1) a na \[0,1\]

**$\omega$-kategorické kritérium kompletnosti**
- zeslabění kompletnosti
- T je kompletní, je-li
	- L bez rovnosti
	- nebo L s rovností a T nemá konečné modely
- Důkaz:
	- bez rovnosti:
		- Löwenheim-Skolemova věta - každý model je elementárně ekvivalentní nějakému spočetně nekonečnému
		- ten je až na izomorfismus jediný, všechny jsou ee, semantická definice kompletnosti
	- s rovností:
		- všechny nekonečné modely jsou elementárně ekvivalentní
		- zakázali jsme konečné modely (potenciálně elementárně neekvivalentní)
- Důsledek:
	- všechny kompletní jednoduché extenze DeLO jsou kompletní