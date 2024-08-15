---
tags:
  - nail062log
---
## Výroková logika
**Strom**
- neprázdný, částečné uspořádání $<_{T}$, kořen je minimální a každá podmnožina předků má nejmenší prvek
- **Větev** - maximální lineárně uspořádaná podmnožina T (nejde přidat další vrcholy, je nejdelší)
- **Uspořádaný strom** - strom + pravolevé uspořádání synů každého vrcholu $<_{L}$
- **Označkovaný strom** - strom + funkce $label: V(T) \Rightarrow Labels$

**Tablo**
- **Položka** - $T \varphi$ nebo $F \varphi$
- Tablo pro položku P - má P v kořeni
- Uspořádaný, položkami označkovaný strom tvořený aplikací následujících pravidel
	- jednoprvkový strom je tablo
	- libovolné položce P na libovolné větvi V lze připojit na konec větve atomické tablo pro položku P
	- na konec libovolné větve můžeme připojit libovolný axiom $\alpha$ teorie T jako  $T \alpha$
- Konečné
- Nekonečné - spočetně mnoho kroků $$\tau = \bigcup_{i\geq 0}\tau_{i}$$
	- $\tau_{0}$ je jednoprvkové tablo
	- $\tau_{i+1}$ vzniklo z $\tau_{i}$ aplikací jednoho z pravidel
	- sjednocení je kvůli přidávání nových vrcholů, $\tau_{i}$ je podstromem $\tau_{i+1}$

**Tablo důkaz**
- sporné tablo z teorie T s položkou $F \varphi$ v kořeni
- $T \vdash \varphi$ - existuje tablo důkaz
- $T \vdash \neg\varphi$ - existuje tablo zamítnutí (sporné tablo s $T \varphi$ v kořeni)
- Položka
	- **redukovaná**
		- buď je olabelovaným prvovýrokem z jazyka P
		- nebo je na větvi kořenem atomického tabla (už jsme ji rozvinuli)
- Větev
	- sporná - obsahuje položky $T \psi$ a $F \psi$ pro nějaký výrok $\psi$, jinak je bezesporná
	- **dokončená**
		- buď je sporná
		- nebo každá položka je redukovaná a obsahuje položku $T \alpha$ pro každý axiom teorie
- Tablo
	- sporné - všechny větve má sporné
	- dokončené - každá větev je dokončená

### Konečnost důkazu
**Systematické tablo**
- Chceme se vyhnout zaseknutí v nekonečné větvi
- Pro teorii T pro položku R je tablo sjednocením $\tau = \bigcup_{i\geq 0}\tau_{i}$:
	- Pro nejlevější položku P v nejmenší úrovni, neredukovanou na bezesporné větvi, která jí prochází:
		- $\tau_{i}'$ = $\tau_{i}$ s připojeným atomickým tablem na každou bezespornou větev procházející P
	- $\tau_{i+1}$ = $\tau_{i}'$ s připojenou $T \alpha_{i+1}$ na každou bezespornou větev. Pokud $i\geq |T|$ (došli nám axiomy teorie), přeskočíme
- Dokončenost:
	- sporné větve vždy dokončíme
	- bezesporné obsahují všechny axiomy T a jsou redukované
		- když P na V není redukovaná, nad ní je konečně mnoho položek a přijde na ní řada (prefix bezesporné V je bezesporný, není nikdy sporný během konstrukce V)

**Königovo lemma**
- Nekonečný, konečně větvící (každý vrchol má konečně mnoho synů) strom má nekonečnou větev

**(T5) Věta o konečnosti sporu, důsledky o konečnosti a systematičnosti důkazů.** ^1f63cb
- Je-li $\tau = \bigcup_{i\geq 0}\tau_{i}$ sporné tablo, pak existuje $n \in \mathbb{N}$ t.ž. $\tau_{n}$ je konečné sporné tablo
- Důkaz:
	- Máme množinu vrcholů $S$ vrcholů stromu $\tau$, které nad sebou ve větvi nemají spor (opačné položky $T \psi, F \psi$)
	- Kdyby $S$ byla nekonečná (tvořila nekonečný strom), má dle Königovo lemmatu nekonečnou větev
	- => měla by nekonečnou bezespornou větev, což je ve sporu se spornosti tabla
	- => existuje hloubka $d \in \mathbb{N}$, která ohraničuje $S$
	- Zvolíme $n$ tak, že $\tau_{n}$ obsahuje první $d+1$ úrovně vrcholů $\tau$, každá větev už je tedy sporná
