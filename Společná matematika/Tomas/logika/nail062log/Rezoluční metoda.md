---
tags:
  - nail062log
---
## Výroková logika
Pravidlo řezu
$$\frac{\varphi \vee \psi,\neg \varphi \vee \chi}{\psi \vee \chi}$$

**Ohodnocení** $\mathcal{V}$
- Modely odpovídají množinám literálů, např. $\mathcal{V}=\{p_{1},\neg p_{2},\neg p_{3}\}$
- Libovolná množina literálů, která neobsahuje dvojici opačných literálů (je konzistentní)
- **Úplné ohodnocení** - obsahuje pozitivní/negativní literál pro každou výrokovou proměnnou
- **Splňující ohodnocení** $\mathcal{V} \models S$ - obsahuje nějaký literál z každé klauzule v $S$: $$\mathcal{V} \cap C \neq \emptyset \text{ pro každou } C\in S$$

**Rezoluční pravidlo**
- Rezolventa $C$ klauzulí $C_{1}$ a $C_{2}$ přes literál $l$: $$C = (C_{1} \backslash \{l\})\cup(C_{2} \backslash \{\bar{l}\})$$
- Korektnost pravidla - pokud ohodnocení splňuje $C_{1}$ a $C_{2}$, pak splňuje i jejich rezolventu $C$ 

**Rezoluční důkaz**
- Odvození klauzule $C$ z formule $S$, $$S \vdash_{R}C$$
- Posloupnost klauzulí $C_{0},C_{1},\dots=C$ t.ž. každá klauzule je rezolventou nějakých dvou předchozích
- **Rezoluční zamítnutí** - rezoluční důkaz prázdné klauzule (sporu) u $S$, S je zamítnutelná

**Rezoluční strom** klauzule $C$ z formule $S$
- Konečný binární strom, vrcholy jsou klauzule
- Kořen je $C$, v listech jsou klauzule z $S$, vnitřní vrcholy jsou rezolventy ze svých synů
- Klauzule má strom <=> $S \vdash_{R}C$ : každý důkaz má jednoznačný strom, ale z jednoho stromu získáme více důkazů procházkou

**Rezoluční uzávěr** $\mathcal{R}(S)$
- Induktivně definován jako nejmenší množina klauzulí:
	- Každá klauzule formule je v uzávěru $C \in \mathcal{R}(S)$ pro všechna $C \in S$
	- Jsou-li C1 C2 v uzávěru a C je rezolventou, pak je také v uzávěru

## Korektnost a úplnost rezoluční metody
**(L10) Věta o korektnosti rezoluce ve výrokové logice.**
- Je-li $S$ zamítnutelná, pak je nesplnitelná
- Důkaz:
	- nechť $S \vdash_{R} \square$ a vezměme důkaz $C_{0},\dots,C_{n}=\square$
	- pro spor nechť $S$ je splnitelná, tzn. má splňující ohodnocení $\mathcal{V} \models S$
	- indukcí podle $i$ dokážeme $\mathcal{V}\models C_{i}$:
		- pro i=0 platí, protože $C_{0} \in S$ a $\mathcal{V}\models S$
		- pro i>0:
			- $C_{i}\in S$, pak ohodnocení splňuje i Ci - $\mathcal{V}\models C_{i}$
			- $C_{i}$ je rezolventou předchozách klauzulí, pro obě platí z ip, že $\mathcal{V}$ je splňuje, takže $\mathcal{V} \models C_{i}$
		- indukcí dojdeme k $\mathcal{V}\models \square$, což je spor

**(L12) Souvislost stromu dosazení a splnitelnosti CNF formule.**
- Splnitelnost konečné formule $S$ zjistíme rekurzivně, dosazením obou literálů pro některý prvovýrok $p$ a rozvětvením na $S^{p}, S^{\overline{p}}$, jako v DPLL, pak máme strom dosazení
- Dosazení - zjednodušení za předpokladu platnosti literálu (jako jednotková propagace)
- $S^{l}=\{C \backslash \{\bar{l}\}|l \not\in C \in S\}$
	- $S^{l}$ je výsledek jednotkové propagace na $S \cup \{\{l\}\}$
	- Neobsahuje prvovýrok z $l$
	- Pokud $S$ neobsahovala tyto literály, pak $S^{l}=S$
	- Pokud $S$ obsahovala jednotkovou klauzuli $\{\mathcal{\bar{l}}\}$, pak $\square \in S^{l}$ a je sporná