- Důsledky:
	- Pokud neprodlužujeme sporné větve při konstrujci tabla, je sporné tablo konečné
		- $\tau=\tau_{n}$
	- (Konečnost) Pokud existuje tablo-důkaz $T \vdash \varphi$, existuje konečný tablo-důkaz ^3d9af3
		- při konstrujci $\tau$ ignorujeme kroky, které by prodlužovali spornou větev
	- (Systematičnost) Pokud $T \vdash \varphi$, systematické tablo je konečným tablo-důkazem
		- $T \vdash \varphi \Rightarrow T \models \varphi$ (z Věty o korektnosti)
		- kdyby systematické tablo mělo bezespornou větev, exitoval by protipříklad
### Korektnost a úplnost
Lemma: shoduje-li se model teorie T s položkou v kořeni tabla z teorie T, pak se shoduje s nějakou větvi
- Model se **shoduje** s položkou P <=> ($P = T \varphi$ a $v \models \varphi$) nebo ($P=F \varphi$ a $v \not\models \varphi$)
- Začneme jednoprvkovou větvi $V_{0}$, se kterou se shoduje model $v$ v $\tau_{0}$
- Indukcí podle $i$ (kroků konstrukce tabla) najdeme posloupnost $V_{0}\subseteq V_{1} \subseteq \dots$ t.ž. $V_{i}$ je větev, která se shoduje s modelem $v$ a $V_{i+1}$ je prodloužením $$V=\bigcup_{i\geq 0} V_{i}$$
	- $\tau_{i+1}$ neprodloužilo větev Vi: Vi+1 = Vi
	- $\tau_{i+1}$ vzniklo připojením položky axiomu teorie na konec Vi, pak Vi+1 je prodloužením. V modelu T platí všechny axiomy T, tedy i nová položka
	- $\tau_{i+1}$ vzniklo připojením atomického tabla na konec větve Vi pro položku P. $v$ se shoduje s položkou P, protože je částí větve Vi, pak se shoduje i s kořenem připojeného tabla (=P) a s některou z jeho větví (vzhledem ke struktuře atomických tabel). Definujeme Vi+1 jako prodloužení o libovolnou ze shodných větví.

**Věta o korektnosti**
- Pokud by existoval důkaz a zároveň protipříklad, protipříklad by se musel shodovat s některo větví důkazu, ty jsou ale sporné
- $$T \vdash \varphi \Rightarrow T \models \varphi$$
- Důkaz sporem (dokazatelná, ale neplatí):
	- $\varphi$ neplatí v T, existuje model $v\in M(T)$, kde neplatí $\varphi$
	- $\varphi$ má tablo důkaz, sporné tablo s položkou $F \varphi$ v kořeni
	- Model $v$ se shoduje s položkou $F \varphi$ (je protipříkladem), podle lemmatu se musí shodovat s nějakou větví V
	- Všechny větve včetně V jsou ale sporné - obsahují položky $T \psi$ a $F \psi$, se kterými se model $v$ shoduje. Tedy $v \models \psi \wedge v \not\models \psi$, což je spor.

[[Kanonický model]]

**Věta o úplnosti**
- všechny pravdivé výroky jsou dokazatelné:$$T \models \varphi \Rightarrow T \vdash \varphi$$
- Důkaz: ($\varphi$ platí v $T$, pak je libovolné dokočené tablo z T s položkou $F \varphi$ v kořeni sporné)
	- Kdyby $\varphi$ platil, ale tablo nebylo sporné, má bezespornou dokončenou větev V
	- Větev V je dokončená = obsahuje $T \alpha$ pro všechny axiomy teorie
	- Kanonický model $v$ se shoduje se všemi položkami V, splňuje tedy všechny axiomy T => $v \models T$
	- Ale $v$ se shoduje s $F \varphi$, takže $v \not\models \varphi$ => $T \not\models \varphi$, spor s předpokladem
	- => Tablo muselo být sporné, být důkazem pro platný výrok $\varphi$
- Důsledky:
	- Dokazatelnost = platnost $$Thm_{\mathbb{P}}(T)=\{\varphi\in VF_{\mathbb{P}}| T \vdash \varphi\}$$
	- $$Thm_{\mathbb{P}}(T)=Csq_{\mathbb{P}}(T)$$

## Predikátová logika
$L_{C}$ jazyk
- rozšíření jazyka $L$ o spočetně mnoho pomocných očíslovaných konstantních symbolů $C=\{c_{i}|i\in \mathbb{N}\}$