- Rekurzivní dosazení obou možných literálů pro proměnnou z formule s rozvětvením výpočtu
- Lemma: $S$ je splnitelná <=> splnitelná $S^{l}$ nebo $S^{\bar{l}}$
	- Důkaz:
	- $\implies$
		- Ohodnocení $\mathcal{V} \models S$, nemá opačné literály
		- BÚNO $\bar{l} \not\in \mathcal{V}$
		- Vezměme klauzuli z $S^{l}$, $C \backslash \{\bar{l}\}$ pro $C\in S$, která neobsahuje $l$
		- $\mathcal{V} \models C$, protože splňuje všechny klauzule z $S$
		- $\mathcal{V}$ neobsahuje $\bar{l}$, takže splnilo nějaký jiný literál $C$ a můžeme ho vynechat, $\mathcal{V} \models C \backslash \{\bar{l}\}$
	- $\impliedby$
		- BÚNO existuje ohodnocení $\mathcal{V}\models S^{l}$
		- $\bar{l}$ se nevyskytuje v $S^{l}$, takže ohodnocení $\mathcal{V}$ splňuje $S^{l}$ i bez něj
		- Ohodnocení $\mathcal{V}'=(\mathcal{V}\backslash \{\bar{l}\})\cup \{l\}$ splňuje každou $C\in S$
			- pokud $l\in C$, klauzule je splněná tímto ohodnocením
			- pokud $l \not\in C$, pak $\mathcal{V}\backslash \{\bar{l}\}\models C \backslash \{\bar{l}\}\in S^{l}$
- Tvrzení: Formule $S$ nad spočetným jazykem je nesplnitelná <=> každá větev stromu dosazení obsahuje prázdnou klauzuli $\square$
	- Důkaz:
	- Pro konečnou indukcí dle počtu proměnných dle lemmatu
	- Pro nekonečnou
		- Je-li $S$ nekonečná a splnitelná, má splňující ohodnocení $\mathcal{V}$
		- To se shoduje s nekonečnou větví ve stromu dosazení
		- Je-li $S$ nekonečná a nesplnitelná, pak dle věty o kompaktnosti má konečnou nesplnitelnou část $S'\subseteq S$
		- Po dosazení bude v každé větvi $\square$ po konečně mnoha krocích

**(T6) Věta o úplnosti rezoluce ve výrokové logice.**
- Je-li $S$ nesplnitelná, je rezolucí zamítnutelná
- Důkaz (indukcí dle proměnných v $S$):
	- Je-li nekonečná, má z Věty o kompaktnosti konečnou nesplitelnou část $S'$, proto předpokládáme konečnou $S$
	- Je-li $|Var(S)|=0$, jediná možná nesplnitelná formule je $S=\{\square\}$ a máme jednokrokový důkaz $S \vdash_{R} \square$
	- Jinak vybere $p \in Var(S)$ a dle lemmatu jsou $S^{p}$ a $S^{\overline{p}}$ nesplnitelné a máme o 1 proměnnou méně, existují rezoluční stromy $T$ pro $S^{p}\vdash \square$ a  $S^{\overline{p}}\vdash \square$
	- Umíme ze stromu T vyrobit $\hat{T}$ pro $S \vdash_{R} \neg p$ analogicky pro $\hat{T}'$ a $p$
	- todo: zbytek

## Predikátová logika
Ekvisplnitelnost
- Ne každá teorie je ekvivalentní CNF formuli
- Formule jsou ekvisplnitelné: $\varphi$ je nesplnitelná <=> $\psi$ je nesplnitelná
- Skolemizace - hledání ekvisplnitelné CNF formule nahrazením $\exists$ kvantifikovaných proměnných konstantními/funkčními symboly
	- např. $(\exists x)\psi(x)$ nahradíme $\psi(x/c)$, $c$ reprezentuje splňujícího svědka
	- ztrácíme ekvivalenci, protože splňujících prvků může být mnoho, ale $\psi(x/c)$ je splnitelná právě když byla původní $(\exists x)\psi(x)$