Položky
- **svědek** - $T (\exists x) \varphi(x)$, $F(\forall x)\varphi(x)$, nahrazujeme $x$ za konstantní symbol $c_{i}\in C$ 
- **všichni** - $T (\forall x) \varphi(x)$, $F(\exists x)\varphi(x)$, nahrazujeme $x$ za konstantní $L_{C}$-term $t_{i}$

**Tablo** (PL)
- $T_{L}$ teorie a $\varphi_{L}$ sentence
- uspořádaný, položkami označkovaný strom zkonstruovaný induktivně:
	- jednoprvkový strom je tablo
	- pro libovolnou položku $P$ na větvi $V$ lze připojit na konec atomické tablo
		- $P$ je svědek - smíme použit jen nový konstantní symbol $c_{i}\in C$, který ještě nebyl na $V$
		- $P$ je všichni - smíme použit libovolný konstantní $L_{C}$ term $t_{i}$
	- na konec libovolné větve lze přidat libovolný axiom $\alpha\in T$

**Tablo důkaz** (PL) sentence $\varphi$
- sporné tablo z $T$ s položkou $F \varphi$ v kořeni
- $T \vdash \varphi$ - výrok teorie je tablo-dokazatelný
- $T \vdash \neg\varphi$ - výrok teorie je tablo-zamítnutelný
- Tablo
	- **sporné** - každá větev je sporná
	- **dokončené** - každá větev je dokončená
- Větev
	- **sporná** - obsahuje položky $T \psi$ a $F \psi$ pro nějakou sentenci $\psi$, jinak **bezesporná**
	- **dokončená** - buď je sporná nebo má každou položku redukovanou a obsahuje položku $T \alpha$ pro všechny axiomy $\alpha\in T$
- Položka
	- **redukovaná** na větvi $V$
		- je ve tvaru $T \psi$ nebo $F \psi$ pro atomickou sentenci $\psi$ (např. R(t1,...,tn)) s konstantními Lc-termy
		- je typu svědek a došlo k jejímu rozvoji na $V$
		- je typu všichni a všechny její výskyty na $V$ jsou redukované
- Výskyt
	- $i$-tý - má $i-1$ předků s touto položkou
	- **redukovaný**
		- položka $P$ má $(i+1)$-ní výskyt na $V$, a zároveň
		- na $V$ se vyskytuje $T \varphi(x/t_{i})$ pro $T(\forall x)\varphi(x)$
			- resp. $F \varphi(x/t_{i})$ pro $F(\exists x)\varphi(x)$
			- museli jsme použit všechny konstantní termy

**Systematické tablo** z teorie $T$ pro položku $R$
- Konečnost - viz [[#^1f63cb|výroková logika]]
- musíme zajistit, abychom použili každou položku, zredukovali každý axiom a substituovali každý Lc term $t_{i}$ za proměnnou v položkách typu všichni
- Tablo $\tau=\bigcup_{i\geq 0}\tau_{i}$
	- $\tau_{0}$ je jednoprvkové $R$
- Pro každé $i \geq 0:$
	- $P$ - položka v nejlevějším vrcholu na co nejmenší úrovní, neredukovaná na bezesporné větvi
	- $\tau_{i}'$ vznikne z $\tau_{i}$ připojením atomického tabla pro $P$ na každou bezespornou věte, která jí prochází
		- $P$ je všichni - má $k$-tý výskyt, pak substitujeme $x/t_{k}$
		- $P$ je svědek - substitujeme $c_{i}\in C$s nejmenším možným $i$ (doposud nevyskytovalo)
		- jinak pokud všechny jsou redukované, pak $\tau_{i+1}=\tau_{i}$
	- $\tau_{i+1}$ vznikne z $\tau'_{i}$ připojením axiomu teorie $T \alpha_{i}$ na každou jeho bezespornou větev, pokud $i \leq |T|$, jinak $\tau_{i+1}=\tau'_{i}$
- Je vždy dokončené
	- pro položky všichni $k$-tý výskyt redukujeme připojením vrcholu s $(k+1)$-ním výžskytem substitucí $t_{k}$
- Poskytje konečný důkaz
	- $T \vdash \varphi \Rightarrow T \models \varphi$

[[Kongruence struktury]]

**(L8) Tablo metoda v jazyce s rovností.**
- $T$ je teorie v jazyce $L_{=}$, pak $T^{*}$ je teorie $T$ s generálními uzávěry axiomů rovnosti pro jazyk $L$ (sentence)
- $\mathcal{A} \models T^{*}$, pak $\mathcal{A}/_{=^{\mathcal{A}}}\models T^{*}$, kde $=^{\mathcal{A}}$ je interpretován jako identita, platí axiomy rovnosti

### Korektnost a úplnost
**(T2) Věta o korektnosti tablo metody v predikátové logice.**
- $$T \vdash \varphi \Rightarrow T \models \varphi$$
- Lemma: Shoduje-li se $\mathcal{A}\models T$ s položkou v kořeni, pak lze $\mathcal{A}$ expandovat do $L_{C}$, aby se shodovala s některou větví v tablu
	- stačí expandovat o nové konstanty na větvi V
	- Důkaz (indukcí podle $i$):
		- Máme tablo $\tau$ a model $\mathcal{A} \in M_{L}(T)$, shoduje se s kořenem $\tau_{0}$
		- Najdeme posloupnost větvi $V_{i}$ a expanzi $\mathcal{A}_{i}$ o konstanty $c^{\mathcal{A}}\in C$ na té větvi, $\mathcal{A}_{i+1}$ je expanzí $\mathcal{A}$
		- Pro expanzi $\mathcal{A}$ do $L_{C}$ interpretujeme všechny konstantní symboly na $V$ stejně jako v $\mathcal{A}_{i}$
			- Pokud $\tau_{i+1}$ vzniklo bez prodloužení $V_{i}$, pak $V_{i+1}=V_{i}$ a $\mathcal{A}_{i+1}=\mathcal{A}$
			- Pokud $\tau_{i+1}$ vzniklo připojením položky s axiomem T, definujeme $V_{i+1}$ jako tu větev a $\mathcal{A}_{i+1}=\mathcal{A_{i}}$ (nepřidali jsme žádný pomocný symbol)
			- Pokud $\tau_{i+1}$ vzniklopřipojením atomického tabla pro $P$ na konec $V_{i}$, pak
				- Pro logickou spojku $\mathcal{A}_{i+1}=\mathcal{A}$ (nepřidali jsme žádný pomocný symbol)
				- Pro svědka:
					- Pokud $P = T(\exists x)\varphi(x)$, existuje $a \in A$, kterým ho můžeme ohodnotit
					- Pak $\mathcal{A}_{i+1}$ definujeme jako expanzi $\mathcal{A}_{i}$ o $c^{A}=a$
				- Pro všichni:
					- Pokud $P=T(\forall x)\varphi(x)$, pak nahradíme termem $T \varphi(x/t)$
					- Pak $\mathcal{A}_{i+1}$ je libovolná expanze $\mathcal{A}_{i}$ o nové konstanty z $t$ $\blacksquare$
- Důkaz (sporem):
	- Pro spor $T \not\models \varphi$, existuje $\mathcal{A}\in M(T): \mathcal{A}\not\models \varphi$
	- Platí $T \vdash \varphi$ => existuje sporné tablu $T$ s $F \varphi$ v kořeni
	- Model $\mathcal{A}$ se shoduje s $F \varphi$, lze ho dle lemmatu expandovat do $L_{C}$ t.ž. expanze se shoduje s nějakou větvi $V$, všechny jsou ale sporné $\blacksquare$

[[Kanonický model]]

**(T4) Věta o úplnosti tablo metody v predikátové logice.**
- Lemma: Kanonický model pro bezespornou dokončenou větev $V$ se shoduje s $V$
	- Důkaz:
		- indukcí podle atomických sentencí
		- je-li na $V$ položka $\varphi=R(s_{1},\dots,s_{n})$, pak je dle definice kanonického modelu v relaci $(s_{1},\dots,s_{n})\in R$
		- pro logické spojky použijeme atomická tabla
		- pro všichni - na V jsou položky nahrazené termem pro každý "t"$\in A$
		- pro svědek - na $V$ je položka nahrazená konstantou pro nějakou "c"$\in A$
- Důkaz úplnosti tabla (sporem se spornoti tabla): $$T \models \varphi \Rightarrow T \vdash \varphi$$
	- Libovolné dokončené tablo T z položkou $F \varphi$ je sporné
	- Kdyby nebylo, má bezespornou dokončenou větev $V$
	- $V$ je dokončena => splňuje všechny axiomy a model $\mathcal{A}$ se shoduje s $F \varphi$
	- Jeho redukt $\mathcal{A'}_{L}\not\models \varphi$, což ale znamená, že $T_{L}\not\models \varphi$, spor $\blacksquare$
- Důsledky:
	- dokazatelnost=platnost
	- sporná teorie = je dokazatelný výrok "spor" $\bot$
	- kompletní - je dokazatelný výrok nebo jeho negace, ne obojí
	- $\varphi\vdash \psi \Leftrightarrow T \vdash \varphi\to \psi$ pro sentence phi, psi