- Ekvisplnitelné teorie, ne nutně ve stejném jazyce:$$\text{T má model} \Leftrightarrow \text{T' má model}$$
1. Převod do PNF (vytýkání kvantifikátorů)
2. Nahrazení formulí generálními uzávěry (ať máme sentence)
3. Skolemizace (odstránění existenčních kvantifikátorů)
4. Generalizace (odstránění zbývajících univerzálních kvantifikátorů) -> otevřené formule

[[Prenexní normální forma]]

Základní instance (ground)
- Pro otevřenou formuli $\varphi$ je instance $\varphi(x_{1}/t_{1},\dots,x_{n}/t_{n})$ je základní, jsou-li všechny temry konstantní

**(T10) Herbrandova věta.**
- Herbrandův model - $\mathcal{A}=\langle A,\mathcal{R}^{\mathcal{A}},\mathcal{F}^{\mathcal{A}}\rangle$
	- $A$ je množina všech konstantních $L$-termů
	- $f^{\mathcal{A}}$("t1",..."tn")="f(t1,...,tn)"
	- $c^{\mathcal{A}}=$ "c"
	- např, funkce splňuje f("c","c")="f(c,c)" (hodnota konstantního řetězce je stejná jako hodnota funkce s konstantními podřetězcemi)
	- na rozdíl od kanonického modelu nepřidáváme nové konstantní symboly (vycházíme z existujících) a nedefinujeme relace
- Pro otevřenou teorii $T_{L}$ bez rovnosti s alespoň jedním konstantním symbolem, buď $T$ má Herbrandův model nebo existuje konečně mnoho základních instancí axiomů $T$, jejichž konjunkce je nesplnitelná
	- Má-li model, má i Herbrandův model nebo najdeme nesplnitelnou konjunkci základních instancí axiomů
	- Důkaz:
		- $T_{ground}$ - množina základních instancí axiomů $T$
		- Zkonstruujeme systematické tablo z $T_{ground}$ s položkou $F \bot$ v kořeni, ale bez rozšíření na $L_{C}$ (protože v $T_{ground}$ nejsou kvantifikátory, nepotřebujeme je)
		- Pokud tablo obsahuje bezespornou větev, pak je kanonický model Herbrandovým modelem $T$
		- Jinak máme tablo-důkaz sporu a $T_{ground}$ a $T$ jsou nesplnitelné
			- Najdeme konečně mnoho základních instancí $\alpha_{ground} \in T_{ground}$, jejíchž konjunkce je nesplnitelná $\blacksquare$
	- Pro jazyk s rovností, nejprve rozšíříme $T$ o axiomy rovnosti na $T^{*}$ a má-li Herbrandův model $\mathcal{A}$, faktorizujeme dle kongruence $=^\mathcal{A}$ stejně jako pro kanonický model dle výskytů vnořených "f"
- Důsledky:
	- Nechť $\varphi$ je otevřená formule v $L$ s alespoň 1 konstantním symbolem
		- Pak existují konstantní termy $t_{ij}$, t.ž.$$(\exists x_{1})\dots(\exists x_{n})\varphi(x_{1},\dots,x_{n}) \Leftrightarrow \varphi(x_{1}/t_{11},\dots,x_{n}/t_{1n}) \vee \dots \vee \varphi(x_{1}/t_{m1},\dots, x_{n}/t_{mn})$$
		- Herbrandova věta aplikovaná na teorii $T=\{\neg \varphi\}$, $\varphi$ je sentence
	- Pro otevřenou teorii $T$ v $L$s alespoň 1 konstantním symbolem,
		- $T$ má model <=> $T_{ground}$ má model
		- v $T$ platí všechny axiomy <=> platí jejich základní instance
		- pokud $T$ nemá model <=> dle Herbrandovy věty je nějaká konečná podmnožina $T_{ground}$ nesplnitelná


**Rezoluční pravidlo**
- Klauzule $C_{1} = C_{1}' \sqcup \{A_{1},\dots,A_{n}\}, C_{2}=\dots \{\neg B_{1},\dots \neg B_{n}\}$ s disjunktními množinami proměnných, kde množinu výrazů lze unifikovat
	- disjunktní množiny proměnných musí být splněné pro přejmenování v jedné z klauzulí
- $S = \{A_{1,\dots,n},\dots,B_{1,\dots,m}\}$
- $\sigma$ je nejobecnější unifikace $S$
- Rezolventa: $$C = C_{1}'\sigma\cup C_{2}'\sigma$$
[[Unifikační algoritmus]]

**Rezoluční důkaz**
- Odvození klauzule $C$ z formule $S$
- Konečná posloupnost klauzulí $C_{0},\dots,C_{n}=C$, t.ž.
	- $C_{i} = C_{i}' \sigma$ pro nějakou klauzuli $C_{i}'\in S$
	- $C_{i}$ je rezolventou nějakých $C_{j},C_{k}$, kde $j,k<i$
- Rezuluční zamítnutí: $S \vdash_{R} \bot$
- V rezolučním kroku v PL potřebujeme odstránit více literálů najednou

**(L11) Věta o korektnosti rezoluce v predikátové logice.**
- Platí-li v struktuře $\mathcal{A}$ $C_{1}, C_{2}$, platí v ní i $C$
- Důkaz (z definice):
	- Víme, že klauzule a jejích rezolventu vyjádříme jako disjunktní sjednocení $C_{1} = C_{1}' \sqcup \{A_{1},\dots,A_{n}\}, C_{2}=\dots \{B_{1},\dots B_{m}\}$
	- $C = C_{1}' \sigma \cup C_{2}'\sigma$ pro nejobecnější unifikaci $\sigma$
	- $C_{1},C_{2}$ jsou otevřené formule platné v $\mathcal{A}$, platí i jejich instance po substituci, tedy $\mathcal{A} \models C_{1} \sigma$ a $C_{2}\sigma$
	- $C_{1} \sigma = C_{1}'\sigma \cup \{A_{1} \sigma\}$ a $C_{2} \sigma = C_{2}'\sigma \cup \{\neg A_{1} \sigma\}$
	- Cílem je $\mathcal{A}\models C[e]$, pro libovolné ohodnocení $e$
		- Nechť $\mathcal{A} \models A_{1} \sigma[e]$, pak  $\mathcal{A} \not\models \neg A_{1} \sigma[e]$ a musí platit $\mathcal{A}\models C_{2}'\sigma[e]$
			- $C_{2}'$ je část formule bez negací $B_{i}$
		- tedy $\mathcal{A}\models C[e]$
- Korektnost rezoluce
	- CNF formule $S$ je rezolucí zamítnutelná => je nesplnitelná
	- Důkaz:
		- Víme, že $S \vdash_{R} \square$, vezměme rezuluční důkaz
		- kdyby existoval model $\mathcal{A} \models S$, díky korektnosti rezolučního pravidla bychom mohli dokázat indukcí dle délky důkazu, že $\mathcal{A} \models \square$, což není možné $\square$

**(T8) Věta o úplnosti rezoluce v predikátové logice (Lifting lemma stačí vyslovit).**
- **Lifting lemma**
	- lze důkaz na úrovni výrokové logiky zvednout na úroveň predikátové
	- pro klauzule $C_{1},C_{2}$ s disjunktními množinami proměnných
	- jsou-li $C_{1}^{*},C_{2}^{*}$ základní instance těchto klauzulí a je-li $C^{*}$ rezolventou $C_{1}^{*},C_{2}^{*}$, pak existuje rezolventa $C$ klauzulí $C_{1},C_{2}$, t.ž. $C^{*}$ je základní instancí $C$
	- Důsledek:
		- Pokud $S^{*}\vdash_{R} C^{*}$pro základní klauzuli $C^{*}$, existuje $C$ a základní substituce $\sigma$ t.ž. $C^{*}=C \sigma$ a $S \vdash_{R} C$
- Je-li CNF formule $S$ nesplnitelná, pak je rezolucí zamítnultelná:
	- Důkaz:
	- díky Herbrandově větě, když $S$ je nesplnitelná, je nesplnitelná i ground $S^{*}$
	- z úplnosti ve vl víme $S^{*}\vdash_{R}\square$ a lifting lemmatu dokážeme $C \sigma = \square$
	- pak ale $C = \square$ a máme rezoluční zamítnutí