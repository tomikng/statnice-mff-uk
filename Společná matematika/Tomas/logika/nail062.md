
# Seznam otázek ke zkoušce z NAIL062 

### (P1) Model ve výrokové logice, pravdivostní funkce výroku. 
- Model ve výrokové logice je interpretace, která přiřazuje pravdivostní hodnoty jednotlivým výrokům. Pravdivostní funkce výroku hodnotí, zda je daný výrok pravdivý nebo nepravdivý v daném modelu.

Jazyk výrokové logiky je určený neprázdnou množinou výrokových proměnných $\mathbb{P}$ (také jim říkáme prvovýroky nebo atomické výroky). Tato množina může být konečná nebo i nekonečná, obvykle ale bude spočetná ${ }^1$ (pokud neřekneme jinak), a bude mít dané uspořádání. Pro výrokové proměnné budeme obvykle používat označení $p_i$ (od slova "proposition"), ale pro lepší čitelnost, zejména je-li $\mathbb{P}$ konečná, také $p, q, r, \ldots$ Například: 
**Definice** 2.1.2 (Výrok). Výrok (výroková formule) v jazyce $\mathbb{P}$ je prvek množiny $\mathrm{VF}_{\mathbb{P}}$ definované následovně: $\mathrm{VF}_{\mathbb{P}}$ je nejmenší množina splňujícíi ${ }^3$ 
- pro každý prvovýrok $p \in \mathbb{P}$ platí $p \in \mathrm{VF}_{\mathbb{P}}$, 
- pro každý výrok $\varphi \in \mathrm{VF}_{\mathbb{P}}$ je $(\neg \varphi)$ také prvek $\mathrm{VF}_{\mathbb{P}}$ 
- pro každé $\varphi, \psi \in \operatorname{VF}_{\mathbb{P}}$ jsou $(\varphi \wedge \psi)$, $(\varphi \vee \psi),(\varphi \rightarrow \psi)$, a $(\varphi \leftrightarrow \psi)$ také prvky $\mathrm{VF}_{\mathbb{P}}$.
  
**Definice** 2.1.6 (Teorie). Teorie v jazyce $\mathbb{P}$ je libovolná množina výroků v $\mathbb{P}$, tedy libovolná podmnožina $T \subseteq \mathrm{VF}_{\mathbb{P}}$. Jednotlivým výrokům $\varphi \in T$ říkáme také axiomy. 

**Definice** 2.2.2 (Pravdivostní funkce). Pravdivostní funkce výroku $\varphi$ v konečném jazyce $\mathbb{P}$ je funkce $f_{\varphi, \mathbb{P}}:\{0,1\}^{|\mathbb{P}|} \rightarrow\{0,1\}$ definovaná induktivně: 
- je-li $\varphi$ i-tý prvovýrok z $\mathbb{P}$, potom $f_{\varphi, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right)=x_i$, 
- je-li $\varphi=\left(\neg \varphi^{\prime}\right)$, potom 
$$ 
f_{\varphi, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right)=f_{\neg}\left(f_{\varphi^{\prime}, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right)\right) 
$$ 
- je-li $\left(\varphi^{\prime} \square \varphi^{\prime \prime}\right)$ kde $\square \in\{\wedge, \vee, \rightarrow, \leftrightarrow\}$, potom 
$$ 
f_{\varphi, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right)=f_{\square}\left(f_{\varphi^{\prime}, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right), f_{\varphi^{\prime \prime}, \mathbb{P}}\left(x_0, \ldots, x_{n-1}\right)\right) . 
$$ 
**Definice** 2.2.5 (Model jazyka). Model jazyka $\mathbb{P}$ je libovolné pravdivostní ohodnocení $v: \mathbb{P} \rightarrow$ $\{0,1\}$. Množinu (všech) modelů jazyka $\mathbb{P}$ označíme $\mathbf{M}_{\mathbb{P}}$ : 
$$ 
\mathrm{M}_{\mathbb{P}}=\{v \mid v: \mathbb{P} \rightarrow\{0,1\}\}=\{0,1\}^{\mathbb{P}} 
$$ 
**Definice** 2.2.7 (Platnost výroku v modelu, model výroku). Mějme výrok $\varphi$ v jazyce $\mathbb{P}$ a model $v \in \mathrm{M}_{\mathbb{P}}$. Pokud platí $f_{\varphi, \mathbb{P}}(v)=1$, potom říkáme, že výrok $\varphi$ platí $\mathrm{v}$ modelu $v, v$ je modelem $\varphi$, a píšeme $v \models \varphi$. Množinu všech modelů výroku $\varphi$ označujeme $\operatorname{M}_{\mathbb{P}}(\varphi)$. 

Modelům jazyka, které nejsou modely $\varphi$, budeme někdy říkat nemodely $\varphi$. Tvoří doplněk množiny modelů $\varphi$. S pomocí zápisu pro inverzní relaci můžeme psát: 
$$ 
\begin{array}{r} 
\mathrm{M}_{\mathbb{P}}(\varphi)=\left\{v \in \mathrm{M}_{\mathbb{P}} \mid v \models \varphi\right\}=f_{\varphi, \mathbb{P}}^{-1}[1] \\ 
\overline{\mathrm{M}_{\mathbb{P}}(\varphi)}=M_{\mathbb{P}} \backslash M_{\mathbb{P}}(\varphi)=\left\{v \in \mathrm{M}_{\mathbb{P}} \mid v \not \models \varphi\right\}=f_{\varphi, \mathbb{P}}^{-1}[0] 
\end{array} 
$$ 
Je-li jazyk zřejmý z kontextu, můžeme psát jen $\mathrm{M}(\varphi)$. Musíme si ale být opravdu jistí: například v jazyce $\mathbb{P}=\{p, q\}$ máme 
$$ 
\mathrm{M}_{\{p, q\}}(p \rightarrow q)=\{(0,0),(0,1),(1,1)\} 
$$ 
zatímco v jazyce $\mathbb{P}^{\prime}=\{p, q, r\}$ bychom měli 
$$ 
\mathrm{M}_{\mathbb{P}^{\prime}}(p \rightarrow q)=\{(0,0,0),(0,0,1),(0,1,0),(0,1,1),(1,1,0),(1,1,1)\} . 
$$ 
**Definice** 2.2.8 (Platnost teorie, model teorie). Je-li $T$ teorie $\mathrm{v}$ jazyce $\mathbb{P}$, potom $T$ platí $\mathrm{v}$ modelu $v$, pokud každý axiom $\varphi \in T$ platí ve $v$. V tom případě říkáme také, že $v$ je modelem $T$, a píšeme $v \models T$. Množinu všech modelů teorie $T$ v jazyce $\mathbb{P}$ označíme $\mathrm{M}_{\mathbb{P}}(T)$. 

Pracujeme-li s konečnou teorií, nebo přidáváme-li k nějaké teorii konečně mnoho nových axiomů, budeme používat následující zjednodušený zápis: 
- $\mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2, \ldots, \varphi_n\right)$ místo $\mathrm{M}_{\mathbb{P}}\left(\left\{\varphi_1, \varphi_2, \ldots, \varphi_n\right\}\right)$, 
- $\mathrm{M}_{\mathbb{P}}(T, \varphi)$ místo $\mathrm{M}_{\mathbb{P}}(T \cup\{\varphi\})$.

Všimněte si, že $\mathrm{M}_{\mathbb{P}}(T, \varphi)=\mathrm{M}_{\mathbb{P}}(T) \cap \mathrm{M}_{\mathbb{P}}(\varphi), \mathrm{M}_{\mathbb{P}}(T)=\bigcap_{\varphi \in T} \mathrm{M}_{\mathbb{P}}(\varphi)$, a že pro konečnou teorii (podobně i pro spočetnou) platí 
$$ 
\mathrm{M}_{\mathbb{P}}\left(\varphi_1\right) \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2\right) \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2, \varphi_3\right) \supseteq \cdots \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2, \ldots, \varphi_n\right) . 
$$ 
Toho můžeme využít při hledání modelů hrubou silou. 


### (P2) Sémantické pojmy (pravdivost, lživost, nezávislost, splnitelnost) v logice, vzhledem k teorii. 
- Pravdivost a lživost jsou hodnoty, které se přiřazují výrokům v logice. Nezávislost výroku znamená, že pravdivost jednoho výroku nijak neovlivňuje pravdivost druhého. Splnitelnost je vlastnost takových výroků nebo systému výroků, pro které existuje model, v němž jsou všechny výroky pravdivé.

**Definice** 2.2.10 (Sémantické pojmy). Říkáme, že výrok $\varphi(v$ jazyce $\mathbb{P})$ je 
- pravdivý, tautologie, platí (v logice/logicky), a píšeme $\models \varphi$, pokud platí v každém modelu $($ jazyka $\mathbb{P}), \mathrm{M}_{\mathbb{P}}(\varphi)=\mathrm{M}_{\mathbb{P}}$ 
- lživý, sporný, pokud nemá žádný $\operatorname{model,~} \mathrm{M}_{\mathbb{P}}(\varphi)=\emptyset$ 
- nezávislý, pokud platí v nějakém modelu, a neplatí v nějakém jiném modelu, tj. není pravdivý ani lživý, $\emptyset \subsetneq \mathrm{M}_{\mathbb{P}}(\varphi) \subsetneq \mathrm{M}_{\mathbb{P}}$ 
- splnitelný, pokud má nějaký model, tj. není lživý, $\mathrm{M}_{\mathbb{P}}(\varphi) \neq \emptyset$. 
Dále říkáme, že výroky $\varphi, \psi$ (ve stejném jazyce $\mathbb{P}$ ) jsou (logicky) ekvivalentní, píšeme $\varphi \sim \psi$ pokud mají stejné modely, tj. 

**Definice** 2.2.12 (Sémantické pojmy vzhledem k teorii). Mějme teorii $T$ v jazyce $\mathbb{P}$. Ríkáme, že výrok $\varphi$ v jazyce $\mathbb{P}$ je 
- pravdivý $v T$, důsledek $T$, platí $v T$, a píšeme $T \models \varphi$, pokud $\varphi$ platí v každém modelu teorie $T$, neboli $\mathrm{M}_{\mathbb{P}}(T) \subseteq \mathrm{M}_{\mathbb{P}}(\varphi)$, 
- lživý $v T$, sporný $v T$, pokud neplatí v žádném modelu $T$, neboli $\mathrm{M}_{\mathbb{P}}(\varphi) \cap \mathrm{M}_{\mathbb{P}}(T)=$ $\mathrm{M}_{\mathbb{P}}(T, \varphi)=\emptyset$ 
- nezávislý $v T$, pokud platí v nějakém modelu $T$, a neplatí v nějakém jiném modelu $T$, tj. není pravdivý v $T$ ani lživý v $T, \emptyset \subsetneq \mathrm{M}_{\mathbb{P}}(T, \varphi) \subsetneq \mathrm{M}_{\mathbb{P}}(T)$, 
- splnitelný $v T$, konzistentní s $T$, pokud platí v nějakém modelu $T$, tj. není lživý v $T$, $\mathrm{M}_{\mathbb{P}}(T, \varphi) \neq \emptyset$. 

A říkáme, že výroky $\varphi, \psi$ (ve stejném jazyce $\mathbb{P}$ ) jsou ekvivalentni v $T, T$-ekvivalentní, píšeme $\varphi \sim_T \psi$ pokud platí v týchž modelech $T, \mathrm{tj}$. 
$\varphi \sim_T \psi$ právě když $\mathrm{M}_{\mathbb{P}}(T, \varphi)=\mathrm{M}_{\mathbb{P}}(T, \psi)$ 

Je-li $T$ teorie v jazyce $L$ a $\varphi L$-formule, potom říkáme, že $\varphi$ je: 
- pravdivá (platí) $v T$, značíme $T \models \varphi$, pokud $\mathcal{A} \models \varphi$ pro všechna $\mathcal{A} \in \mathrm{M}(T)$ (neboli: $\mathrm{M}(T) \subseteq \mathrm{M}(\varphi))$ 
- lživá $v T$, pokud $T \models \neg \varphi, \mathrm{tj}$. pokud je lživá v každém modelu $T$ (neboli: $\mathrm{M}(T) \cap \mathrm{M}(\varphi)=$ $\emptyset)$, 
- nezávislá v $T$, pokud není pravdivá $\mathrm{v} T$ ani lživá $\mathrm{v} T$. 
Máme-li prázdnou teorii $T=\emptyset\left(\mathrm{tj} . \mathrm{M}(T)=\mathrm{M}_L\right)$, potom teorii $T$ vynecháváme, píšeme $\models \varphi$, a říkáme, že $\varphi$ je pravdivá (v logice), (logicky) platí, je tautologie; podobně pro ostatní pojmy. 
Teorie je sporná, jestliže v ní platí spor $\perp$, který v predikátové logice můžeme definovat jako $R\left(x_1, \ldots, x_n\right) \wedge \neg R\left(x_1, \ldots, x_n\right)$, kde $R$ je libovolný (třeba první) relační symbol z jazyka nebo rovnost (nemá-li jazyk relační symbol, musí být s rovností). Teorie je sporná, právě když v ní platí každá formule, nebo, ekvivalentně, právě když nemá žádný model. Jinak říkáme, že je teorie bezesporná (neplatí-li v ní spor, ekvivalentně má-li alespoň jeden model). 

Sentencím pravdivým v $T$ říkáme důsledky $T$; množina všech důsledků $T$ v jazyce $L$ je: 
$$ 
\operatorname{Csq}_L(T)=\{\varphi \mid \varphi \text { je sentence a } T \models \varphi\} 
$$ 

### (P3) Ekvivalence výroků resp. výrokových teorií, T-ekvivalence. 
- Ekvivalence výroků znamená, že dva výroky jsou pravdivé nebo nepravdivé za stejných okolností. T-ekvivalence výrokových teorií znamená, že dvě teorie jsou ekvivalentní, pokud mají stejné modely.

Dále říkáme, že výroky $\varphi, \psi$ (ve stejném jazyce $\mathbb{P}$ ) jsou (logicky) ekvivalentní, píšeme $\varphi \sim \psi$ pokud mají stejné modely, tj. 

A říkáme, že výroky $\varphi, \psi$ (ve stejném jazyce $\mathbb{P}$ ) jsou ekvivalentní v $T, T$-ekvivalentní, píšeme $\varphi \sim_T \psi$ pokud platí v týchž modelech $T$, tj. 
$\varphi \sim_T \psi$ právě když $\mathrm{M}_{\mathbb{P}}(T, \varphi)=\mathrm{M}_{\mathbb{P}}(T, \psi)$. 

### (P4) Sémantické pojmy o teorii (sporná, bezesporná, kompletní, splnitelná). 
- Sporná teorie obsahuje výroky, které se vzájemně vylučují. Bezesporná teorie je taková, která není sporná. Kompletní teorie je teorie, ve které pro každý výrok platí, že je buď pravdivý, nebo je pravdivý jeho negace. Splnitelná teorie je taková, pro kterou existuje alespoň jeden model, v němž jsou všechny výroky pravdivé.

**Definice** 2.4.2 (Vlastnosti teorií). Rekneme, že teorie $T$ v jazyce $\mathbb{P}$ je 
- sporná, jestliže v ní platí $\perp$ (spor), ekvivalentně, jestliže nemá žádný model, ekvivalentně, jestliže v ní platí všechny výroky, 
- bezesporná (splnitelná), pokud není sporná, tj. má nějaký model, 
- kompletní, jestliže není sporná a každý výrok je v ní pravdivý nebo lživý (tj. nemá žádné nezávislé výroky), ekvivalentně, pokud má právě jeden model.
  
Je-li $T$ teorie v jazyce $L$ a $\varphi$ $L$-formule, potom říkáme, že $\varphi$ je: 
- pravdivá (platí) $v T$, značíme $T \models \varphi$, pokud $\mathcal{A} \models \varphi$ pro všechna $\mathcal{A} \in \mathrm{M}(T)$ (neboli: $\mathrm{M}(T) \subseteq \mathrm{M}(\varphi))$ 
- lživá v $T$, pokud $T \models \neg \varphi, \mathrm{t}$. pokud je lživá v každém modelu $T$ (neboli: $\mathrm{M}(T) \cap \mathrm{M}(\varphi)=$ $\emptyset)$, 
- nezávislá $v T$, pokud není pravdivá $\mathrm{v} T$ ani lživá $\mathrm{v} T$. 
- Máme-li prázdnou teorii $T=\emptyset\left(\mathrm{tj} . \mathrm{M}(T)=\mathrm{M}_L\right)$, potom teorii $T$ vynecháváme, píšeme $\models \varphi$, a říkáme, že $\varphi$ je pravdivá (v logice), (logicky) platí, je tautologie; podobně pro ostatní pojmy. 
- Teorie je sporná, jestliže v ní platí spor $\perp$, který v predikátové logice můžeme definovat jako $R\left(x_1, \ldots, x_n\right) \wedge \neg R\left(x_1, \ldots, x_n\right)$, kde $R$ je libovolný (třeba první) relační symbol z jazyka nebo rovnost (nemá-li jazyk relační symbol, musí být s rovností). Teorie je sporná, právě když v ní platí každá formule, nebo, ekvivalentně, právě když nemá žádný model. Jinak říkáme, že je teorie bezesporná (neplatí-li v ní spor, ekvivalentně má-li alespoň jeden model). 

Sentencím pravdivým v $T$ říkáme důsledky $T$; množina všech důsledků $T$ v jazyce $L$ je: 
$$ 
\operatorname{Csq}_L(T)=\{\varphi \mid \varphi \text { je sentence a } T \models \varphi\} 
$$ 
Kompletnost $\mathrm{v}$ predikátové logice 
Jak je tomu s pojmem kompletnosti teorie? ${ }^{22}$ 
**Definice** 6.5.1. Teorie je kompletní, je-li bezesporná a každá sentence je v ní bud' pravdivá, nebo lživá. 

Nemůžeme ale říci, že je teorie kompletní, právě když má jediný model. Máme-li totiž jeden model, dostáváme z něj nekonečně mnoho jiných, ale izomorfních modelů, tj. lišících se jen pojmenováním prvků univerza. ${ }^{23}$ Uvažovat jediný model 'až na izomorfismus' by ale nebylo dostatečné. Správným pojmem je tzv. elementární ekvivalence: 

### (P5) Extenze teorie (jednoduchá, konzervativní), odpovídající sémantická kritéria. 
- Extenze teorie je rozšíření původní teorie o nové výroky. Jednoduchá extenze přidává výroky, které nejsou v původní teorii zahrnuty. Konzervativní extenze přidává výroky, které nezpochybňují pravdivost výroků v původní teorii.

2.4.1 Důsledky teorií 
Připomeňme, že důsledek teorie $T$ je každý výrok, který v $T$ platí (tj. platí v každém modelu $T$ ) a označme si množinu všech důsledků teorie $T$ v jazyce $\mathbb{P}$ jako 
$$ 
\operatorname{Csq}_{\mathbb{P}}(T)=\left\{\varphi \in \operatorname{VF}_{\mathbb{P}} \mid T \models \varphi\right\} 
$$ 
Pokud je teorie $T$ v jazyce $\mathbb{P}$, můžeme psát: 
$$ 
\operatorname{Csq}_{\mathbb{P}}(T)=\left\{\varphi \in \operatorname{VF}_{\mathbb{P}} \mid \mathrm{M}_{\mathbb{P}}(T) \subseteq \mathrm{M}_{\mathbb{P}}(\varphi)\right\} 
$$ 
(Dává ale smysl mluvit i o důsledcích teorie v nějakém menším jazyce, který je podmnožinou jazyka $T$ ). 
Ukážeme si několik jednoduchých vlastností důsledků: 
**Tvrzení** 2.4.4. Mějme teorie $T, T^{\prime}$ a výroky $\varphi, \varphi_1, \ldots, \varphi_n$ v jazyce $\mathbb{P}$. Potom platí: 
(i) $T \subseteq \operatorname{Csq}_{\mathbb{P}}(T)$, 
(ii) $\operatorname{Csq}_{\mathbb{P}}(T)=\operatorname{Csq}_{\mathbb{P}}\left(\operatorname{Csq}_{\mathbb{P}}(T)\right)$, 
(iii) pokud $T \subseteq T^{\prime}$, potom $\mathrm{Csq}_{\mathbb{P}}(T) \subseteq \mathrm{Csq}_{\mathbb{P}}\left(T^{\prime}\right)$, 
(iv) $\varphi \in \operatorname{Csq\mathbb {P}}\left(\left\{\varphi_1, \ldots, \varphi_n\right\}\right)$ právě když je výrok $\left(\varphi_1 \wedge \cdots \wedge \varphi_n\right) \rightarrow \varphi$ tautologie. uvědomíme-li si následující vztahy: 
- $\mathrm{M}(\operatorname{Csq}(T))=\mathrm{M}(T)$ 
- je-li $T \subseteq T^{\prime}$ potom $\mathrm{M}(T) \supseteq \mathrm{M}\left(T^{\prime}\right),{ }^{20}$ 
- $\psi \rightarrow \varphi$ je tautologie, právě když platí $\mathrm{M}(\psi) \subseteq \mathrm{M}(\varphi)$, 
- $\mathrm{M}\left(\varphi_1 \wedge \cdots \wedge \varphi_n\right)=\mathrm{M}\left(\varphi_1, \ldots, \varphi_n\right)$.
  
**Definice** 2.4.6 (Extenze teorie). Mějme teorii $T$ v jazyce $\mathbb{P}$. 

- Extenze teorie $T$ je libovolná teorie $T^{\prime}$ v jazyce $\mathbb{P}^{\prime} \supseteq \mathbb{P}$ splňující $\operatorname{Csq}_{\mathbb{P}}(T) \subseteq \operatorname{Csq}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right)$,
- je to jednoduchá extenze, pokud $\mathbb{P}^{\prime}=\mathbb{P}$, 
- je to konzervativní extenze, pokud $\operatorname{Csq}_{\mathbb{P}}(T)=\operatorname{Csq}_{\mathbb{P}}\left(T^{\prime}\right)=\operatorname{Csq}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right) \cap \mathrm{VF}_{\mathbb{P}}$.

Extenze tedy znamená, že splňuje všechny důsledky původní teorie. Extenze je jednoduchá, pokud do jazyka nepřidáváme žádné nové výrokové proměnné, a konzervativní, pokud neměníme platnost tvrzení vyjádřitelných v původním jazyce, každý nový důsledek tedy musí obsahovat nějakou nově přidanou výrokovou proměnnou. 

Co tyto pojmy znamenají sémanticky, v řeči modelủ? Zformulujme nejprve obecné pozorování, které ihned poté ilustrujeme na příkladě: 

Pozorování 2.4.7. Je-li $T$ teorie v jazyce $\mathbb{P}$ a $T^{\prime}$ teorie v jazyce $\mathbb{P}^{\prime}$ obsahujícím jazyk $P$. Potom platí: 
- $T^{\prime}$ je jednoduchou extenzí $T$, právě když $\mathbb{P}^{\prime}=\mathbb{P}$ a $\mathrm{M}_{\mathbb{P}}\left(T^{\prime}\right) \subseteq \mathrm{M}_{\mathbb{P}}(T)$, 
- $T^{\prime}$ je extenzí $T$, právě když $\mathrm{M}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right) \subseteq \mathrm{M}_{\mathbb{P}^{\prime}}(T)$. Uvažujeme tedy modely teorie $T$ nad rozšířeným jazykem $\mathbb{P}^{\prime} .21$ Jinými slovy, restrikce ${ }^{22}$ libovolného modelu $v \in \mathrm{M}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right)$ na původní jazyk $\mathbb{P}$ musí být modelem $T$, mohli bychom psát $v]_{\mathbb{P}} \in \mathrm{M}_{\mathbb{P}}(T)$ nebo: 
$$ 
\left\{v\left\lceil_{\mathbb{P}} \mid v \in \mathrm{M}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right)\right\} \subseteq \mathrm{M}_{\mathbb{P}}(T)\right. 
$$ 
- T' je konzervativní extenzí T, pokud je extenzí a navíc platí, že každý model $T$ (v jazyce $\mathbb{P})$ lze nějak expandovat (rozšířit) ${ }^{23}$ na model $T^{\prime}$ (v jazyce $\left.\mathbb{P}^{\prime}\right)$, neboli každý model $T$ (v jazyce $\mathbb{P}$ ) získáme restrikcí nějakého modelu $T^{\prime}$ na jazyk $\mathbb{P}$. Mohli bychom psát: 
$$ 
\left\{v \|_{\mathbb{P}} \mid v \in \mathrm{M}_{\mathbb{P}^{\prime}}\left(T^{\prime}\right)\right\}=\mathrm{M}_{\mathbb{P}}(T) 
$$ 
- $T^{\prime}$ je extenzí $T$ a zároveň $T$ je extenzí $T^{\prime}$, právě kdyż $\mathbb{P}^{\prime}=\mathbb{P}$ a $\mathrm{M}_{\mathbb{P}}\left(T^{\prime}\right)=\mathrm{M}_{\mathbb{P}}(T)$, neboli $T^{\prime} \sim T$. 
- Kompletní jednoduché extenze T jednoznačně až na ekvivalenci odpovídají modelům $T$. Sentencím pravdivým v $T$ říkáme důsledky $T$; množina všech důsledků $T$ v jazyce $L$ je: 
$$ 
\operatorname{Csq}_L(T)=\{\varphi \mid \varphi \text { je sentence a } T \models \varphi\} 
$$ 
**Definice** 6.7.1 (Extenze teorie). Mějme teorii $T$ v jazyce $L$. 
- Extenze teorie $T$ je libovolná teorie $T^{\prime} \mathrm{v}$ jazyce $L^{\prime} \supseteq L$ splňující $\operatorname{Csq}_L(T) \subseteq \mathrm{Csq}_{L^{\prime}}\left(T^{\prime}\right)$, 
- je to jednoduchá extenze, pokud $L^{\prime}=L$, 
- je to konzervativní extenze, pokud $\operatorname{Csq}_L(T)=\mathrm{Csq}_L\left(T^{\prime}\right)=\mathrm{Csq}_{L^{\prime}}\left(T^{\prime}\right) \cap \mathrm{Fm}_L$, $\operatorname{kde}^2 \mathrm{Fm}_L$ značí množinu všech formulí $\mathrm{v}$ jazyce $L$. 
- Teorie $T^{\prime}$ (v jazyce $\left.L\right)$ je ekvivalentní teorii $T$, pokud je $T^{\prime}$ extenzí $T$ a $T$ extenzí $T^{\prime}$.
  
Podobně jako ve výrokové logice, pro teorie ve stejném jazyce platí následující sémantický popis těchto pojmů: 
Pozorování 6.7.2. Mějme teorie $T$, $T^{\prime}$ v jazyce L. Potom: 
- $T^{\prime}$ je extenze $T$, právě když $\mathrm{M}_L\left(T^{\prime}\right) \subseteq \mathrm{M}_L(T)$. 
- $T^{\prime}$ je ekvivalentnís $T$, právě když $\mathrm{M}_L\left(T^{\prime}\right)=\mathrm{M}_L(T)$. 
Jak je tomu v případě, kdy teorie $T^{\prime}$ je nad větším jazykem než $T$ ? Připomeňme situaci ve výrokové logice, popsanou v Pozorování 2.4.7. Zformulujeme a dokážeme analogické tvrzení: Zatímco ve výrokové logice jsme přidávali hodnoty pro nové prvovýroky, resp. je zapomínali, v predikátové logice budeme expandovat resp. redukovat struktury, tj. přidávat nebo zapomínat interpretace relačních, funkčních, a konstantních symbolů. Princip tvrzení ale zůstává stejný.

**Tvrzení** 6.7.3. Mějme jazyky $L \subseteq L^{\prime}$, teorii $T$ v jazyce $L$, a teorii $T^{\prime}$ v jazyce $L^{\prime}$. 
(i) $T^{\prime}$ je extenzí teorie $T$, právě když redukt každého modelu $T^{\prime}$ na jazyk L je modelem $T$. 
(ii) Pokud je $T^{\prime}$ extenzí teorie T, a každý model $T$ lze expandovat do jazyka $L^{\prime}$ na nějaký model teorie $T^{\prime}$, potom je $T^{\prime}$ je konzervativní extenzi teorie $T$. 

**Poznámka** 6.7.4. V části (ii) platí i opačná implikace, důkaz ale není tak jednoduchý, jako ve výrokové logice, a proto ho neuvedeme. (Problémem je jak získat z modelu $T$ který nelze expandovat na model $T^{\prime} L$-sentenci, která platí v $\mathrm T$ ale ne v $\mathrm T^{\prime}$. 

**Důkaz**. Nejprve dokažme (i): Mějme model $\mathcal{A}^{\prime}$ teorie $T^{\prime}$ a označme jako $\mathcal{A}$ jeho redukt na jazyk $L$. Protože $T^{\prime}$ je extenzí teorie $T$, platí v $T^{\prime}$, a tedy i v $\mathcal{A}^{\prime}$, každý axiom $\varphi \in T$. Potom ale i $\mathcal{A} \models \varphi(\varphi$ obsahuje jen symboly z jazyka $L)$, tedy $\mathcal{A}$ je modelem $T$. 

Na druhou stranu, mějme $L$-sentenci $\varphi$ takovou, že $T \models \varphi$. Chceme ukázat, že $T^{\prime} \models \varphi$ Pro libovolný model $\mathcal{A}^{\prime} \in \mathrm{M}_{L^{\prime}}\left(T^{\prime}\right)$ víme, že jeho $L$-redukt $\mathcal{A}$ je modelem $T$, tedy $\mathcal{A} \models \varphi$. Z toho plyne i $\mathcal{A}^{\prime} \models \varphi$ (opět proto, že $\varphi$ je v jazyce $L$ ). 

Nyní (ii): Vezměme libovolnou $L$-sentenci $\varphi$, která platí v teorii $T^{\prime}$, a ukažme, že platí i v $T$. Každý model $\mathcal{A}$ teorie $T$ lze expandovat na nějaký model $\mathcal{A}^{\prime}$ teorie $T^{\prime}$. Víme, že $\mathcal{A}^{\prime} \models \varphi$ takže i $\mathcal{A} \models \varphi$. Tím jsme dokázali, že $T \models \varphi$, tj. jde o konzervativní extenzi. 

### (P6) Tablo z teorie, tablo důkaz. 
- Tablo je grafická metoda pro testování logických argumentů a dokazování tezí ve výrokové a predikátové logice. Tablo důkaz je metoda pro ověřování pravdivosti výroků pomocí stromové struktury, kde výroky jsou rozděleny na menší části až do základních atomických výroků.

**Definice** 4.3.1 (Tablo). Konečné tablo z teorie $T$ je uspořádaný, položkami označkovaný strom zkonstruovaný aplikací konečně mnoha následujících pravidel:
- jednoprvkový strom označkovaný libovolnou položkou je tablo z teorie $T$,
- pro libovolnou položkou $P$ na libovolné větvi $V$, můžeme na konec větve $V$ připojit atomické tablo pro položku $P$,
- na konec libovolné větve můžeme připojit položku T $\alpha$ pro libovolný axiom teorie $\alpha \in T$.
  
Tablo $z$ teorie T je bud' konečné, nebo i nekonečné: v tom případě vzniklo ve spočetně mnoha krocích. Můžeme ho formálně vyjádřit jako sjednocení $\tau=\bigcup_{i \geq 0} \tau_i$, kde $\tau_i$ jsou konečná tabla z $T, \tau_0$ je jednoprvkové tablo, a $\tau_{i+1}$ vzniklo z $\tau_i$ v jednom kroku. ${ }^4$
Tablo pro položku $P$ je tablo, které má položku $P \mathrm{v}$ kořeni.

Připomeňme konvenci, že kořen atomického tabla nebudeme zapisovat (nebot' vrchol $\mathrm{s}$ položkou $P$ už v tablu je). V definici neurčujeme, v jakém pořadí provádět jednotlivé kroky, později ale specifikujeme konkrétní postup konstrukce (algoritmus), kterému budeme říkat systematické tablo.

Abychom získali důkazový systém, zbývá definovat pojem tablo důkazu (a související pojmy). Připomeňme ještě jednou, že jde o důkaz sporem, tedy předpokládáme, že výrok neplatí, a najdeme sporné tablo:

**Definice** 4.3.2 (Tablo důkaz). Tablo důkaz výroku $\varphi$ z teorie $T$ je sporné tablo z teorie $T$ s položkou F$\varphi$ v kořeni. Pokud existuje, je $\varphi$ (tablo) dokazatelný z $T$, píšeme $T \vdash \varphi$. (Definujme také tablo zamítnutí jako sporné tablo s $\mathrm{T}$$\varphi$ v kořeni. Pokud existuje, je $\varphi$ (tablo) zamítnutelný z $T$, tj. platí $T \vdash \neg \varphi$.)

- Tablo je sporné, pokud je každá jeho větev sporná.
- Větev je sporná, pokud obsahuje položky T $\psi$ a F $\psi$ pro nějaký výrok $\psi$, jinak je bezesporná.
- Tablo je dokončené, pokud je každá jeho větev dokončená.
- Větev je dokončená, pokud
    - je sporná, nebo
    - je každá její položka na této větvi redukovaná a zároveň obsahuje položku T $\alpha$ pro každý axiom $\alpha \in T$

- Položka $P$ je redukovaná na větvi $V$ procházející touto položkou, pokud
    - je tvaru T$p$ resp. F$p$ pro nějakou výrokovou proměnnou $p \in \mathbb{P}$, nebo
    - při konstrukci tabla již došlo k jejímu rozvoji na $V$, tj. vyskytuje se na $V$ jako kořen atomického tabla. ${ }^5$


7.2.2 Tablo důkaz 
**Definice** v této části jsou téměř identické odpovídajícím definicím z výrokové logiky. Hlavní technický problém je jak definovat redukovanost položek typu 'všichni' na větvi tabla: chceme aby za proměnnou byly substituovány všechny konstantní $L_C$-termy $t_i$. 

**Definice** 7.2.1 (Tablo). Konečné tablo $z$ teorie $T$ je uspořádaný, položkami označkovaný strom zkonstruovaný aplikací konečně mnoha následujících pravidel: 
- jednoprvkový strom označkovaný libovolnou položkou je tablo z teorie $T$, 
- pro libovolnou položkou $P$ na libovolné větvi $V$, můžeme na konec větve $V$ připojit atomické tablo pro položku $P$, přičemž je-li $P$ typu 'svědek', můžeme použít jen pomocný konstantní symbol $c_i \in C$, který se na větvi $V$ dosud nevyskytuje (pro položky typu 'všichni' můžeme použít libovolný konstantní $L_C$-term $t_i$ ), 
- na konec libovolné větve můžeme připojit položku T $\alpha$ pro libovolný axiom teorie $\alpha \in T$.
  
Tablo z teorie $T$ je bud' konečné, nebo i nekonečné: v tom případě vzniklo ve spočetně mnoha krocích. Můžeme ho formálně vyjádřit jako sjednocení $\tau=\bigcup_{i \geq 0} \tau_i$, kde $\tau_i$ jsou konečná tabla z $T, \tau_0$ je jednoprvkové tablo, a $\tau_{i+1}$ vzniklo z $\tau_i$ v jednom kroku. ${ }^3$ 
Tablo pro položku $P$ je tablo, které má položku $P$ v kořeni.

Připomeňme konvenci, že pokud $P$ není typu 'všichni', potom kořen atomického tabla nebudeme zapisovat (nebot' vrchol s položkou $P$ už v tablu je).

**Definice** 7.2.2 (Tablo důkaz). Tablo důkaz sentence $\varphi$ z teorie $T$ je sporné tablo z teorie $T$ s položkou $F \varphi$ v kořeni. Pokud existuje, je $\varphi$ (tablo) dokazatelná z $T$, pís̃eme $T \vdash \varphi$. (Definujme také tablo zamítnutí jako sporné tablo s T $\varphi$ v kořeni. Pokud existuje, je $\varphi$ (tablo) zamítnutelná z $T$, tj. platí $T \vdash \neg \varphi$.) 
- Tablo je sporné, pokud je každá jeho větev sporná. 
- Větev je sporná, pokud obsahuje položky T $\psi$ a F $\psi$ pro nějakou sentenci $\psi$, jinak je bezesporná. 
- Tablo je dokončené, pokud je každá jeho větev dokončená. 
- Větev je dokončená, pokud 
    - je sporná, nebo 
    - je každá položka na této větvi redukovaná a zároveň větev obsahuje položku T $\alpha$ pro každý axiom $\alpha \in T$. 
- Položka $P$ je redukovaná na větvi $V$ procházející touto položkou, pokud 
    - není typu 'všichni' a při konstrukci tabla již došlo k jejímu rozvoji na $V$, tj. vyskytuje se na $V$ jako kořen atomického tabla. ${ }^4$ 
    - je typu 'všichni' a všechny její výskyty na $V$ jsou na větvi $V$ redukované. 
- Výskyt položky $P$ typu 'všichni' na větvi $V$ je $i$-tý, pokud má na $V$ právě $i-1$ předků označených touto položkou, a $i$-tý výskyt je redukovaný na $V$, pokud 
    - položka $P$ má $(i+1)$-ní výskyt na $V$, a zároveň 
    - na $V$ se vyskytuje položka $\mathrm{T} \varphi\left(x / t_i\right)$ (je-li $P=\mathrm{T}(\forall x) \varphi(x)$ ) resp. F $\varphi\left(x / t_i\right)$ (je-li $P=\mathrm{F}(\exists x) \varphi(x))$, kde $t_i$ je $i$-tý konstantní $L_C$-term. ${ }^5$

Všimněte si, že je-li položka typu 'všichni' na nějaké větvi redukovaná, musí mít na této větvi nekonečně mnoho výskytı̊, a museli jsme v nich použít při substituci všechny možnosti, tj. všechny konstantní $L_C$-termy. 

### (P7) Kanonický model. 
- Kanonický model je specifický model dané teorie, který se vyznačuje jednoduchostí a přehledností a slouží jako vzorový příklad pro danou teorii.

**Definice** 4.5.3 (Kanonický model). Je-li $V$ bezesporná větev dokončeného tabla, potom kanonický model pro $V$ je model definovaný předpisem (pro $p \in \mathbb{P})$ : 
$$ 
v(p)=\left\{\begin{array}{l} 
1 \text { pokud se na } V \text { vyskytuje položka } \mathrm{T} p, \\ 
0 \text { jinak. } 
\end{array}\right. 
$$ 

**Definice** 7.4.3 (Kanonický model). Mějme teorii $T$ v jazyce $L=\langle\mathcal{F}, \mathcal{R}\rangle$ a nechť $V$ je bezesporná větev nějakého dokončeného tabla z teorie $T$. Potom kanonický model pro $V$ je $L_C$-struktura $\mathcal{A}=\left\langle A, \mathcal{F}^{\mathcal{A}} \cup C^{\mathcal{A}}, \mathcal{R}^{\mathcal{A}}\right\rangle$ definovaná následovně: 
Je-li jazyk $L$ bez rovnosti, potom: 
- Doména $A$ je množina všech konstantních $L_C$-termů. 
- Pro každý n-ární relační symbol $R \in \mathcal{R}$ a "s $s_1, \ldots$, "s ${ }_n$ " z $A$ : 
$\left(" s_1 ", \ldots\right.$, " $\left.s_n "\right) \in R^{\mathcal{A}}$ právě když na větvi $V$ je položka $\mathrm{T} R\left(s_1, \ldots, s_n\right)$ 
- Pro každý $n$-ární funkční symbol $f \in \mathcal{F}$ a "s $s_1,, \ldots$, "s $n_n$ z $A$ : 
$$ 
f^{\mathcal{A}}\left(" s_1 ", \ldots, " s_n "\right)=" f\left(s_1, \ldots, s_n\right) " 
$$ 
Speciálně, pro konstantní symbol $c$ máme $c^{\mathcal{A}}=$ "c". 
Funkci $f^{\mathcal{A}}$ tedy interpretujeme jako 'vytvoření' nového termu ze symbolu $f$ a vstupních termů 
Necht je $L$ jazyk s rovností. Připomeňme, že naše tablo je nyní z teorie $T^*$, tj. z rozšíření $T$ o axiomy rovnosti pro $L$. Nejprve vytvoříme kanonický model $\mathcal{B}$ pro $V$ jakoby byl $L$ bez rovnosti (jeho doména $B$ je tedy množina všech konstantních $L_C$-termů). Dále definujeme relaci $=^B$ stejně jako pro ostatní relační symboly: 

"$s_1$ "$={ }^B$ "$s_2$ " právě když na větvi $V$ je položka $\mathrm{T} s_1=s_2$

Kanonický model pro $V$ potom definujeme jako faktorstrukturu $\mathcal{A}=\mathcal{B} /=^B$. 
Jak plyne z diskuze v Sekci 7.3 , relace $={ }^B$ je opravdu kongruence struktury $\mathcal{B}$, definice je tedy korektní, a relace $=^{\mathcal{A}}$ je identita na $A$. Platí následující jednoduché pozorování: 

Pozorování 7.4.4. Pro každou formuli $\varphi$ máme $\mathcal{B} \models \varphi$ (kde symbol $=$ je interpretován jako binární relace $\left.=^B\right)$, právě když $\mathcal{A}=\mathcal{B} /=^B \models \varphi(k d e=$ je interpretován jako identita). 

### (P8) Kongruence struktury, faktorstruktura, axiomy rovnosti. 
- Kongruence struktury je relace, která je kompatibilní s operacemi struktury. Faktorstruktura je struktura získaná vytvořením ekvivalenčních tříd na základě kongruence. Axiomy rovnosti jsou základní pravidla, která definují vlastnosti rovnosti.

**Definice** 7.3.1 (Kongruence). Mějme ekvivalenci $\sim$ na množině $A$, funkci $f: A^n \rightarrow A$, a relaci $R \subseteq A^n$. Říkáme, že $\sim$ je: 
- kongruencí pro funkci $f$, pokud pro všechna $x_i, y_i \in A$ taková, že $x_i \sim y_i(1 \leq i \leq n)$ platí $f\left(x_1, \ldots, x_n\right) \sim f\left(y_1, \ldots, y_n\right)$ 
- kongruencí pro relaci $R$, pokud pro všechna $x_i, y_i \in A$ taková, že $x_i \sim y_i(1 \leq i \leq n)$ platí $R\left(x_1, \ldots, x_n\right)$ právě když $R\left(y_1, \ldots, y_n\right)$. 

Kongruence struktury $\mathcal{A}$ je ekvivalence $\sim$ na množině $A$, která je kongruencí pro všechny funkce a relace $\mathcal{A}$. 

**Definice** 7.3.2 (Faktorstruktura). Mějme strukturu $\mathcal{A}$ a její kongruenci . Faktorstruktura (podílová struktura) $\mathcal{A}$ podle $\sim$ je struktura $\mathcal{A} / \sim$ v témž jazyce, jejíž univerzum $A / \sim$ je množina všech rozkladových tříd $A$ podle $\sim$, a jejíž funkce a relace jsou definované pomocí reprezentantů, $\mathrm{tj}:$ 
- $f^{\mathcal{A} / \sim}\left(\left[x_1\right]_{\sim}, \ldots,\left[x_n\right]_{\sim}\right)=\left[f^{\mathcal{A}}\left(x_1, \ldots, x_n\right)\right]_{\sim}$, pro každý (n-ární) funkční symbol $f$, a 
- $R^{\mathcal{A} / \sim}\left(\left[x_1\right]_{\sim}, \ldots,\left[x_n\right]_{\sim}\right)$ právě když $R^{\mathcal{A}}\left(x_1, \ldots, x_n\right)$, pro každý (n-ární) relační symbol $R$.
  
**Definice** 7.3.3 (Axiomy rovnosti). Axiomy rovnosti pro jazyk $L$ s rovností jsou následující: 
(i) $x=x$ 
(ii) $x_1=y_1 \wedge \cdots \wedge x_n=y_n \rightarrow f\left(x_1, \ldots, x_n\right)=f\left(y_1, \ldots, y_n\right)$ pro každý $n$-ární funkční symbol $f$ jazyka $L$ 
(iii) $x_1=y_1 \wedge \cdots \wedge x_n=y_n \rightarrow\left(R\left(x_1, \ldots, x_n\right) \rightarrow R\left(y_1, \ldots, y_n\right)\right)$ pro každý $n$-ární relační symbol $R$ jazyka $L$ včetně rovnosti. 

### (P9) CNF a DNF, Hornův tvar. Množinová reprezentace CNF formule, splňující ohodnocení. 
- CNF (Conjunctive Normal Form) a DNF (Disjunctive Normal Form) jsou standardizované formy zápisu logických formulí. Hornův tvar je specifická forma CNF. Množinová reprezentace CNF formule je zápis formule jako množiny klauzulí. Splňující ohodnocení je takové ohodnocení proměnných, při kterém je celá formule pravdivá.

Připomeňme, že výroky jsou ekvivalentní, pokud mají stejnou množinu modelů. Pro každý výrok existuje nekonečně mnoho ekvivalentních výroků; často se hodí vyjádřit výrok v nějakém 'hezkém' (užitečném) 'tvaru', tj. najít ekvivalentní výrok v daném tvaru. Takovému konceptu tvaru se v matematice říká normální forma. My si představíme dvě nejznámější: konjunktivní normální formu (conjunctive normal form, CNF) a disjunktivní normální formu (DNF). 
Používá se následující terminologie a značení: 
- Literál $\ell$ je bud' prvovýrok $p$ nebo negace prvovýroku $\neg p$. Pro prvovýrok $p$ označme $p^0=\neg p$ a $p^1=p$. Je-li $\ell$ literál, potom $\bar{\ell}$ označuje opačný literál k $\ell$. Je-li $\ell=p$ (pozitivní literál), potom $\bar{\ell}=\neg p$, je-li $\ell=\neg p$ (negativní literál), potom $\bar{\ell}=p$ 
- Klauzule (clause) je disjunkce literálů $C=\ell_1 \vee \ell_2 \vee \cdots \vee \ell_n$. Jednotková klauzule (unit clause) je samotný literál $(n=1)$ a prázdnou klauzulí $(n=0)$ myslíme $\perp$. 
- Výrok je v konjunktivní normální formě (v CNF) pokud je konjunkcí klauzulí. Prázdný výrok v CNF je $\top$. 
- Elementární konjunkce je konjunkce literálů $E=\ell_1 \wedge \ell_2 \wedge \cdots \wedge \ell_n$. Jednotková elementární konjunkce je samotný literál $(n=1)$. Prázdná elementární konjunkce $(n=0)$ je $\top$. 
- Výrok je $v$ disjunktivní normální formě (v DNF) pokud je disjunkcí elementárních konjunkcí. Prázdný výrok v DNF je $\perp$. 
Nyní si ukážeme další fragment SATu řešitelný v polynomiálním čase, tzv. Horn-SAT neboli problém splnitelnosti hornovských výroků.
- Výrok je v hornovský (v Hornově tvaru) ${ }^6$, pokud je konjunkcí hornovských klauzulí, tj. klauzulí obsahujících nejvýše jeden *pozitivni* literál. Význam Hornovských klauzulí vyplývá z ekvivalentního vyjádření ve formě implikace: 
$$ 
\neg p_1 \vee \neg p_2 \vee \cdots \vee \neg p_n \vee q \sim\left(p_1 \wedge p_2 \wedge \cdots \wedge p_n\right) \rightarrow q 
$$ 
Hornovské formule tedy dobře modelují systémy, kde splnění určitých podmínek zaručuje splnění jiné podmínky. Upozorněme, že jednotková klauzule $\ell$ je také hornovská. V kontextu logického programování se jí říká fakt, pokud je literál pozitivní, a cíl pokud je negativní. ${ }^7$ Hornovské formule s alespoň jedním pozitivním a alespoň jedním negativním literálem jsou pravidla. 

5.1 Množinová reprezentace 
Nejprve představíme úspornější zápis CNF výroků, tzv. množinový zápis. Bylo by totiž nepraktické zapisovat výroky včetně závorek a logických symbolů. 
- Připomeňme, že Literál $\ell$ je prvovýrok nebo negace prvovýroku a že $\bar{\ell}$ označuje opačný literál k $\ell$. 
- Klauzule $C$ je konečná množina literálů. Prázdnou klauzuli, která není nikdy splněna, označíme $\square$. 
- $(C N F)$ formule $S$ je (konečná, nebo i nekonečná) množina klauzulí. Prázdná formule $\emptyset$ je vždy splněna.  

**Poznámka** 5.1.1. Všimněte si, že formule může být i nekonečná množina klauzulí. Pokud tedy převádíme nekonečnou výrokovou teorii do CNF, zapíšeme v množinové reprezentaci všech nekonečně mnoho klauzulí jako prvky jediné formule (množiny). V praktických aplikacích je samozřejmě formule (téměř vždy) konečná. 

V množinové reprezentaci odpovídají modely množinám literálů, které obsahují pro každou výrokovou proměnnou $p$ právě jeden z literálo̊ $p, \neg p$ : 
- (Částečné) ohodnocení $\mathcal{V}$ je libovolná množina literálů, která je konzistentní, tj. neobsahuje dvojici opačných literálů. 
- Ohodnocení je úplné, pokud obsahuje pozitivní nebo negativní literál pro každou výrokovou proměnnou. 
- Ohodnocení $\mathcal{V}$ splňuje formuli $S$, píšeme $\mathcal{V} \models S$, pokud $\mathcal{V}$ obsahuje nějaký literál z každé klauzule v $S$, tj.: 
$$ 
\mathcal{V} \cap C \neq \emptyset \text { pro každou } C \in S 
$$ 

### (P10) Rezoluční pravidlo, unifikace, nejobecnější unifikace. 
- Rezoluční pravidlo je metoda, která se používá pro důkaz výroků v logice, konkrétně v predikátové logice. Unifikace je proces hledání takového ohodnocení proměnných, které dělá dva výroky ekvivalentními. Nejobecnější unifikace je taková unifikace, která má nejméně omezení na hodnoty proměnných.

**Definice** 5.2.1 (Rezoluční pravidlo). Mějme klauzule $C_1$ a $C_2$ a literál $\ell$ takový, že $\ell \in C_1$ a $\bar{\ell} \in C_2$. Potom rezolventa klauzulí $C_1$ a $C_2$ přes literál $\ell$ je klauzule 
$$ 
C=\left(C_1 \backslash\{\ell\}\right) \cup\left(C_2 \backslash\{\bar{\ell}\}\right) 
$$ 
Z první klauzule tedy odstraníme literál $\ell$ a z druhé literál $\bar{\ell}$ (které tam musely být!) a všechny zbylé literály sjednotíme do výsledné rezolventy. S pomocí symbolu ப் pro disjunktní sjednocení bychom také mohli psát: 
$$ 
C_1^{\prime} \cup C_2^{\prime} \text { je rezolventou klauzulí } C_1^{\prime} \dot{ப}\{\ell\} \text { a } C_2^{\prime} \dot{ப}\{\bar{\ell}\} 
$$ 

**Definice** 8.4.2 (Substituce). Substituce je konečná množina $\sigma=\left\{x_1 / t_1, \ldots, x_n / t_n\right\}$, kde $x_i$ jsou navzájem různé proměnné a $t_i$ jsou termy, přičemž vyžadujeme, aby term $t_i$ nebyl roven proměnné $x_i$. Substituce $\sigma$ je 
- základní, jsou-li všechny termy $t_i$ konstantní, 
- přejmenováni proměnných, jsou-li všechny termy $t_i$ navzájem různé proměnné.
  
Instance výrazu (termu nebo literálu) $E$ při substituci $\sigma=\left\{x_1 / t_1, \ldots, x_n / t_n\right\}$ je výraz vzniklý z $E$ simultánním nahrazením všech výskytů proměnných $x_i$ termy $t_i$, označme jej $E \sigma$. Je-li $S$ množina výrazů, potom značíme $S \sigma=\{E \sigma \mid E \in S\}$. 

Protože proměnné nahrazujeme simultánně pro všechny proměnné zároveň, případný výskyt proměnné $x_i \mathrm{v}$ termu $t_j$ nepovede ke zřetězení substitucí. 

**Definice** 8.4.8 (Unifikace). Mějme konečnou množinu výrazů $S=\left\{E_1, \ldots, E_n\right\}$. Substituce $\sigma$ je unifikace pro $S$, pokud $E_1 \sigma=E_2 \sigma=\cdots=E_n \sigma$, neboli $S \sigma$ obsahuje jediný výraz. Pokud existuje, potom říkáme také, že $S$ je unifikovatelná. 

Unifikace pro $S$ je nejobecnější, pokud pro každou unifikaci $\tau$ pro $S$ existuje substituce $\lambda$ taková, že $\tau=\sigma \lambda$. Všimněte si, že nejobecnějších unifikací pro $S$ může být více, ale liší se jen přejmenováním proměnných. 

**Definice** 8.5.2 (Rezoluční pravidlo). Mějme klauzule $C_1$ a $C_2$ s disjunktními množinami proměnných a necht' jsou tvaru 
$$ 
C_1=C_1^{\prime} \sqcup\left\{A_1, \ldots, A_n\right\}, \quad C_2=C_2^{\prime} \sqcup\left\{\neg B_1, \ldots, \neg B_m\right\} 
$$ 
kde $n, m \geq 1$ a množinu výrazů $S=\left\{A_1, \ldots, A_n, B_1, \ldots, B_m\right\}$ lze unifikovat. ${ }^{10}$ Bud' $\sigma$ nejobecnější unifikace $S .^{11}$ Rezolventa klauzulí $C_1$ a $C_2$ je následující klauzule: 
$$ 
C=C_1^{\prime} \sigma \cup C_2^{\prime} \sigma 
$$ 
**Poznámka** 8.5.3. Podmínku o disjunktních množinách proměnných můžeme vždy splnit, pokud přejmenujeme proměnné v jedné z klauzulí. Proč je to potřeba? Například, z klauzulí $\{\{P(x)\},\{\neg P(f(x))\}\}$ můžeme získat prázdnou klauzuli $\square$, pokud nahradíme klauzuli $\{P(x)\}$ klauzulí $\{P(y)\}$. Množina výrazů $\{P(x), \neg P(f(x))\}$ ale není unifikovatelná, bez přejmenování proměnných by to tedy nešlo. 


### (P11) Rezoluční důkaz a zamítnutí, rezoluční strom. 
- Rezoluční důkaz je technika používaná v predikátové logice k dokazování nebo zamítnutí výroků pomocí rezolučního pravidla. Rezoluční strom je grafická reprezentace tohoto procesu, kde uzly stromu představují jednotlivé kroky důkazu.

**Definice** 5.2.4 (Rezoluční důkaz). Rezoluční důkaz (odvození) klauzule $C$ z formule $S$ je konečná posloupnost klauzulí $C_0, C_1, \ldots, C_n=C$ taková, že pro každé $i$ bud' $C_i \in S$ nebo $C_i$ je rezolventou nějakých $C_j, C_k$ kde $j<i$ a $k<i$. 

Pokud rezoluční důkaz existuje, říkáme, že $C$ je rezolucí dokazatelná z $S$, a píšeme $S \vdash_R C$. (Rezoluční) zamítnutí formule $S$ je rezoluční důkaz $\square$ z $S$, v tom případě je $S$ (rezolucí) zamítnutelná. 

**Definice** 5.2.6 (Rezoluční strom). Rezoluční strom klauzule $C$ z formule $S$ je konečný binární strom s vrcholy označenými klauzulemi, kde 
- v kor̆eni je $C$, 
- v listech jsou klauzule z $S$, 
- v každém vnitřním vrcholu je rezolventa klauzulí ze synů tohoto vrcholu.
  
**Definice** 8.5.4 (Rezoluční důkaz). Rezoluční důkaz (odvození) klauzule $C$ z formule $S$ je konečná posloupnost klauzulí $C_0, C_1, \ldots, C_n=C$ taková, že pro každé $i$ je 
- bud' $C_i=C_i^{\prime} \sigma$ pro nějakou klauzuli $C_i \in S$ a přejmenování proměnných $\sigma$, nebo 
- $C_i$ je rezolventou nějakých $C_j, C_k$ kde $j<i$ a $k<i$.
  
Pokud rezoluční důkaz existuje, říkáme, že $C$ je rezolucí dokazatelná z $S$, a píšeme $S \vdash_R C$. (Rezoluční) zamítnutí formule $S$ je rezoluční důkaz $\square$ z $S$, v tom případě je $S$ (rezolucí) zamítnutelná. 

### (P12) Lineární rezoluce, lineární důkaz, LI-rezoluce, LI-důkaz. 
- Lineární rezoluce a lineární důkaz jsou techniky, při kterých se postupuje sekvenčně, krok za krokem, bez možnosti větvení. LI-rezoluce a LI-důkaz jsou specifické druhy lineární rezoluce a důkazu, které se vyznačují specifickými omezeními na formu výroků.

**Definice** 5.4.1 (Lineární důkaz). Lineární důkaz (rezolucí) klauzule $C$ z formule $S$ je konečná posloupnost 
$$ 
\left[\begin{array}{l} 
C_0 \\ 
B_0 
\end{array}\right],\left[\begin{array}{l} 
C_1 \\ 
B_1 
\end{array}\right], \ldots,\left[\begin{array}{l} 
C_n \\ 
B_n 
\end{array}\right], C_{n+1} 
$$ 
kde $C_i$ říkáme centrální klauzule, $C_0$ je počáteční, $C_{n+1}=C$ je koncová, $B_i$ jsou boční klauzule, a platí: 
- $C_0 \in S$, pro $i \leq n$ je $C_{i+1}$ rezolventou $C_i$ a $B_i$, 
- $B_0 \in S$, pro $i \leq n$ je $B_i \in S$ nebo $B_i=C_j$ pro nějaké $j<i$.
  
Lineární zamítnutí $S$ je lineární důkaz $\square$ z $S$.

5.4.2 LI-rezoluce 
V obecném lineárním důkazu může být každá následující boční klauzule bud' axiom z $S$ nebo jedna z předchozích centrálních klauzulí. Pokud zakážeme druhou možnost, budeme-li tedy požadovat, aby všechny boční klauzule byly z $S$, dostaneme tzv. LI (linear-input) rezoluci:

**Definice** 5.4.4 (LI-důkaz). LI-důkaz (rezolucí) klauzule $C$ z formule $S$ je lineární důkaz 
$$ 
\left[\begin{array}{l} 
C_0 \\ 
B_0 
\end{array}\right],\left[\begin{array}{l} 
C_1 \\ 
B_1 
\end{array}\right], \ldots,\left[\begin{array}{l} 
C_n \\ 
B_n 
\end{array}\right], C 
$$ 
ve kterém je každá boční klauzule $B_i$ axiom z $S$. Pokud LI-důkaz existuje, říkáme, že je $C$ LI-dokazatelná z $S$, a píšeme $S \vdash_{L I} C$. Pokud $S \vdash_{L I} \square$, je $S$ LI-zamítnutelná. 

**Poznámka** 5.4.5. LI-důkaz přímo dává rezoluční strom (všechny listy jsou axiomy), a to ve speciálním tvaru, kterému bychom mohli říkat 'chlupatá cesta'. A naopak, z rezolučního stromu ve tvaru chlupaté cesty okamžitě získáme LI-důkaz: vrcholy na cestě jsou centrální klauzule, chlupy jsou boční klauzule. 

Zatímco lineární rezoluce je jen jiný pohled na obecný rezoluční důkaz, LI-rezoluce přináší zásadní omezení: ztrácíme úplnost (ne každá nesplnitelná formule má LI-zamítnutí). Na druhou stranu, LI-důkazy je jednodušší konstruovat. ${ }^5$ 

V této sekci připomeneme pojmy lineárniho a linear-input důkazu, LI-rezoluci a její úplnost pro Hornovské formule. **Definice** i znění vět jsou stejné jako ve výrokové logice, důkaz lze provést převedením na výrokovou logiku opět pomocí Herbrandovy věty a Lifting lemmatu. 
**Definice** 8.7.1 (Lineární a LI důkaz). Lineární důkaz (rezolucí) klauzule $C$ z formule $S$ je konečná posloupnost 
$$ 
\left[\begin{array}{l} 
C_0 \\ 
B_0 
\end{array}\right],\left[\begin{array}{l} 
C_1 \\ 
B_1 
\end{array}\right], \ldots,\left[\begin{array}{l} 
C_n \\ 
B_n 
\end{array}\right], C_{n+1} 
$$ 
kde $C_i$ ř́́káme centrální klauzule, $C_0$ je počáteční, $C_{n+1}=C$ je koncová, $B_i$ jsou boční klauzule, a platí: 
- $C_0$ je varianta klauzule z $S$, pro $i \leq n$ je $C_{i+1}$ rezolventou $C_i$ a $B_i$, 
- $B_0$ je varianta klauzule z $S$, pro $i \leq n$ je $B_i$ varianta klauzule z $S$ nebo $B_i=C_j$ pro nějaké $j<i$. 
Lineární zamítnutí $S$ je lineární důkaz $\square$ z $S$. 
LI-důkaz je lineární důkaz, ve kterém je každá boční klauzule $B_i$ variantou klauzule z $S$. Pokud existuje LI-důkaz, říkáme, že je $C$ LI-dokazatelná z $S$, a píšeme $S \vdash_{L I} C$. Pokud $S \vdash_{L I} \square$, je $S$ LI-zamítnutelná. 

V Poznámce 5.4.2 jsme poznamenali, že 'lineární' rezoluce (založená na lineárních důkazech) je úplná. **Důkaz** byl ponechán jako cvičení. Stejné tvrzení platí i v predikátové rezoluci: 
**Věta** 8.7.2 (O úplnosti lineární rezoluce). Klauzule $C$ má lineární důkaz z CNF formule $S$, právě když má rezoluční důkaz z $S\left(t j . S \vdash_R C\right)$. 

**Důkaz**. Z lineárního důkazu snadno vyrobíme rezoluční strom. Opačná implikace plyne z Poznámky 5.4.2 a z Lifting lemmatu (jehož použití zachovává linearitu rezolučního důkazu). 

### (P13) Signatura a jazyk predikátové logiky, struktura daného jazyka. 
- Signatura je sada symbolů používaných v jazyce predikátové logiky. Jazyk predikátové logiky je sada výroků vytvořených pomocí těchto symbolů. Struktura daného jazyka je konkrétní interpretace tohoto jazyka.

**Definice** 6.2.1. Signatura je dvojice $\langle\mathcal{R}, \mathcal{F}\rangle$, kde $\mathcal{R}, \mathcal{F}$ jsou disjunktní množiny symbolů (relační a funkční, ty zahrnují konstantní) spolu s danými aritami (tj. danými funkcí ar: $\mathcal{R} \cup$ $\mathcal{F} \rightarrow \mathbb{N}$ ) a neobsahující symbol '=' (ten je rezervovaný pro rovnost). 

Často ale budeme signaturu zapisovat jen výčtem symbolo̊, bude-li jejich arita a to, zda jsou relační nebo funkční, zřejmé z kontextu.

Strukturu dané signatury získáme tak, že na nějaké neprázdné doméně zvolíme realizace (také říkáme interpretace) všech relačních a funkčních symbolů (a konstant), tj. konkrétní relace resp. funkce příslušných arit. (V případě konstantního symbolu je jeho realizací zvolený prvek z domény.)

6.3.1 **Jazyk**

Při specifikaci jazyka nejprve stanovíme, v jakého typu jsou struktury, které chceme popisovat, tj. určíme signaturu. Dále přidáme informaci, zda je jazyk $s$ rovností nebo ne, tj. zda ve formulích můžeme také používat symbol '=' vyjadřující rovnost (identitu) prvků v doméně struktur. ${ }^{10}$ Do jazyka patří následující: 
- spočetně mnoho proměnných $x_0, x_1, x_2, \ldots$ (ale píšeme také $x, y, z, \ldots ;$ množinu všech proměnných označíme Var), 
- relační, funkční a konstantní symboly ze signatury, a symbol = jde-li o jazyk s rovností, 
- univerzální a existenční kvantifikátory $(\forall x),(\exists x)$ pro každou proměnnou $x \in$ Var, $^{11}$ 
- symboly pro logické spojky $\neg, \wedge, \vee, \rightarrow, \leftrightarrow$ a závorky $($,$) .$

Podobně jako symbol $\square$ zastupující libovolnou binární logickou spojku budeme někdy psát $(Q x)$ pro kvantifikátor $(\forall x)$ nebo $(\exists x)$. 

Symbolům ze signatury říkáme mimologické, ostatní jsou logické. Jazyk musí obsahovat alespoň jeden relační symbol (bud' rovnost, nebo v signatuře)..$^{12}$ 

Jazyk tedy specifikujeme pomocí signatury a informace 's rovností' (popř. 'bez rovnosti'). 
**Definice** 6.2.3 (Struktura). Struktura v signatuře $\langle\mathcal{R}, \mathcal{F}\rangle$ je trojice $\mathcal{A}=\left\langle A, \mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}}\right\rangle$, kde 
- A je neprázdná množina, říkáme jí doména (také univerzum), 
- $\mathcal{R}^{\mathcal{A}}=\left\{R^{\mathcal{A}} \mid R \in \mathcal{R}\right\}$ kde $R^{\mathcal{A}} \subseteq A^{\operatorname{ar}(R)}$ je interpretace relačního symbolu $R$, 
- $\mathcal{F}^{\mathcal{A}}=\left\{f^{\mathcal{A}} \mid f \in \mathcal{F}\right\}$ kde $f^{\mathcal{A}}: A^{\operatorname{ar}(R)} \rightarrow A$ je interpretace funkčního symbolu $f$ (speciálně pro konstantní symbol $c \in \mathcal{F}$ máme $c^{\mathcal{A}} \in A$ ). 
6.3.2 Termy 
Termy jsou syntaktické 'výrazy' složené z proměnných, konstantních symbolů a funkčních symbolů.



### (P14) Atomická formule, formule, sentence, otevřené formule. 
- Atomická formule je nejjednodušší typ formule, která neobsahuje žádné další formule. Formule je jakýkoli výrok vytvořený pomocí symbolů daného jazyka. Sentence je formule, která neobsahuje žádné volné proměnné. Otevřená formule je formule, která obsahuje alespoň jednu volnou proměnnou.

**Definice** 6.3.1 (Termy). Termy jazyka $L$ jsou konečné nápisy definované induktivně: 
- každá proměnná a každý konstantní symbol z $L$ je term, 
- je-li $f$ funkční symbol z $L$ arity $n$ a jsou-li $t_1, \ldots, t_n$ termy, potom nápis $f\left(t_1, t_2, \ldots, t_n\right)$ je také term.
  
Množinu všech termů jazyka $L$ označíme $\operatorname{Term}_L$. 

Při zápisu termů obsahujících binární funkční symbol můžeme používat infixový zápis, např. $\left(t_1+t_2\right)$ znamená $+\left(t_1, t_2\right)$. Závorky někdy vynecháváme, je-li struktura termu ('priorita operátorů') zřejmá. 

Podterm je podřetězec termu, který je sám termem (je to tedy bud' celý term, nebo se vyskytl jako nějaké $t_i$ při konstrukci termu). 

Pokud term neobsahuje proměnnou, ř́káme mu konstantní (ground), například $((S(0)+$ $S(0)) \cdot S(S(0)))$ je konstantní term v jazyce aritmetiky. ${ }^{13}$ 

Strom termu $t$, označme Tree $(t)$, je definován podobně jako strom výroku, v listech jsou proměnné nebo konstantní symboly, ve vnitřních vrcholech jsou funkční symboly, jejichž arita je rovna počtu synů. 

**Definice** 6.3.3 (Atomická formule). Atomická formule jazyka $L$ je nápis $R\left(t_1, \ldots, t_m\right)$, kde $R$ je $n$-ární relační symbol z $L$ (včetně $=$ jde-li o jazyk s rovností) a $t_i \in \operatorname{Term}_L$. 

U binárních relačních symbolů často používáme infixový zápis, např. atomickou formuli $\leq(x, y)$ zapíšeme jako $x \leq y$, a (je-li jazyk s rovností) místo $=\left(t_1, t_2\right)$ budeme psát $t_1=t_2$. Příklad 6.3.4. Uved'me několik příkladů atomických formulí: 
- $R(f(f(x)), c, f(d))$ kde $R$ je ternární relační, $f$ unární funkční, $c, d$ konstantní symboly, 
- $(x \cdot x)+(y \cdot y) \leq(x+y) \cdot(x+y)$ v jazyce uspořádaných těles, 
- $x \cdot y \leq(S(0)+x) \cdot y \mathrm{v}$ jazyce aritmetiky, 
- $\neg(x \wedge y) \vee \perp=\perp \mathrm{v}$ jazyce Booleových algeber
   
**Definice** 6.3.5 (Formule). Formule jazyka $L$ jsou konečné nápisy definované induktivně: 
- každá atomická formule jazyka $L$ je formule,
- je-li $\varphi$ formule, potom ($\neg\varphi$) je také formule,
- jsou-li $\varphi, \psi$ formule, potom $(\varphi \wedge \psi),(\varphi \vee \psi),(\varphi \rightarrow \psi)$, a $(\varphi \leftrightarrow \psi)$ jsou také formule, 
- je-li $\varphi$ formule a $x$ proměnná, potom $((\forall x) \varphi)$ a $((\exists x) \varphi)$ jsou také formule.
  
Podformule je podřetězec, který je sám o sobě formulí. Strom formule, označíme Tree( $(\varphi)$, je definován takto: strom atomické formule $\varphi=R\left(t_1, \ldots, t_n\right)$ má $\mathrm{v}$ kořeni relační symbol $R$, a k němu jsou připojeny stromy Tree $\left(t_i\right)$. Není-li $\varphi$ atomická, strom zkonstruujeme obdobně jako strom výroku. ${ }^{14}$ Při zápisu formulí používáme obdobné konvence jako ve výrokové logice, $((\forall x) \varphi)$ tedy můžeme psát $(\forall x) \varphi \cdot{ }^{15}$ 
Volné a vázané proměnné 
Význam formule ${ }^{16}$ může, nebo nemusí záviset na proměnných, které se v ní vyskytují: srovnejte $x \leq 0$ a $(\exists x)(x \leq 0)$ (a co teprve $x \leq 0 \vee(\exists x)(x \leq 0)$ ). Nyní tento koncept upřesníme a zavedeme potřebnou terminologii. 

Výskytem proměnné $x$ ve formuli $\varphi$ myslíme list Tree $(\varphi)$ označený $x .{ }^{17}$ Výskyt je vázaný, je-li součástí nějaké podformule (podstromu) začínající $(Q x)$. Není-li výskyt vázaný, je volný. 
Proměnná je volná ve $\varphi$, pokud má ve $\varphi$ volný výskyt, a vázaná ve $\varphi$, pokud má ve $\varphi$ vázaný výskyt. Zápis $\varphi\left(x_1, \ldots, x_n\right)$ znamená, že $x_1, \ldots, x_n$ jsou všechny volné proměnné ve formuli $\varphi$. 

**Definice** 6.3.9 (Otevřená a uzavřená formule). Formule je otevřená, neobsahuje-li žádný kvantifikátor, a uzavřená (neboli sentence), pokud nemá žádnou volnou proměnnou 

Každá atomická formule je otevřená, otevřené formule jsou jen kombinace atomických pomocí logických spojek. Formule může být otevřená i uzavřená zároveň, v tom případě jsou všechny její termy konstantní. Formule je uzavřená, právě když nemá žádnou volnou proměnnou. 

### (P15) Instance formule, substituovatelnost, varianta formule. 
- Instance formule je formule získaná nahrazením některých nebo všech volných proměnných dané formule konkrétními termíny. Substituovatelnost označuje schopnost nahradit proměnné v formuli jinými termíny. Varianta formule je formule, která je syntakticky odlišná, ale sémanticky ekvivalentní.

**Definice** 6.3.13 (Substituovatelnost a instance). Term $t$ je substituovatelný za proměnnou $x$ ve formuli $\varphi$, pokud po simultánním nahrazení všech volných výskyti̊ $x$ ve $\varphi$ za $t$ nevznikne ve $\varphi$ žádný vázaný výskyt proměnné z $t$. $\mathrm{V}$ tom případě říkáme vzniklé formuli instance $\varphi$ vzniklá substitucí $t$ za $x$, a označujeme ji $\varphi(x / t)$. 

**Poznámka** 6.3.14. Všimněte si, že term $t$ není substituovatelný za $x$ do $\varphi$, právě když $x$ má volný výskyt v nějaké podformuli $\varphi$ tvaru $(Q y) \psi$ a proměnná $y$ se vyskytuje $\mathrm{v} t$. Speciálně, konstantní termy jsou vždy substituovatelné. 

**Definice** 6.3.15 (Varianta). Má-li formule $\varphi$ podformuli tvaru $(Q x) \psi$ a je-li $y$ proměnná, taková, že 
- $y$ je substituovatelná za $x$ do $\psi$ a 
- $y$ nemá volný výskyt v $\psi$, 
potom nahrazením podformule $(Q x) \psi$ formulí $(Q y) \psi(x / y)$ vznikne varianta formule $\varphi$ v podformuli $(Q x) \psi$. Varianta ř́íkáme i výsledku postupné variace ve více podformulích. 

Všimněte si, že požadavek na proměnnou $y$ z definice varianty je vždy splněn, pokud se $y$ nevyskytuje ve formuli $\varphi$. 

### (P16) Pravdivostní hodnota formule ve struktuře při ohodnocení, platnost formule ve struktuře. 
- Pravdivostní hodnota formule ve struktuře při ohodnocení je určena pomocí pravidel daného logického systému a specifické interpretace proměnných ve struktuře. Platnost formule ve struktuře znamená, že formule je pravdivá pro všechna ohodnocení proměnných ve struktuře.

6.4.2 Hodnota termu 
Mějme term $t$ jazyka $L=\langle\mathcal{R}, \mathcal{F}\rangle$ (s rovností nebo bez), a $L$-strukturu $\mathcal{A}=\left\langle A, \mathcal{R}^{\mathcal{A}}, F^{\mathcal{A}}\right\rangle$. Ohodnocení proměnných $\mathrm{v}$ množině $A$ je libovolná funkce $e:$ Var $\rightarrow A$. 

**Definice** 6.4.4 (Hodnota termu). Hodnota termu t ve struktuře $\mathcal{A}$ pr̆i ohodnocení e, kterou značíme $t^{\mathcal{A}}[e]$, je dána induktivně: 
- $x^{\mathcal{A}}[e]=e(x)$ pro proměnnou $x \in \operatorname{Var}$, 
- $c^{\mathcal{A}}[e]=c^{\mathcal{A}}$ pro konstantní symbol $c \in \mathcal{F}$, a 
- je-li $t=f\left(t_1, \ldots, t_n\right)$ složený term, kde $f \in \mathcal{F}$, potom: 
$$ 
t^{\mathcal{A}}[e]=f^{\mathcal{A}}\left(t_1^{\mathcal{A}}[e], \ldots, t_n^{\mathcal{A}}[e]\right) 
$$ 
**Poznámka** 6.4.5. Všimněte si, že hodnota termu závisí pouze na ohodnocení proměnných vyskytujících se v něm. Speciálně, je-li $t$ konstantní term, jeho hodnota na ohodnocení nezávisí. Obecně, každý term $t$ reprezentuje termovou funkci $f_t^{\mathcal{A}}: A^k \rightarrow A$, kde $k$ je počet proměnných v $t$, a konstantním termům odpovídají konstantní funkce. 

**Definice** 6.4.7 (Pravdivostní hodnota). Mějme formuli $\varphi$ v jazyce $L$, strukturu $\mathcal{A} \in \mathrm{M}(L)$, a ohodnocení proměnných $e: \operatorname{Var} \rightarrow A$. Pravdivostni hodnota $\varphi$ v $\mathcal{A}$ při ohodnocení $e$, $\mathrm{PH}^{\mathcal{A}}(\varphi)[e]$, je definována induktivně podle struktury formule: 
Pro atomickou formuli $\varphi=R\left(t_1, \ldots, t_n\right)$ máme 
$$ 
\mathrm{PH}^{\mathcal{A}}(\varphi)[e]= \begin{cases}1 & \text { pokud }\left(t_1^{\mathcal{A}}[e], \ldots, t_n^{\mathcal{A}}[e]\right) \in R^{\mathcal{A}}, \\ 0 & \text { jinak. }\end{cases} 
$$ 
Speciálně, je-li $\varphi$ tvaru $t_1=t_2$, potom $\mathrm{PH}^{\mathcal{A}}(\varphi)[e]=1$ právě $\operatorname{když~}\left(t_1^{\mathcal{A}}[e], t_2^{\mathcal{A}}[e]\right) \in=^{\mathcal{A}}$, kde $=^{-\mathcal{A}}$ je identita na $A$, tj. právě když $t_1^{\mathcal{A}}[e]=t_2^{\mathcal{A}}[e]$ (obě strany rovnosti jsou stejný prvek $a \in A$ ). 
Pravdivostní hodnota negace je definována takto: 
$$ 
\mathrm{PH}^{\mathcal{A}}(\neg \varphi)[e]=f_{\neg}\left(\mathrm{PH}^{\mathcal{A}}(\varphi)[e]\right)=1-\mathrm{PH}^{\mathcal{A}}(\varphi)[e] 
$$ 
Obdobně pro binární logické spojky, jsou-li $\varphi, \psi$ a $\square \in\{\wedge, \vee, \rightarrow, \leftrightarrow\}$, potom: 
$$ 
\mathrm{PH}^{\mathcal{A}}(\varphi \square \psi)[e]=f_{\square}\left(\mathrm{PH}^{\mathcal{A}}(\varphi)[e], \mathrm{PH}^{\mathcal{A}}(\psi)[e]\right) 
$$ 
Zbývá definovat pravdivostní hodnotu pro kvantifikátory, tj. formule tvaru $(Q x) \varphi$. Budeme potřebovat následující značení: Změníme-li v ohodnocení $e:$ Var $\rightarrow A$ hodnotu pro proměnnou $x$ na $a$, výsledné ohodnocení zapíšeme jako $e(x / a)$. Platí tedy $e(x / a)(x)=a$. Pravdivostní hodnotu pro $(Q x) \varphi$ definujeme takto: 
$$ 
\begin{aligned} 
& \mathrm{PH}^{\mathcal{A}}((\forall x) \varphi)[e]=\min _{a \in A}\left(\mathrm{PH}^{\mathcal{A}}(\varphi)[e(x / a)]\right) \\ 
& \mathrm{PH}^{\mathcal{A}}((\exists x) \varphi)[e]=\max _{a \in A}\left(\mathrm{PH}^{\mathcal{A}}(\varphi)[e(x / a)]\right) 
\end{aligned} 
$$ 
Tedy v ohodnocení $e$ nastavíme hodnotu proměnné $x$ postupně na všechny prvky $a \in A$ a požadujeme, aby PH byla rovna 1 vždy (v případě $\forall$ ) nebo alespoň jednou (v případě $\exists) .{ }^{19}$ 

**Poznámka** 6.4.8. Pravdivostní hodnota závisí pouze na ohodnocení volných proměnných. Speciálně, je-li $\varphi$ sentence, potom její pravdivostní hodnota nezávisí na ohodnocení. 
6.4.4 Platnost 
Na základě pravdivostní hodnoty už můžeme definovat klíčový pojem sémantiky, platnost. 

**Definice** 6.4.10 (Platnost ve struktuře). Mějme formuli $\varphi$ a strukturu $\mathcal{A}$ (ve stejném jazyce). 
- Je-li $e$ ohodnocení a $\operatorname{PH}^{\mathcal{A}}(\varphi)[e]=1$, potom říkáme, že $\varphi$ platí v $\mathcal{A}$ při ohodnocení e, a píšeme $\mathcal{A} \models \varphi[e]$. (V opačném případě říkáme, že $\varphi$ neplatí $v \mathcal{A}$ při ohodnocení $e$, a píšeme $\mathcal{A} \not \models \varphi[e]$.) 
- Pokud $\varphi$ platí v $\mathcal{A}$ při každém ohodnocení $e:$ Var $\rightarrow A$, potom říkáme, že $\varphi$ je pravdivá (platí) $v \mathcal{A}$, a píšeme $\mathcal{A} \models \varphi$. 
- Pokud $\mathcal{A} \models \neg \varphi$, tj. $\varphi$ neplatí v $\mathcal{A}$ při žádném ohodnocení (pro každé $e$ máme $\mathcal{A} \forall=\varphi[e]$ ), potom je $\varphi$ lživá $v \mathcal{A} .^{20}$ 

Shrňme několik jednoduchých vlastností, nejprve týkajících se platnosti při ohodnocení. Bud' $\mathcal{A}$ struktura, $\varphi, \psi$ formule, a $e$ ohodnocení. 
- $\mathcal{A}=\neg \varphi[e]$ právě když $\mathcal{A} \not \models \varphi[e]$, 
- $\mathcal{A} \models(\varphi \wedge \psi)[e]$ právě když $\mathcal{A} \models \varphi[e]$ a $\mathcal{A} \models \psi[e]$, 
- $\mathcal{A} \models(\varphi \vee \psi)[e]$ právě když $\mathcal{A} \models \varphi[e]$ nebo $\mathcal{A} \models \psi[e]$, 
- $\mathcal{A} \models(\varphi \rightarrow \psi)[e]$ právě když platí: jestliže $\mathcal{A} \models \varphi[e]$ potom $\mathcal{A} \models \psi[e]$, 
- $\mathcal{A} \models(\varphi \leftrightarrow \psi)[e]$ právě když platí: $\mathcal{A} \models \varphi[e]$ právě když $\mathcal{A} \models \psi[e]$, 
- $\mathcal{A} \models(\forall x) \varphi[e]$ právě když $\mathcal{A} \models \varphi[e(x / a)]$ pro všechna $a \in A$, 
- $\mathcal{A} \models(\exists x) \varphi[e]$ právě když $\mathcal{A} \models \varphi[e(x / a)]$ pro nějaké $a \in A$. 
- Je-li term $t$ substituovatelný za proměnnou $x$ do formule $\varphi$, potom 
$$ 
\mathcal{A} \models \varphi(x / t)[e] \text { právě když } \mathcal{A} \models \varphi[e(x / a)] \text { pro } a=t^{\mathcal{A}}[e] . 
$$ 
- Je-li $\psi$ varianta $\varphi$, potom $\mathcal{A} \models \varphi[e]$ právě když $\mathcal{A} \models \psi[e]$. 

### (P17) Kompletní teorie v predikátové logice, elementární ekvivalence. 
- Kompletní teorie v predikátové logice je teorie, ve které je každý výrok nebo jeho negace doložen. Elementární ekvivalence dvou struktur znamená, že každá formule, která je pravdivá v jedné struktuře, je pravdivá i v druhé struktuře.

**Definice** 6.5.1. Teorie je kompletní, je-li bezesporná a každá sentence je v ní bud' pravdivá, nebo lživá. 

Nemůžeme ale říci, že je teorie kompletní, právě když má jediný model. Máme-li totiž jeden model, dostáváme z něj nekonečně mnoho jiných, ale izomorfních modelů, tj. lišících se jen pojmenováním prvků univerza. ${ }^{23}$ Uvažovat jediný model 'až na izomorfismus' by ale nebylo dostatečné. Správným pojmem je tzv. elementární ekvivalence: 

**Definice** 6.5.2. Struktury $\mathcal{A}, \mathcal{B}$ (v témž jazyce) jsou elementárně ekvivalentní, pokud v nich platí tytéž sentence. Značíme $\mathcal{A} \equiv \mathcal{B}$. 

Pozorování 6.5.4. Teorie je kompletní, právě když má právě jeden model až na elementární ekvivalenci. 

### (P18) Podstruktura, generovaná podstruktura, expanze a redukt struktury. 
- Podstruktura je část struktury, která sama tvoří strukturu. Generovaná podstruktura je nejmenší podstruktura, která obsahuje určitou množinu prvků. Expanze struktury je struktura, která rozšiřuje původní strukturu o nové elementy nebo operace. Redukt struktury je struktura, která je získána odstraněním některých elementů nebo operací z původní struktury.

Podstruktura 
Pojem podstruktury zobecňuje podgrupy, podprostory vektorového tělesa, a indukované podgrafy grafu: vybereme nějakou podmnožinu $B$ univerza struktury $\mathcal{A}$, a vytvoříme na ní strukturu $\mathcal{B}$ stejné signatury, která 'zdědí' relace, operace, a konstanty. Abychom to mohli provést, potřebujeme, aby byla množina $B$ uzavřená na všechny operace a obsahovala všechny konstanty. 

**Definice** 6.6.1 (Podstruktura). Mějme strukturu $\mathcal{A}=\left\langle A, \mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}}\right\rangle \mathrm{v}$ signatuře $\langle\mathcal{R}, \mathcal{F}\rangle$. Struktura $\mathcal{B}=\left\langle B, \mathcal{R}^{\mathcal{B}}, \mathcal{F}^{\mathcal{B}}\right\rangle$ je (indukovaná) podstruktura $\mathcal{A}$, značíme $\mathcal{B} \subseteq \mathcal{A}$, jestliže 
- $\emptyset \neq B \subseteq A$ 
- $R^{\mathcal{B}}=R^{\mathcal{A}} \cap B^{\mathrm{ar}(\mathrm{R})}$ pro každý relační symbol $R \in \mathcal{R}$, 
- $f^{\mathcal{B}}=f^{\mathcal{A}} \cap\left(B^{\operatorname{ar}(\mathrm{f})} \times B\right)$ pro každý funkční symbol $f \in \mathcal{F}$ (tj. funkce $f^{\mathcal{B}}$ je restrikce $f^{\mathcal{A}}$ na množinu $B$, a její výstupy jsou všechny také z $B$ ), 
- speciálně, pro každý konstantní symbol $c \in \mathcal{F}$ máme $c^{\mathcal{B}}=c^{\mathcal{A}} \in B$.
  
Množina $C \subseteq A$ je uzavřená na funkci $f: A^n \rightarrow A$, pokud $f\left(x_1, \ldots, x_n\right) \in C$ pro všechna $x_i \in C$. Platí: 

Pozorování 6.6.2. Množina $\emptyset \neq C \subseteq A$ je univerzem podstruktury struktury $\mathcal{A}$, právě když je $C$ uzavřená na všechny funkce struktury $\mathcal{A}$ (včetně konstant). 
$\mathrm{V}$ tom případě říkáme této podstruktuře restrikce $\mathcal{A}$ na množinu $C$, a značíme ji $\mathcal{A} \uparrow C$. 
Platnost v podstrukture 
Jak je tomu s platností formulí v podstruktuře? Uved'me několik jednoduchých pozorování o otevřených formulích. 

Pozorování 6.6.4. Je-li $\mathcal{B} \subseteq \mathcal{A}$, potom pro každou otevřenou formuli $\varphi$ a ohodnocení proměnných e: $\operatorname{Var} \rightarrow B$ platí: $\mathcal{B} \models \varphi[e]$ právě $k d y \check{z} \mathcal{A} \models \varphi[e]$. 

**Důkaz**. Pro atomické formule je zřjejmé, dále snadno dokážeme indukcí podle struktury formule. 

**Důsledek** 6.6.5. Otevřená formule platí ve struktuře $\mathcal{A}$, právě když platí v každé podstruktuře $\mathcal{B} \subseteq \mathcal{A}$ 
Říkáme, že teorie $T$ je otevřená, jsou-li všechny její axiomy otevřené formule. 

**Důsledek** 6.6.6. Modely otevřené teorie jsou uzavřené na podstruktury, tj. každá podstruktura modelu otevřené teorie je také model této teorie. 
Generovaná podstruktura 
Co dělat, máme-li podmnožinu univerza, která není uzavřená na operace struktury? V tom případě uvážíme uzávěr této množiny na operace. ${ }^{26}$ 

**Definice** 6.6.9. Mějme strukturu $\mathcal{A}=\left\langle A, \mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}}\right\rangle$ a neprázdnou podmnožinu $X \subseteq A$. Označme jako $B$ nejmenší podmnožinu $A$, která obsahuje množinu $X$ a je uzavřená na všechny funkce struktury $\mathcal{A}$ (tj. také obsahuje všechny konstanty). Potom o podstruktuře $\mathcal{A}\lceil B$ říkáme, že je generovaná množinou $X$, a značíme ji $\mathcal{A}\langle X\rangle$. 

Přiklad 6.6.10. Uvažme struktury $\mathbb{\mathbb { Q }}=\langle Q,+, \cdot, 0\rangle, \underline{\mathbb{Z}}=\langle Z,+, \cdot, 0\rangle$, a $\underline{\mathbb{N}}=\langle N,+, \cdot, 0\rangle$. Potom $\underline{\mathbb{Q}}\langle\{1\}\rangle=\underline{\mathbb{N}}, \underline{\mathbb{Q}}\langle\{-1\}\rangle=\underline{\mathbb{Z}}$, a $\underline{\mathbb{Q}}\langle\{2\}\rangle$ je podstruktura $\underline{\mathbb{N}}$ na množině všech sudých čísel. 
Přiklad 6.6.11. Pokud $\mathcal{A}$ nemá žádné operace (ani konstanty), např. je-li to graf či uspořádání, potom není čím generovat, a $\mathcal{A}\langle X\rangle=\mathcal{A} \uparrow X$. 

Expanze a redukt 
Prozatím jsme konstruovali nové struktury změnou univerza. Můžeme ale také nechat univerzum stejné, a přidat resp. odebrat relace, operace, a konstanty. Výsledku takové operace říkáme expanze resp. redukt. Všimněte si, že jde o strukturu v jiné signatuře. 

**Definice** 6.6.12 (Expanze a redukt). Mějme jazyky $L \subseteq L^{\prime}, L$-strukturu $\mathcal{A}$, a $L^{\prime}$-strukturu $\mathcal{A}^{\prime}$ na stejné doméně $A=A^{\prime}$. Jestliže je interpretace každého symbolu [relačního, funkčního, konstantního] stejná [relace, funkce, konstanta] v $\mathcal{A}$ i v $\mathcal{A}^{\prime}$ potom říkáme, že struktura $\mathcal{A}^{\prime}$ je expanzí struktury $\mathcal{A}$ do jazyka $L^{\prime}$ (také říkáme, že je $L^{\prime}$-expanzí) a že struktura $\mathcal{A}$ je reduktem struktury $\mathcal{A}^{\prime}$ na jazyk $L$ (také říkáme, že je $L$-reduktem). 

Přiklad 6.6.13. Mějme grupu celých čísel $\langle\mathbb{Z},+,-, 0\rangle$. Potom struktura $\langle\mathbb{Z},+\rangle$ je jejím reduktem, zatímco struktura $\langle\mathbb{Z},+,-, 0, \cdot, 1\rangle$ (okruh celých čísel) je její expanzí. 
Přiklad 6.6.14. Mějme graf $\mathcal{G}=\left\langle G, E^{\mathcal{G}}\right\rangle$. Potom struktura $\left\langle G, E^G, c_v^{\mathcal{G}}\right\rangle_{v \in G} \mathrm{v}$ jazyce $\left\langle E, c_v\right\rangle_{v \in G}$, kde $c_v^{\mathcal{G}}=v$ pro všechny vrcholy $v \in G$, je expanzí $\mathcal{G}$ o jména prvků (z množiny $G$ ). 

### (P19) Definovatelnost ve struktuře. 
- Definovatelnost ve struktůře se týká schopnosti vyjádřit určité vlastnosti nebo relace mezi prvky struktury pomocí formule daného jazyka.

6.8 Definovatelnost ve struktuře 
Formuli s jednou volnou proměnnou $x$ můžeme chápat jako vlastnost prvků. V dané struktuře taková formule definuje množinu prvků, které tuto vlastnost splňují, tj. takových, že formule platí při ohodnocení $e$, ve kterém $e(x)=a$. Máme-li formuli se dvěma volnými proměnnými, definuje binární relaci, atp. Nyní tento koncept formalizujeme. Připomeňme, že zápis $\varphi\left(x_1, \ldots, x_n\right)$ znamená, že $x_1, \ldots, x_n$ jsou právě všechny volné proměnné formule $\varphi$. 

**Definice** 6.8.1 (Definovatelné množiny). Mějme formuli $\varphi\left(x_1, \ldots, x_n\right)$ a strukturu $\mathcal{A}$ v témž jazyce. Množina definovaná formulí $\varphi\left(x_1, \ldots, x_n\right)$ ve struktuře $\mathcal{A}$, značíme $\varphi^{\mathcal{A}}\left(x_1, \ldots, x_n\right)$, je: 
$$ 
\varphi^{\mathcal{A}}\left(x_1, \ldots, x_n\right)=\left\{\left(a_1, \ldots, a_n\right) \in A^n \mid \mathcal{A} \models \varphi\left[e\left(x_1 / a_1, \ldots, x_n / a_n\right)\right]\right\} 
$$ 
Zkráceně totéž zapíšeme také jako $\varphi^{\mathcal{A}}(\bar{x})=\left\{\bar{a} \in A^n \mid \mathcal{A} \models \varphi[e(\bar{x} / \bar{a})]\right\}$. 
Přǐklad 6.8.2. Uved'me několik příkladů: 
- Formule $\neg(\exists y) E(x, y)$ definuje množinu všech izolovaných vrcholo̊ v daném grafu. 
- Uvažme těleso reálných čísel $\mathbb{R}$. Formule $(\exists y)(y \cdot y=x) \wedge \neg(x=0)$ definuje množinu všech kladných reálných čísel. 
- Formule $x \leq y \wedge \neg(x=y)$ definuje $\mathrm{v}$ dané uspořádané množině $\left\langle S, \leq^S\right\rangle$ relaci ostrého uspor̃ádání $<$. 

Často se také hodí mluvit o vlastnostech prvků relativně k jiným prvkům dané struktury. To nelze vyjádřit čistě syntakticky, ale můžeme za některé z volných proměnných dosadit prvky struktury jako parametry. Zápisem $\varphi(\bar{x}, \bar{y})$ myslíme, že formule $\varphi$ má volné proměnné $x_1, \ldots, x_n, y_1, \ldots, y_k$ (pro nějaká $n, k$ ). 

**Definice** 6.8.3. Mějme formuli $\varphi(\bar{x}, \bar{y})$, kde $|\bar{x}|=n$ a $|\bar{y}|=k$, strukturu $\mathcal{A}$ v témž jazyce, a $k$-tici prvků $\bar{b} \in A^k$. Množina definovaná formulí $\varphi(\bar{x}, \bar{y})$ s parametry $\bar{b}$ ve struktuře $\mathcal{A}$, značíme $\varphi^{\mathcal{A}, \bar{b}}(\bar{x}, \bar{y})$, je: 
$$ 
\varphi^{\mathcal{A}, \bar{b}}(\bar{x}, \bar{y})=\left\{\bar{a} \in A^n \mid \mathcal{A} \models \varphi[e(\bar{x} / \bar{a}, \bar{y} / \bar{b})]\right\} 
$$ 
Pro strukturu $\mathcal{A}$ a podmnožinu $B \subseteq A$ označíme $\operatorname{Df}^n(\mathcal{A}, B)$ množinu všech množin definovatelných ve struktuře $\mathcal{A}$ s parametry pocházejícími z $B$. 
Přiklad 6.8.4. Pro $\varphi(x, y)=E(x, y)$ je $\varphi^{\mathcal{G}, v}(x, y)$ množina všech sousedů vrcholu $v$. 
Pozorování 6.8.5. Množina $\operatorname{Df}^n(\mathcal{A}, B)$ je uzavřená na doplněk, průnik, sjednocení, a obsahuje $\emptyset$ a $A^n$. Jde tedy o podalgebru potenční algebry $\mathcal{P}\left(A^n\right)$. 

### (P20) Extenze o definice. 
- Extenze o definice je rozšíření struktury nebo teorie o nové formule, které jsou definovány pomocí existujících symbolů a pravidel.

Nyní si ukážeme speciální druh konzervativní extenze, tvz. extenzi od definice nových (relačních, funkčních, konstantních) symbolů

**Definice** relačního symbolu 
Nejjednodušším případem je definování nového relačního symbolu $R\left(x_1, \ldots, x_n\right)$. Jako definice může sloužit libovolná formule s $n$ volnými proměnnými $\psi\left(x_1, \ldots, x_n\right)$. Přiklad 6.7.5. Uved'me nejprve několik příkladů: 
- Jakoukoliv teorii v jazyce s rovností můžeme rozšíritit o binární relační symbol $\neq$, který definujeme formulí $\neg x_1=x_2$. To znamená, že požadujeme, aby platilo: $x_1 \neq x_2 \leftrightarrow \neg x_1=$ $x_2$. 
- Teorii uspořádání můžeme rozšíritit o symbol < pro ostré uspořádání, který definujeme formulí $x_1 \leq x_2 \wedge \neg x_1=x_2$. To znamená, že požadujeme, aby platilo $x_1<x_2 \leftrightarrow x_1 \leq$ $x_2 \wedge \neg x_1=x_2$. 
- V aritmetice můžeme zavést symbol $\leq$, pomocí $x_1 \leq x_2 \leftrightarrow(\exists y)\left(x_1+y=x_2\right)$.
  
Nyní uvedeme definici:

**Definice** 6.7.6 (**Definice** relačního symbolu). Mějme teorii $T$ a formuli $\psi\left(x_1, \ldots, x_n\right)$ v jazyce $L$. Označme jako $L^{\prime}$ rozšírení jazyka $L$ o nový $n$-ární relační symbol $R$. Extenze teorie $T$ o definici $R$ formuli $\psi$ je $L^{\prime}$-teorie: 
$$ 
T^{\prime}=T \cup\left\{R\left(x_1, \ldots, x_n\right) \leftrightarrow \psi\left(x_1, \ldots, x_n\right)\right\} 
$$ 
Všimněte si, že každý model $T$ lze jednoznačně expandovat na model $T^{\prime}$. Z **Tvrzení** 6.7.3 potom ihned plyne následující: 

**Důsledek** 6.7.7. $T^{\prime}$ je konzervativní extenze $T$. 

Ukážeme si ještě, že nový symbol lze ve formulích nahradit jeho definicí, a získat tak (T-ekvivalentní) formuli v původním jazyce: 

**Tvrzení** 6.7.8. Pro každou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 
**Důkaz**. Je třeba nahradit atomické podformule s novým symbolem $R$, tj. tvaru $R\left(t_1, \ldots, t_n\right)$. Takovou podformuli nahradíme formulí $\psi^{\prime}\left(x_1 / t_1, \ldots, x_n / t_n\right)$, kde $\psi^{\prime}$ je varianta $\psi$ zaručující substituovatelnost všech termů, tj. například přejmenujeme všechny vázané proměnné $\psi$ na zcela nové (nevyskytující se ve formuli $\varphi^{\prime}$ ). 

**Definice** funkčního symbolu 

Nový funkční symbol definujeme obdobným způsobem, musíme si ale být jisti, že definice dává jednoznačnou možnost, jak nový symbol interpretovat 
Př̌klad 6.7.9. Opět začneme příklady: 
- V teorii grup můžeme zavést binární funkční symbol - ${ }_b$ pomocí + a unárního - takto: 
$$ 
x_1-{ }_b x_2=y \leftrightarrow x_1+\left(-x_2\right)=y 
$$ 
Je zřejmé, že pro každá $x, y$ existuje jednoznačné $z$ splňující definici. 
- Uvažme teorii lineárních uspořádání, tj. teorii uspořádání spolu s axiomem linearity $x \leq y \vee y \leq x$. Definujme binární funkční symbol min takto: 
$$ 
\min \left(x_1, x_2\right)=y \leftrightarrow y \leq x_1 \wedge y \leq x_2 \wedge(\forall z)\left(z \leq x_1 \wedge z \leq x_2 \rightarrow z \leq y\right) 
$$ 
Existence a jednoznačnost platí díky linearitě. Pokud bychom ale měli pouze teorii uspořádání, taková formule by nebyla dobrou definicí: v některých modelech by $\min \left(x_1, x_2\right)$ pro některé prvky neexistovalo, selhala by tedy požadovaná jednoznačnost. 

**Definice** 6.7.10 (**Definice** funkčního symbolu). Mějme teorii $T$ a formuli $\psi\left(x_1, \ldots, x_n, y\right)$ v jazyce $L$. Označme jako $L^{\prime}$ rozšírínení jazyka $L$ o nový $n$-ární funkční symbol $f$. Nechť v teorii $T$ platí: 
- axiom existence $(\exists y) \psi\left(x_1, \ldots, x_n, y\right)$, 
- axiom jednoznačnosti $\psi\left(x_1, \ldots, x_n, y\right) \wedge \psi\left(x_1, \ldots, x_n, z\right) \rightarrow y=z$. 
Potom extenze teorie $T$ o definici $f$ formuli $\psi$ je $L^{\prime}$-teorie: 
$$ 
T^{\prime}=T \cup\left\{f\left(x_1, \ldots, x_n\right)=y \leftrightarrow \psi\left(x_1, \ldots, x_n, y\right)\right\} 
$$ 
Formule $\psi$ tedy definuje v každém modelu $(n+1)$-ární relaci, a po této relaci požadujeme, aby byla funkcí, tj. aby pro každou $n$-tici prvků existovala jednoznačná možnost, jak ji rozšířit do $(n+1)$-tice, která je prvkem této relace. Všimněte si, že je-li definující formule $\psi$ tvaru $t\left(x_1, \ldots, x_n\right)=y$, kde $x_1, \ldots, x_n$ jsou proměnné $L$-termu $t$, potom axiomy existence a jednoznačnosti vždy platí. 
Opět platí, že každý model $T$ lze jednoznačně expandovat na model $T^{\prime}$, tedy: 
**Důsledek** 6.7.11. $T^{\prime}$ je konzervativní extenze $T$. 
A platí také analogické tvrzení o rozvádění definic: 
**Tvrzení** 6.7.12. Pro každou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 

**Definice** konstantního symbolu 

Konstantní symbol je speciálním případem funkčního symbolu arity 0 . Platí tedy stejná tvrzení. Axiomy existence a jednoznačnosti jsou: $(\exists y) \psi(y)$ a $\psi(y) \wedge \psi(z) \rightarrow y=z$. A extenze o definici konstantního symbolu $c$ formulí $\psi(y)$ je teorie $T^{\prime}=T \cup\{c=y \leftrightarrow \psi(y)\}$. Příklad 6.7.13. Ukážeme si dva příklady: 
- Teorii aritmetiky můžeme rozšírit o definici konstantního symbolu 1 formulí $\psi(y)$ tvaru $y=S(0)$, přidáme tedy axiom $1=y \leftrightarrow y=S(0)$ 
- Uvažme teorii těles a nový symbol $\frac{1}{2}$, definovaný formulí $y \cdot(1+1)=1$, tj. přidáním axiomu: 
$$ 
\frac{1}{2}=y \leftrightarrow y \cdot(1+1)=1 
$$ 
Zde nejde o korektní extenzi o definici, nebot' neplatí axiom existence. Ve dvouprvkovém tělese $\mathbb{Z}_2$ (a v každém tělese charakteristiky 2 ) nemá rovnice $y \cdot(1+1)=1$ řešení, nebot $1+1=0$ 
Pokud ale vezmeme teorii těles charakteristiky různé od 2 , tj. přidáme-li $\mathrm{k}$ teorii těles axiom $\neg(1+1=0)$, potom už půjde o korektní extenzi o definici. Například v tělese $\mathbb{Z}_3$ máme $\frac{1}{2} \mathbb{Z}_3=2$ 
Extenze o definice 
Máme-li $L$-teorii $T$ a $L^{\prime}$-teorii $T^{\prime}$, potom řekneme, že $T^{\prime}$ je extenzi $T$ o definice, pokud vznikla z $T$ postupnou extenzí o definice relačních a funkčních (příp. konstantních) symbolů. Vlastnosti, které jsme dokázali o extenzích o jeden symbol (at už relační nebo funkční), se snadno rozšíríí indukcí na více symbolů: 
**Důsledek** 6.7.14. Je-li $T^{\prime}$ extenze teorie $T$ o definice, potom platí: 
- Každý model teorie T lze jednoznačně expandovat na model $T^{\prime}$. 
- $T^{\prime}$ je konzervativní extenze $T$. 
- Pro každou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 
Na závěr ještě jeden příklad, na kterém si ukážeme i rozvádění definic: 
Příklad 6.7.15. V teorii $T=\{(\exists y)(x+y=0),(x+y=0) \wedge(x+z=0) \rightarrow y=z\}$ jazyka $L=\langle+, 0, \leq\rangle$ s rovností lze zavést $<$ a unární funkční symbol - přidáním axiomů: 
$$ 
\begin{aligned} 
-x=y & \leftrightarrow x+y=0 \\ 
x<y & \leftrightarrow x \leq y \wedge \neg(x=y) 
\end{aligned} 
$$ 
Formule $-x<y\left(\mathrm{v}\right.$ jazyce $\left.L^{\prime}=\langle+,-, 0, \leq,<\rangle\right)$ s rovností) je $\mathrm{v}$ této extenzi o definice ekvivalentní následující formuli: 
$(\exists z)((z \leq y \wedge \neg(z=y)) \wedge x+z=0)$ 

### (P21) Prenexní normální forma, Skolemova varianta. 
- Prenexní normální forma je formule predikátové logiky, ve které jsou všechny kvantifikátory umístěny na začátku formule. Skolemova varianta je transformace formule do tvaru, kde je každý existenční kvantifikátor nahrazen Skolemovo funkcí.

8.2.1 Prenexní normální forma 
Nejprve ukážeme postup, jakým můžeme z libovolné formule 'vytknout' kvantifikátory, tj. převést do tzv. prenexní normální formy, která začíná posloupností kvantifikátorů, a pokračuje už jen volnou formulí. 
**Definice** 8.2.2 (PNF). Formule $\varphi$ je v prenexní normální formě (PNF), je-li tvaru 
$$ 
\left(Q_1 x_1\right) \ldots\left(Q_n x_n\right) \varphi^{\prime} 
$$ 
kde $Q_i$ je kvantifikátor $\left(\forall\right.$ nebo $\exists$ ) a formule $\varphi^{\prime}$ je otevřená. Formuli $\varphi^{\prime}$ potom říkáme otevřené jádro $\varphi$ a $\left(Q_1 x_1\right) \ldots\left(Q_n x_n\right)$ je kvantifikátorový prefix. 

Je-li $\varphi$ formule v PNF a jsou-li všechny kvantifikátory univerzální, potom říkáme, že $\varphi$ je univerzální formule. 
Cílem této podsekce je ukázat následující tvrzení: 
**Tvrzení** 8.2.3 (Převod do PNF). Ke každé formuli $\varphi$ existuje ekvivalentní formule v prenexní normální formě. 

Algoritmus bude podobně jako převod do CNF založen na nahrazování podformulí ekvivalentními podformulemi, s cílem posunout kvantifikátory blíże ke kořeni stromu formule. Co myslíme ekvivalencí formulí $\varphi \sim \varphi^{\prime}$ ? To, že mají stejný význam, tj. v každém modelu a při každém ohodnocení proměnných mají tu samou pravdivostní hodnotu. Ekvivalentně, že platí $\models \varphi \leftrightarrow \varphi^{\prime}$. Budeme potr̃ebovat následující jednoduché pozorování: 

Pozorování 8.2.4. Nahradíme-li ve formuli $\varphi$ nějakou podformuli $\psi$ ekvivalentní formulí $\psi^{\prime}$, potom je i výsledná formule $\varphi^{\prime}$ ekvivalentní formuli $\varphi$. 
Převod je založen na opakovaném použití následujících syntaktických pravidel: 
Lemma 8.2.5. Označme jako $\bar{Q}$ kvantifikátor opačný ke $Q$. Necht́ $\varphi$ a $\psi$ jsou formule, a proměnná $x$ necht není volná ve formuli $\psi$. Potom platí: 
$$ 
\begin{aligned} 
\neg(Q x) \varphi & \sim(\bar{Q} x) \neg \varphi \\ 
(Q x) \varphi \wedge \psi & \sim(Q x)(\varphi \wedge \psi) \\ 
(Q x) \varphi \vee \psi & \sim(Q x)(\varphi \vee \psi) \\ 
(Q x) \varphi \rightarrow \psi & \sim(\bar{Q} x)(\varphi \rightarrow \psi) \\ 
\psi \rightarrow(Q x) \varphi & \sim(Q x)(\psi \rightarrow \varphi) 
\end{aligned} 
$$ 
8.2.2 Skolemova varianta 
Nyní jsme převedli naše axiomy na ekvivalentní sentence v prenexním tvaru. Pokud by některá sentence obsahovala pouze univerzální kvantifikátory, tj. byla tvaru 
$$ 
\left(\forall x_1\right) \ldots\left(\forall x_n\right) \varphi\left(x_1, \ldots, x_n\right) 
$$ 
kde $\varphi$ je otevřená, mohli bychom ji prostě nahradit jejím otevřeným jádrem $\varphi$, které je jí v tomto případě ekvivalentní. Jak si ale poradit s existenčními kvantifikátory, např. $(\exists x) \varphi(x)$, $(\forall x)(\exists y) \varphi(x, y)$, apod? Ty nejprve nahradíme jejich Skolemovou variantou. 

**Definice** 8.2.9 (Skolemova varianta). Mějme $L$-sentenci $\varphi$ v PNF, a necht všechny její vázané proměnné jsou různé. Necht' existenční kvantifikátory z prefixu $\varphi$ jsou $\left(\exists y_1\right), \ldots,\left(\exists y_n\right)$ (v tomto pořadí), a nechť pro každé $i$ jsou $\left(\forall x_1\right), \ldots,\left(\forall x_{n_i}\right)$ právě všechny univerzální kvantifikátory předcházející kvantifikátor $\left(\exists y_i\right)$ v prefixu $\varphi$. 

Označme $L^{\prime}$ rozšíření $L$ o nové $n_i$-ární funkční symboly $f_1, \ldots, f_n$, kde symbol $f_i$ je arity $n_i$, pro každé $i$. Skolemova varianta sentence $\varphi$ je $L^{\prime}$-sentence $\varphi_S$ vzniklá z $\varphi$ tak, že pro každé $i=1, \ldots, n$ : 
- odstraníme z prefixu kvantifikátor $\left(\exists y_i\right)$, a 
- substituujeme za proměnnou $y_i$ term $f_i\left(x_1, \ldots, x_{n_i}\right)$.
  
Tomuto procesu říkáme také skolemizace. 

Přiklad 8.2.10. Skolemova varianta sentence 
$$ 
\varphi=\left(\exists y_1\right)\left(\forall x_1\right)\left(\forall x_2\right)\left(\exists y_2\right)\left(\forall x_3\right) R\left(y_1, x_1, x_2, y_2, x_3\right) 
$$ 
je sentence 
$$ 
\varphi_S=\left(\forall x_1\right)\left(\forall x_2\right)\left(\forall x_3\right) R\left(f_1, x_1, x_2, f_2\left(x_1, x_2\right), x_3\right) 
$$ 
kde $f_1$ je nový konstantní symbol a $f_2$ je nový binární funkční symbol. 
**Poznámka** 8.2.11. Nezapomeňte, že při skolemizaci musíme vycházet ze sentence! Například, máme-li formuli $(\exists y) E(x, y)$, není $E(x, c)$ její Skolemova varianta. Musíme napřed provést generální uzávěr $(\forall x)(\exists y) E(x, y)$, a potom správně skolemizovat jako $(\forall x) E(x, f(x))$, což je ekvivalentní otevřené formuli $E(x, f(x))$ (která říká něco mnohem slabšího než $E(x, c)$ ). 

### (P22) Izomorfismus struktur, izomorfní spektrum, $\omega$-kategorická teorie. 
- Izomorfismus struktur je bijekce mezi strukturami, která zachovává všechny operace a relace. Izomorfní spektrum je množina velikostí struktur, které jsou izomorfní dané struktuře. $\omega$-kategorická teorie je teorie, ve které jsou všechny bezkonečné modely dané velikosti izomorfní.

9.2 Izomorfismus struktur 
Podívejme se blíže na pojem izomorfismu struktur, který zobecňuje izomorfismus grafů, vektorových prostorů, apod. Neformálně řečeno, struktury jsou izomorfní, pokud se liší jen pojmenováním konkrétních prvků. 

**Definice** 9.2.1. Mějme struktury $\mathcal{A}, \mathcal{B}$ jazyka $L=\langle\mathcal{R}, \mathcal{F}\rangle$. Izomorfismus $\mathcal{A}$ a $\mathcal{B}$ (nebo ' $\mathcal{A}$ na ') je bijekce $h: A \rightarrow B$ splñující následující vlastnosti: 
- Pro každý ( $n$-ární) funkční symbol $f \in \mathcal{F}$ a pro všechna $a_i \in A$ platí: 
$$ 
h\left(f^{\mathcal{A}}\left(a_1, \ldots, a_n\right)\right)=f^{\mathcal{B}}\left(h\left(a_1\right), \ldots, h\left(a_n\right)\right) 
$$ 
(Speciálně, je-li $c \in \mathcal{F}$ konstantní symbol, platí $h\left(c^{\mathcal{A}}\right)=c^{\mathcal{B}}$.) 
- Pro každý ( $n$-ární) relační symbol $R \in \mathcal{R}$ a pro všechna $a_i \in A$ platí: 
$$ 
R^{\mathcal{A}}\left(a_1, \ldots, a_n\right) \text { právě když } R^{\mathcal{B}}\left(h\left(a_1\right), \ldots, h\left(a_n\right)\right) 
$$ 
Pokud existuje, říkáme, že $\mathcal{A}$ a $\mathcal{B}$ jsou izomorfní (nebo ' $\mathcal{A}$ je izomorfní s $\mathcal{B}$ via $h$ ') a píšeme $\mathcal{A} \simeq \mathcal{B}\left(\right.$ nebo $\left.\mathcal{A} \simeq_h \mathcal{B}\right)$. Automorfismus $\mathcal{A}$ je izomorfismus $\mathcal{A}$ na $\mathcal{A}$ 
Všimněte si, že relace 'býti izomorfní' je ekvivalence. Ukažme si jeden příklad: 
Př́klad 9.2.2. Je-li $|X|=n$, je potenční algebra $\underline{\mathcal{P}(X)}=\langle\mathcal{P}(X),-, \cap, \cup, \emptyset, X\rangle$ izomorfní s Booleovou algebrou $\underline{2}^n=\left\langle\{0,1\}^n,-{ }_n, \wedge_n, \vee_n,(0, \ldots, 0),(1, \ldots, 1)\right\rangle$ (kde operace aplikujeme po složkách) via $h(A)=\chi_A$, kde $\chi_A$ je charakteristický vektor podmnožiny $A \subseteq X$. 
9.3 w-kategorické teorie 
Nyní se podíváme na teorie, které mají jediný spočetně nekonečný model (až na izomorfismus), říkáme jim $\omega$-kategorické. ${ }^6$ 

**Definice** 9.3.1 (Izomorfní spektrum, $\kappa$-kategoricita). Izomorfní spektrum teorie $T$ je počet $I(\kappa, T)$ modelů $T$ kardinality $\kappa$ až na izomorfismus, pro každou kardinalitu $\kappa$ (včetně transfinitních). Teorie $T$ je $\kappa$-kategorická, pokud $I(\kappa, T)=1$. 

Nadále nás bude zajímat jen případ $\kappa=\omega$, totiž teorie $\mathrm{s}$ jediným spočetně nekonečným modelem (až na izomorfismus). Jako příklad uved'me teorii hustého lineárního uspořádání bez konců: 
**Tvrzení** 9.3.2. Teorie DeLO je $\omega$-kategorická. 
**Důkaz**. Vezměme dva spočetně nekonečné modely $\mathcal{A}, \mathcal{B}$ a očíslujme jejich prvky: $A=\left\{a_i \mid\right.$ $i \in \mathbb{N}\}, B=\left\{b_i \mid i \in \mathbb{N}\right\}$. Indukcí podle $n$ lze díky hustotě nalézt posloupnost $h_0 \subseteq h_1 \subseteq$ $h_2 \subseteq \cdots$ prostých (parciálních) funkcí z $A$ do $B$, takových, že $\left\{a_0, \ldots, a_{n-1}\right\} \subseteq \operatorname{dom} h_n$, $\left\{b_0, \ldots, b_{n-1}\right\} \subseteq \operatorname{rng} h_n,{ }^7$ a zachovávají uspoř́ádáni ${ }^8$ Potom $\mathcal{A} \simeq \mathcal{B}$ via $h=\bigcup_{n \in \mathbb{N}} h_n$. 
**Důsledek** 9.3.3. Izomorfní spektrum teorie DeLO* je následující: 
$$ 
I\left(\kappa, \text { DeLO }^*\right)= \begin{cases}0 & \text { pro } \kappa \in \mathbb{N}, \\ 4 & \text { pro } \kappa=\omega .\end{cases} 
$$ 
Spočetné modely až na izomorfismus jsou napřiklad: 
$$ 
\mathbb{Q}=\langle\mathbb{Q}, \leq\rangle \simeq \mathbb{Q}\lceil(0,1), \mathbb{Q}\lceil(0,1], \mathbb{Q}\lceil[0,1), \mathbb{Q}\lceil[0,1] 
$$ 
**Důkaz**. Husté uspořádání jistě nemůže být konečné. Izomorfismus musí zobrazit nejmenší prvek na nejmenší prvek, a největší na největší. 

Pojem $\omega$-kategoricity lze chápat jako zeslabení pojmu kompletnosti. Platí následující užitečné kritérium: jazyce L. Je-li 
- L bez rovnosti, nebo 
- L s rovností a $T$ nemá konečné modely, potom je teorie $T$ kompletni. 

### (P23) Axiomatizovatelnost, konečná axiomatizovatelnost, otevřená axiomatizovatelnost. 
- Axiomatizovatelnost je schopnost vyjádřit všechny pravdivé výroky teorie pomocí konečné nebo spočetné množiny axiomů. Konečná axiomatizovatelnost znamená, že existuje konečná množina axiomů, která generuje všechny pravdivé výroky teorie. Otevřená axiomatizovatelnost se týká schopnosti vyjádřit všechny pravdivé výroky otevřené formule teorie pomocí množiny axiomů.

9.4 Axiomatizovatelnost 
Na závěr této kapitoly se podíváme, za jakých okolností lze 'popsat' (axiomatizovat) třídu modelů respektive teorii. Zajímat nás bude také kdy si vystačíme s konečně mnoha axiomy, a kdy to lze pomocí otevřených axiomů (kterých může být i nekonečně mnoho). Srovnejte s **Tvrzení**m 2.3.4 z výrokové logiky. 

**Definice** 9.4.1 (Axiomatizovatelnost). Mějme třídu struktur $K \subseteq \mathrm{M}_L$ v nějakém jazyce $L$. Ř́káme, že $K$ je 
- axiomatizovatelná, pokud existuje $L$-teorie $T$ taková, že $\mathrm{M}_L(T)=K$, 
- konečně axiomatizovatelná, pokud je axiomatizovatelná konečnou teorií, a 
- otevřeně axiomatizovatelná, pokud je axiomatizovatelná otevřenou teorií. 
O L-teorii $T^{\prime}$ říkáme, že je konečně resp. otevřeně axiomatizovatelná, pokud to platí o třídě modelů $K=\mathrm{M}_L\left(T^{\prime}\right)$. 
Přiklad 9.4.2. Uved'me několik příkladů: 
- grafy nebo částečná uspořádání jsou konečně i otevřeně axiomatizovatelné, 
- tělesa jsou konečně, ale ne otevřeně axiomatizovatelná, 
- nekonečné grupy jsou axiomatizovatelné, ale ne konečně, 
- konečné grafy nejsou axiomatizovatelné. 
Proč tomu tak je ukážeme níže. 
Začněme jednoduchým faktem: 
Pozorování 9.4.3. Je-li $K$ axiomatizovatelná, musí být uzavřená na elementární ekvivalenci. 
Z věty o kompaktnosti snadno získáme následující tvrzení, pomocí kterého lze ukázat neaxiomatizovatelnost např. konečných grafů, konečných grup, konečných těles. 

**Věta** 9.4.4. Pokud má teorie libovolně velké konečné modely, potom má i nekonečný model. $V$ tom případě není třída všech jejích konečných modeluْ axiomatizovatelná. 
9.4.1 Konečná axiomatizovatelnost 
Ukážeme následující kritérium konečné axiomatizovatelnosti: jak třída struktur $K$ tak i $\bar{K}$ musí být axiomatizovatelné. 

**Věta** 9.4.6 (O konečné axiomatizovatelnosti). Mějme třídu struktur $K \subseteq \mathrm{M}_L$ a uvažme také její doplněk $\bar{K}=\mathrm{M}_L \backslash K$. Potom $K$ je konečně axiomatizovatelná, právě když $K i \bar{K}$ jsou axiomatizovatelné. 
9.4.2 Otevřená axiomatizovatelnost 
Pro otevřenou axiomatizovatelnost existuje jednoduché sémantické kritérium: třída jejích modelů musí být uzavřená na podstruktury. Platí dokonce ekvivalence, dokážeme ale jen jednu implikaci (důkaz druhé je obtížnější). 

**Věta** 9.4.9. Pokud je teorie T otevřeně axiomatizovatelná, potom je každá podstruktura modelu $T$ také modelem $T$. 

**Poznámka** 9.4.10. Platí i obrácená implikace: Je-li každá podstruktura modelu $T$ také modelem, potom je $T$ otevřeně axiomatizovatelná. **Důkaz** zde ale neuvedeme. 

**Důkaz**. Necht' $T^{\prime}$ je otevřená axiomatizace $T$. Mějme model $\mathcal{A} \models T^{\prime}$ a podstrukturu $\mathcal{B} \subseteq \mathcal{A}$. Pro každou formuli $\varphi \in T^{\prime}$ platí $\mathcal{B} \models \varphi$ (nebot $\varphi$ je otevřená), tedy i $\mathcal{B} \models T^{\prime}$. 

### (P24) Rekurzivní axiomatizace, rekurzivní axiomatizovatelnost, rekurzivně spočetná kompletace. 
- Rekurzivní axiomatizace je proces definování množiny axiomů pomocí rekurzivního pravidla. Rekurzivní axiomatizovatelnost je schopnost vyjádřit všechny pravdivé výroky teorie pomocí rekurzivně definované množiny axiomů. Rekurzivně spočetná kompletace je proces doplnění rekurzivně definované množiny axiomů o další axiomy tak, aby byla kompletní.

10.1 Rekurzivní axiomatizace a rozhodnutelnost 
$\mathrm{V}$ důkazových systémech, kterými jsme se zabývali (tablo metoda, rezoluce, hilbertův kalkulus) jsme povolili, aby teorie $T$, ve které dokazujeme, byla nekonečná. Vůbec jsem se ale zatím nezabývali tím, jak je zadaná. Pokud chceme ověřit, že je daný objekt (tablo, rezoluční strom, posloupnost formulí) korektním důkazem, potřebujeme nějaký algoritmický př́stup ke všem axiomům $T$. 

Jednou z možností by bylo požadovat enumerátor $T$, tj. algoritmus, který vypisuje na výstup axiomy z $T$, a každý axiom někdy vypíše. ${ }^2$ Potom by bylo snadné potvrdit, že je daný důkaz korektní. Pokud bychom ale dostali důkaz, který použil chybný axiom, který v $T$ není, nikdy bychom se to nedozvěděli: nekonečně dlouho bychom čekali, zda jej enumerátor přeci jen nevypíše. Požadujeme proto silnější vlastnost, která umožňuje rozpoznat i chybné důkazy rekurzivní axiomatizaci $:^3$ 

**Definice** 10.1.1 (Rekurzivní axiomatizace). Teorie $T$ je rekurzivně axiomatizovaná, pokud existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $\varphi \in T$. 

**Poznámka** 10.1.2. Ve skutečnosti by nám stačil enumerátor pro $T$, pokud by bylo garantováno, že vypisuje axiomy v lexikografickém uspořádání. To už je ekvivalentní rekurzivní axiomatizaci. (Rozmyslete si proč.) 
${ }^1$ Viz přednáška NTIN090 Základy složitosti a vyčíslitelnosti. 
${ }^2$ Nutným předpokladem je, aby $T$ byla spočetná. K tomu stačí předpokládat, že jazyk je spočetný. 
${ }^3$ Slovo rekurzivní zde neznamená běžně známou rekurzi, ale odkazuje na formalizaci algoritmu pomocí 'rekurzivních funkcí' od Gödela. Rekurzivní funkce zde znamená totéž, co vyčíslitelná nějakým Turingovým strojem, a teorii vyčíslitelnosti (computability theory) se někdy také říká recursion theory. 
10.1.2 Rekurzivní axiomatizovatelnost 
$\mathrm{V}$ předchozí kapitole, konkrétně v Sekci 9.4 , jsme se zabývali otázkou, kdy lze popsat nějakou třídu struktur [resp. teorii] pomocí axiomů [určitého tvaru]. Nyní se zaměřme na otázku, kdy to lze udělat algoritmicky. 

**Definice** 10.1.8 (Rekurzivní axiomatizovatelnost). Třída $L$-struktur $K \subseteq \mathrm{M}_L$ je rekurzivně axiomatizovatelná, pokud existuje rekurzivně axiomatizovaná $L$-teorie $T$ taková, že $K=M_L(T)$. Teorie $T^{\prime}$ je rekurzivně axiomatizovatelná, pokud je rekurzivně axiomatizovatelná třída jejích modelů, neboli pokud je $T^{\prime}$ ekvivalentní nějaké rekurzivně axiomatizované teorii. 

**Poznámka** 10.1.9. Podobně bychom mohli definovat rekurzivně spočetnou axiomatizovatelnost. 
Ukažme si následující jednoduché tvrzení: 
**Tvrzení** 10.1.10. Je-li $\mathcal{A}$ konečná struktura v konečném jazyce s rovností, potom je teorie $\operatorname{Th}(\mathcal{A})$ rekurzivně axiomatizovatelná. 
10.1.1 Rekurzivně spočetná kompletace 
Požadavek kompletnosti je příliš silný, ukážeme, že stačí pokud jsme schopni efektivně popsat všechny kompletní jednoduché extenze. ${ }^5$ 

**Definice** 10.1.5 (Rekurzivně spočetná kompletace). Řekneme, že teorie $T$ má rekurzivně spočetnou kompletaci, pokud (nějaká) množina až na ekvivalenci všech jednoduchých kompletních extenzí teorie $T$ je rekurzivně spočetná, tj. existuje algoritmus, který pro danou vstupní dvojici přirozených čísel $(i, j)$ vypíše na výstup $i$-tý axiom $j$-té extenze (v nějakém pevně daném uspořádání ${ }^6$ ), nebo odpoví, že takový axiom už neexistuje. ${ }^7$ 

**Tvrzení** 10.1.6. Pokud je teorie $T$ rekurzivně axiomatizovaná a má rekurzivně spočetnou kompletaci, potom je $T$ rozhodnutelná. 
${ }^4$ Zde nám stačí enumerátor axiomů $T$, nebo postupně generujeme všechny sentence (např. v lexikografickém pořadí) a pro každou testujeme, zda je axiomem. 
${ }^5 \mathrm{~T} j$. 'všechny modely až na elementární ekvivalenci'. 
${ }^6$ Zde potřebujeme, aby byl jazyk spočetný. 
${ }^7$ Jeli extenzí méně než $j$, nebo má-li $j$-tá extenze méně než $i$ axiomů. 

### (P25) Rozhodnutelná a částečnĕ rozhodnutelná teorie. 
- Rozhodnutelná teorie je teorie, pro kterou existuje algoritmus, který dokáže rozhodnout pravdivost libovolného výroku teorie. Částečně rozhodnutelná teorie je teorie, pro kterou existuje algoritmus, který dokáže rozhodnout pravdivost libovolného výroku.

Zaměříme se na otázku, zda můžeme v dané teorii $T$ 'algoritmicky rozhodovat pravdu' (tj. platnost vstupní formule). Pokud ano, říkáme, že je teorie rozhodnutelná. To je ale poměrně silná vlastnost, definujeme proto také částečnou rozhodnutelnost, která znamená, že pokud formule platí, algoritmus nám to řekne, ale pokud neplatí, nikdy se nemusíme dočkat odpovědi. 
**Definice** 10.1.3 (Rozhodnutelnost). O teorii $T$ říkáme, že je 
- rozhodnutelná, pokud existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $T \models \varphi$, 
- částečně rozhodnutelná, pokud existuje algoritmus, který pro každou vstupní formuli: 
- pokud $T \models \varphi$, doběhne a odpoví "ano", 
- pokud $T \not \models \varphi$, bud' nedoběhne, nebo doběhne a odpoví "ne".
  
Můžeme jako obvykle předpokládat, že $\varphi$ v definici je sentence. Ukážeme si jednoduché tvrzení:

**Tvrzení** 10.1.4. Necht $T$ je rekurzivně axiomatizovaná. Potom: 
(i) T je částečně rozhodnutelná, 
(ii) je-li T navíc kompletní, potom je rozhodnutelná. 


## Seznam lehkých otázek 
### (L1) Množinu modelů nad konečným jazykem lze axiomatizovat výrokem v CNF, výrokem v DNF. 
**Tvrzení** 2.3.4. Mějme konečný jazyk $\mathbb{P}$ a libovolnou množinu modelů $M \subseteq \mathrm{M}_{\mathbb{P}}$. Potom existuje výrok $\varphi_{\mathrm{DNF}} v$ DNF a výrok $\varphi_{\mathrm{CNF}}$ v CNF takový, že $M=\mathrm{M}_{\mathbb{P}}\left(\varphi_{\mathrm{DNF}}\right)=\mathrm{M}_{\mathbb{P}}\left(\varphi_{\mathrm{CNF}}\right)$. Konkrétně: 
$$ 
\begin{aligned} 
\varphi_{\mathrm{DNF}} & =\bigvee_{v \in M} \bigwedge_{p \in \mathbb{P}} p^{v(p)} \\ 
\varphi_{\mathrm{CNF}} & =\bigwedge_{v \in \bar{M}} \bigvee_{p \in \mathbb{P}} \overline{p^{v(p)}}=\bigwedge_{v \notin M} \bigvee_{p \in \mathbb{P}} p^{1-v(p)} 
\end{aligned} 
$$ 
**Důkaz**. Pro výrok $\varphi_{\mathrm{DNF}}$ viz důkaz **Tvrzení** 2.2.14, každá elementární konjunkce popisuje jeden model. Výrok $\varphi_{\mathrm{CNF}}$ je duální k výroku $\varphi_{\mathrm{DNF}}^{\prime}$ sestrojenému pro doplněk $M^{\prime}=\bar{M}$. Nebo můžeme dokázat přímo: modely klauzule $C_v=\bigvee_{p \in \mathbb{P}} p^{1-v(p)}$ jsou všechny modely kromě $v$, $\mathrm{M}_C=\mathrm{M}_P \backslash\{v\}$, tedy každá klauzule $\mathrm{v}$ konjunkci zakazuje jeden nemodel. 

$$ 
\begin{aligned} 
& \mathbb{P}_1=\{p, q, r\} \\ 
& \mathbb{P}_2=\left\{p_0, p_1, p_2, p_3, \ldots\right\}=\left\{p_i \mid i \in \mathbb{N}\right\} 
\end{aligned} 
$$ 
Do jazyka patří kromě výrokových proměnných také logické symboly: symboly pro logické spojky $\neg, \wedge, \vee, \rightarrow, \leftrightarrow$ a závorky $($,$)$ . Budeme ale pro jednoduchost mluvit o "jazyce $\mathbb{P}$ ". 

**Tvrzení** 2.2.14. Množiny logických spojek $\{\neg, \wedge, \vee\} a\{\neg, \rightarrow\}$ jsou univerzální. 
**Důkaz**. Mějme funkci $f:\{0,1\}^n \rightarrow\{0,1\}$, resp. množinu modelů $M=f^{-1}[1] \subseteq\{0,1\}^n$. Náš jazyk bude $\mathbb{P}=\left\{p_1, \ldots, p_n\right\}$. Pokud by množina $M$ obsahovala jediný model, např. $v=(1,0,1,0)$ mohli bychom ji reprezentovat výrokem $\varphi_v=p_1 \wedge \neg p_2 \wedge p_3 \wedge \neg p_4$, který říká 'musím být model $v$ '. Pro obecný model $v$ bychom výrok $\varphi_v$ zapsali takto: 
$$ 
\varphi_v=p_1^{v_1} \wedge p_2^{v_2} \wedge \cdots \wedge p_n^{v_n}=\bigwedge_{i=1}^n p_i^{v\left(p_i\right)}=\bigwedge_{p \in \mathbb{P}} p^{v(p)} 
$$ 
kde zavádíme následující užitečné značení: $p^{v(p)}$ je výrok $p$ pokud $v(p)=1$, a výrok $\neg p$ pokud $v(p)=0$ 

Obsahuje-li množina $M$ více modelů, řekneme 'musím být alespoň jeden z modelů z $M$ ': 
$$ 
\varphi_M=\bigvee_{v \in M} \varphi_v=\bigvee_{v \in M} \bigwedge_{p \in \mathbb{P}} p^{v(p)} 
$$ 
Zřejmě platí $M_{\mathbb{P}}\left(\varphi_M\right)=M$ neboli $f_{\varphi_M, \mathbb{P}}=f$. (Pokud $M=\emptyset$, potom z definice $\bigvee_{v \in M} \varphi_v=$ L. $)^{16}$ 

Univerzálnost $\{\neg, \rightarrow\}$ plyne z univerzálnosti $\{\neg, \wedge, \vee\}$ a faktu, že konjunkci a disjunkci můžeme vyjádřit pomocí negace a implikace: $p \wedge q \sim \neg(p \rightarrow \neg q)$ a $p \vee q \sim \neg p \rightarrow q$. 

**Důsledek** 2.3.6. Každý výrok (v libovolném, i nekonečném jazyce $\mathbb{P}$ ) je ekvivalentní nějakému výroku v CNF a nějakému výroku v DNF. 

**Důkaz**. I když je jazyk $\mathbb{P}$ nekonečný, výrok $\varphi$ obsahuje jen konečně mnoho výrokových proměnných, můžeme tedy použít **Tvrzení** 2.3.4 pro jazyk $\mathbb{P}^{\prime}=\operatorname{Var}(\varphi)$, a množinu modelů $M=\mathrm{M}_{\mathbb{P}^{\prime}}(\varphi)$. Protože $M=\mathrm{M}_{\mathbb{P}^{\prime}}\left(\varphi_{\mathrm{DNF}}\right)=\mathrm{M}_{\mathbb{P}^{\prime}}\left(\varphi_{\mathrm{CNF}}\right)=M$, máme $\varphi \sim \varphi_{\mathrm{DNF}} \sim \varphi_{\mathrm{CNF}}$. 

### (L2) Algebra výroků bezesporné teorie nad konečným jazykem je izomorfní potenční algebře. 
Podívejme se na věc abstraktněji. Formálně, uvažujeme množinu ekvivalenčních tříd na množině všech výroků $\mathrm{VF}_{\mathbb{P}}$, kterou označíme $\mathrm{VF}_{\mathbb{P}} / \sim$. Prvky této množiny jsou množiny ekvivalentních výroků, např. $[p \rightarrow q]_{\sim}=\{p \rightarrow q, \neg p \vee q, \neg(p \wedge \neg q), \neg p \vee q \vee q, \ldots\}$. A máme zobrazení $h: \mathrm{VF}_{\mathrm{P}} / \sim \rightarrow \mathcal{P}\left(\mathrm{M}_{\mathrm{P}}\right)$ (kde $\mathcal{P}(X)$ je množina všech podmnožin $X$ ) definované předpisem: 
$$ 
h\left([\varphi]_{\sim}\right)=\mathrm{M}(\varphi) 
$$ 
tj. třídě ekvivalentních výroků přiř̌adíme množinu modelů libovolného z nich. Je snadné ověřit, že toto zobrazení je korektně definované (nezáleží na tom, jaký výrok z třídy ekvivalence jsme si vybrali) a prosté, a že je-li jazyk $\mathbb{P}$ konečný, je $h$ dokonce bijekce. (Ověřte!) 
Na množině $\mathrm{VF}_{\bar{F}} / \sim$ můžeme zavést operace $\neg, \wedge, \vee$ pomocí předpisu 
$$ 
\begin{aligned} 
\neg[\varphi]_{\sim} & =[\neg \varphi]_{\sim} \\ 
{[\varphi]_{\sim} \wedge[\psi]_{\sim} } & =[\varphi \wedge \psi]_{\sim} \\ 
{[\varphi]_{\sim} \vee[\psi]_{\sim} } & =[\varphi \vee \psi]_{\sim} 
\end{aligned} 
$$ 
tedy vybereme reprezentanta resp. reprezentanty, a provedeme operaci s nimi, např. 'konjunkce' tříd $[p \rightarrow q]_{\sim}$ a $[q \vee \neg r]_{\sim}$ je: 
$$ 
[p \rightarrow q]_{\sim} \wedge[q \vee \neg r]_{\sim}=[(p \rightarrow q) \wedge(q \vee \neg r)]_{\sim} 
$$ 
Přidáme-li také konstanty $\perp=[\perp]_{\sim}$ a $\top=[\top]_{\sim}$, dostáváme (matematickou) strukturu ${ }^{26}$ 
$$ 
\mathbf{A} \mathbf{V}_{\mathbb{P}}=\left\langle\mathrm{VF}_{\mathrm{P}} / \sim ; \neg, \wedge, \vee, \perp, \top\right\rangle 
$$ 
které ř́káme algebra výroků jazyka $\mathbb{P}$. Je to příklad tzv. Booleovy algebry. To znamená, že její operace se 'chovají' jako operace ${ }^{-}, \cap, \cup$ na množině všech podmnožin $\mathcal{P}(X)$ nějaké neprázdné množiny $X$, a konstanty odpovídají $\emptyset, X$ (takové Booleově algebře říkáme potenční algebra). ${ }^{27}$ 
Zobrazení $h: \mathrm{VF}_{\mathrm{P}} / \sim \rightarrow \mathcal{P}\left(\mathrm{M}_{\mathbb{P}}\right)$ je tedy zobrazení z algebry výroků $\mathbf{A V}_{\mathbb{P}}$ na potenční algebru 
$$ 
\mathcal{P}\left(\mathrm{M}_{\mathbb{P}}\right)=\left\langle\mathcal{P}\left(\mathrm{M}_{\mathbb{P}}\right) ;-, \cap, \cup, \emptyset, \mathrm{M}_{\mathbb{P}}\right\rangle 
$$ 
a je-li jazyk konečný, je to bijekce. Toto zobrazení 'zachovává' operace a konstanty, tj. platí $h(\perp)=\emptyset, h(\top)=\mathrm{M}_{\mathbb{P}}, \mathrm{a}$ 
$$ 
\begin{aligned} 
h\left(\neg[\varphi]_{\sim}\right) & =\overline{h\left([\varphi]_{\sim}\right)}=\overline{\mathrm{M}(\varphi)}=\mathrm{M}_{\mathrm{P}} \backslash \mathrm{M}(\varphi) \\ 
h\left([\varphi]_{\sim} \wedge[\psi]_{\sim}\right) & =h\left([\varphi]_{\sim}\right) \cap h\left([\psi]_{\sim}\right)=\mathrm{M}(\varphi) \cap \mathrm{M}(\psi) \\ 
h\left([\varphi]_{\sim} \vee[\psi]_{\sim}\right) & =h\left([\varphi]_{\sim}\right) \cup h\left([\psi]_{\sim}\right)=\mathrm{M}(\varphi) \cup \mathrm{M}(\psi) 
\end{aligned} 
$$ 
Takovému zobrazení říkáme homomorfismus Booleových algeber, a je-li to bijekce, jde o izomorfismus. 
**Poznámka** 2.5.2. Tyto vztahy můžeme také využít při hledání modelů: například pro výrok $\varphi \rightarrow(\neg \psi \wedge \chi)$ platí (s využitím toho, že $\left.\mathrm{M}\left(\varphi \rightarrow \varphi^{\prime}\right)=M\left(\neg \varphi \vee \varphi^{\prime}\right)\right)$ : 
$$ 
\mathrm{M}(\varphi \rightarrow(\neg \psi \wedge \chi))=\overline{\mathrm{M}(\varphi)} \cup(\overline{\mathrm{M}(\psi)} \cap \mathrm{M}(\chi)) 
$$ 
Všechny předchozí úvahy můžeme také relativizovat vzhledem k dané teorii $T$ v jazyce $\mathbb{P}$, a to tak, že ekvivalenci $\sim$ nahradíme $T$-ekvivalencí $\sim_T$ a množinu modelů jazyka $\mathrm{M}_{\mathbb{P}}$ nahradíme množinou modelů teorie $\mathrm{M}_{\mathbb{P}}(T)$. Dostáváme: 
$$ 
\begin{aligned} 
h(\perp) & =\emptyset, \\ 
h(\top) & =\mathrm{M}(T) \\ 
h\left(\neg[\varphi]_{\sim_T}\right) & =\mathrm{M}(T) \backslash \mathrm{M}(T, \varphi) \\ 
h\left([\varphi]_{\sim_T} \wedge[\psi]_{\sim_T}\right) & =\mathrm{M}(T, \varphi) \cap \mathrm{M}(T, \psi) \\ 
h\left([\varphi]_{\sim_T} \vee[\psi]_{\sim_T}\right) & =\mathrm{M}(T, \varphi) \cup \mathrm{M}(T, \psi) 
\end{aligned} 
$$ 
Výslednou algebru výroků vzhledem $k$ teorii $T$ označíme $\mathbf{A V}_{\mathbb{P}}(T)$. Algebra výroků jazyka je tedy totéž co algebra výroků vzhledem k prázdné teorii. Z technických důvodů potřebujeme, aby $\mathrm{M}(T)$ byla neprázdná, tj. $T$ musí být bezesporná. Shrňme naše úvahy: 

**Důsledek** 2.5.3. Je-li $T$ bezesporná teorie nad konečným jazykem $\mathbb{P}$, potom je algebra výroků $\mathbf{A} \mathbf{V}_{\mathbb{P}}(T)$ izomorfní potenční algebr̆e $\mathcal{P}\left(\mathrm{M}_{\mathbb{P}}(\mathbf{T})\right.$ ) prostřednictvím zobrazení $h\left([\varphi]_{\sim_T}\right)=$ $M(T, \varphi)$ 

Víme tedy, že negace, konjunkce, a disjunkce odpovídají doplňku, průniku a sjednocení množin modelů, a že chceme-li najít počet výroků až na ekvivalenci resp. T-ekvivalenci, stačí určit počet příslušných množin modelů. Shrňme si několik takových výpočtů ve formě tvrzení, jeho důkaz necháme jako cvičení. 

**Tvrzení** 2.5.4. Mějme n-prvkový jazyk $\mathbb{P}$ a bezespornou teorii $T$ mající právě $k$ modelů. Potom v jazyce $\mathbb{P}$ existuje až na ekvivalenci: 
- $2^{2^n}$ výroků (resp. teorí́), 
- $2^{2^n-k}$ výroků pravdivých (resp. lživých) v $T$, 
- $2^{2^n}-2 \cdot 2^{2^n-k}$ výroků nezávislých $v T$, 
- $2^k$ jednoduchých extenzí teorie $T$ (z toho 1 sporná), 
- $k$ kompletních jednoduchých extenzí $T$. 
Dále až na $T$-ekvivalenci existuje: 
- $2^k$ výroku, 
- 1 výrok pravdivý vT, 1 lživý vT, 
- $2^k-2$ výroků nezávislých $v T$. 

### (L3) 2-SAT, Algoritmus implikačního grafu, jeho korektnost. 
3.2 2-SAT a implikační graf 
Výrok $\varphi$ je $\mathrm{v} k$-CNF, pokud je $\mathrm{v}$ CNF a každá klauzule má nejvýše $k$ literáll̊. Problému $k$-SAT se ptá, zda je daný $k$-CNF formule splnitelná. Pro $k \geq 3$ je $k$-SAT nadále NP-úplný, každou CNF formuli lze zakódovat do 3-CNF formule: 

Cvičení 3.1. Ukažte, že pro každý výrok $\varphi \mathrm{v}$ CNF existuje ekvisplnitelný výrok v $\varphi^{\prime} 3$-CNF (tj. $\varphi$ je splnitelný, právě když $\varphi^{\prime}$ je splnitelný), který lze zkonstruovat v lineárním čase. 
Pro problém 2-SAT ale existuje polynomiální (dokonce lineární) algoritmus, který si nyní představíme. Algoritmus využívá tzv. implikačniho grafu. Ukážeme si postup na příkladě: 
Přiklad 3.2.1. Mějme následující 2-CNF výrok $\varphi$ : 
$$ 
\left(\neg p_1 \vee p_2\right) \wedge\left(\neg p_2 \vee \neg p_3\right) \wedge\left(p_1 \vee p_3\right) \wedge\left(p_3 \vee \neg p_4\right) \wedge\left(\neg p_1 \vee p_5\right) \wedge\left(p_2 \vee p_5\right) \wedge p_1 \wedge \neg p_4 
$$ 
Implikační graf 
Implikační graf 2-CNF výroku $\varphi$ je založený na myšlence, že 2-klauzuli $\ell_1 \vee \ell_2$ (kde $\ell_1, \ell_2$ jsou literály) lze chápat jako dvojici implikací: $\overline{\ell_1} \rightarrow \ell_2$ a $\overline{\ell_2} \rightarrow \ell_1 \cdot{ }^4$ Například, z klauzule $\neg p_1 \vee p_2$ vzniknou implikace $p_1 \rightarrow p_2$ a také , $\neg p_2 \rightarrow \neg p_1$. Tedy pokud $p_1$ platí v nějakém modelu, musí platit i $p_2$, a pokud $p_2$ neplatí, nesmí platit ani $p_1$. Jednotkovou klauzuli $\ell$ můžeme také vyjádřit pomocí implikace jako $\bar{\ell} \rightarrow \ell$, např. z $p_1$ dostáváme $\neg p_1 \rightarrow p_1$. 

Implikační graf $\mathcal{G}_{\varphi}$ je tedy orientovaný graf, jehož vrcholy jsou všechny literály (proměnné z $\operatorname{Var}(\varphi)$ a jejich negace) a hrany jsou dané implikacemi popsanými výše: 
- $V\left(\mathcal{G}_{\varphi}\right)=\{p, \neg p \mid p \in \operatorname{Var}(\varphi)\}$ 
- $E\left(\mathcal{G}_{\varphi}\right)=\left\{\left(\overline{\ell_1}, \ell_2\right),\left(\overline{\ell_2}, \ell_1\right) \mid \ell_1 \vee \ell_2\right.$ je klauzule $\left.\varphi\right\} \cup\{(\bar{\ell}, \ell) \mid \ell$ je jednotková klauzule $\varphi\}$ 
$\mathrm{V}$ našem příkladě máme množinu vrcholů 
$$ 
V\left(\mathcal{G}_{\varphi}\right)=\left\{p_1, p_2, p_3, p_4, p_5, \neg p_1, \neg p_2, \neg p_3, \neg p_4, \neg p_5\right\} 
$$ 
a hrany jsou: 
$$ 
\begin{aligned} 
E\left(\mathcal{G}_{\varphi}\right)= & \left\{\left(p_1, p_2\right),\left(\neg p_2, \neg p_1\right),\left(p_2, \neg p_3\right),\left(p_3, \neg p_2\right),\left(\neg p_1, p_3\right),\left(\neg p_3, p_1\right),\left(\neg p_3, \neg p_4\right),\right. \\ 
& \left.\left(p_4, p_3\right),\left(p_1, p_5\right),\left(\neg p_5, \neg p_1\right),\left(\neg p_2, p_5\right),\left(\neg p_5, p_2\right),\left(\neg p_1, p_1\right),\left(p_4, \neg p_4\right)\right\} 
\end{aligned} 
$$ 
3.2.1 Silně souvislé komponenty 
Nyní musíme najít komponenty silné souvislosti ${ }^5$ tohoto grafu. V našem příkladě dostáváme následující komponenty: $C_1=\left\{p_4\right\}, C_2=\left\{\neg p_5\right\}, C_3=\left\{\neg p_1, \neg p_2, p_3\right\}, \overline{C_3}=\left\{p_1, p_2, \neg p_3\right\}$, $\overline{C_2}=\left\{p_5\right\}, \overline{C_1}=\left\{\neg p_4\right\}$ 

Všechny literály v jedné komponentě musí být ohodnoceny stejně. Pokud bychom tedy našli dvojici opačných literálů v jedné komponentě, znamená to, že výrok je nesplnitelný. V opačném případě vždy můžeme najít splňující ohodnocení, jak si dokážeme v **Tvrzení** 3.2.2. Potřebujeme zajistit, aby z žádné komponenty ohodnocené 1 nevedla hrana do komponenty ohodnocené 0 . Provedeme-li kontrakci komponent, výsledný graf $\mathcal{G}_{\varphi}^*$ je acyklický (každý cyklus byl uvnitř nějaké komponenty), a můžeme ho tedy nakreslit v topologickém uspořádání (tj. uspořádání na přímce, kde hrany vedou jen doprava), viz Obrázek 3.2. 

Při hledání splňujícího ohodnocení (pokud nám nestačí informace, že výrok je splnitelný) potom postupujeme tak, že vezmeme nejlevější dosud neohodnocenou komponentu, ohodnotíme ji 0 , opačnou komponentu ohodnotíme 1, a postup opakujeme dokud zbývá nějaká 
${ }^5$ Silná souvislost znamená, že existuje orientovaná cesta $\mathrm{z} u$ do $v$ i z $v$ do $u$, neboli každé dva vrcholy $\mathrm{v}$ jedné komponentě leží v orientovaném cyklu. A naopak, každý orientovaný cyklus leží uvnitř nějaké komponenty. neohodnocená komponenta. Například, topologické uspořádání na Obrázku 3.3 odpovídá modelu $v=(1,1,0,0,1)$ 
Na závěr shrneme naše úvahy do následujícího tvrzení: 
**Tvrzení** 3.2.2. Výrok $\varphi$ je splnitelný, právě když žádná silně souvislá komponenta $v \mathcal{G}_{\varphi}$ neobsahuje dvojici opačných literálů $\ell, \bar{\ell}$. 

**Důkaz**. Každý model, neboli splňující ohodnocení, musí ohodnotit všechny literály ze stejné komponenty stejnou hodnotou. ( $\mathrm{V}$ opačném případě by nutně existovala implikace $\ell_1 \rightarrow \ell_2$, kde $\ell_1 \mathrm{v}$ modelu platí ale $\ell_2$ neplatí.) $\mathrm{V}$ jedné komponentě tedy nemohou být opačné literály. 
Naopak předpokládejme, že žádná komponenta neobsahuje dvojici opačných literálo̊, a ukažme, že potom existuje model. Označme $\mathcal{G}_{\varphi}^*$ graf vzniklý z $\mathcal{G}_{\varphi}$ kontrakcí silně souvislých komponent. Tento graf je acyklický, zvolme nějaké topologické uspořádání. Model zkonstruujeme tak, že zvolíme první dosud neohodnocenou komponentu v našem topologickém uspořádání, všechny literály v ní obsažené ohodnotíme 0 , a opačné literály ohodnotíme 1. Takto pokračujeme dokud nejsou všechny komponenty ohodnoceny. 

Proč v takto získaném modelu platí výrok $\varphi$ ? Kdyby ne, neplatila by některá z klauzulí. Jednotková klauzule $\ell$ musí platit, nebot $\mathrm{v}$ grafu $\mathcal{G}_{\varphi}$ máme hranu $\bar{\ell} \rightarrow \ell$. Stejná hrana je i v grafu komponent, tedy $\bar{\ell}$ předchází v topologickém uspořádání komponentu obsahující $\ell$. Při konstrukci modelu jsme museli ohodnotit $\bar{\ell}$ dříve než $\ell$, tedy $\bar{\ell}=0$ a $\ell=1$. Podobně, 2-klauzule $\ell_1 \vee \ell_2$ také musí platit: máme hrany $\overline{\ell_1} \rightarrow \ell_2$ a $\overline{\ell_2} \rightarrow \ell_1$. Pokud jsme $\ell_1$ ohodnotili dř́ive než $\ell_2$, museli jsme kvůli hraně $\overline{\ell_1} \rightarrow \ell_2$ ohodnotit $\overline{\ell_1}=0$, tedy $\ell_1$ platí. Podobně pokud jsme ohodnotili nejdříve $\ell_2$, musí být $\overline{\ell_2}=0$ a $\ell_2=1$. 

### (L4) Horn-SAT, Algoritmus jednotkové propagace, jeho korektnost. 
3.3 Horn-SAT a jednotková propagace 
Nyní si ukážeme další fragment SATu řešitelný v polynomiálním čase, tzv. Horn-SAT neboli problém splnitelnosti hornovských výroků. Výrok je v hornovský (v Hornově tvaru) ${ }^6$, pokud je konjunkcí hornovských klauzulí, tj. klauzulí obsahujících nejvýše jeden *pozitivní literál. Význam Hornovských klauzulí vyplývá z ekvivalentního vyjádření ve formě implikace: 
$$ 
\neg p_1 \vee \neg p_2 \vee \cdots \vee \neg p_n \vee q \sim\left(p_1 \wedge p_2 \wedge \cdots \wedge p_n\right) \rightarrow q 
$$ 
Hornovské formule tedy dobře modelují systémy, kde splnění určitých podmínek zaručuje splnění jiné podmínky. Upozorněme, že jednotková klauzule $\ell$ je také hornovská. V kontextu logického programování se jí říká fakt, pokud je literál pozitivní, a cúl pokud je negativní. ${ }^7$ Hornovské formule s alespoň jedním pozitivním a alespoň jedním negativním literálem jsou pravidla. 

Přiklad 3.3.1. Příkladem výroku, který je v CNF, ale není hornovský, je třeba $\left(p_1 \vee p_2 \vee \neg p_3\right) \wedge$ $\left(\neg p_1 \vee p_3\right)$. Jako příklad, na kterém budeme ilustrovat algoritmus, nám poslouží následující hornovský výrok: 
$$ 
\varphi=\left(\neg p_1 \vee p_2\right) \wedge\left(\neg p_1 \vee \neg p_2 \vee p_3\right) \wedge\left(\neg p_3 \vee \neg p_4\right) \wedge\left(\neg p_5 \vee \neg p_4\right) \wedge p_4 
$$ 
Polynomiální algoritmus pro řešení problému Horn-SAT je založený na jednoduché myšlence jednotkové propagace: Pokud náš výrok obsahuje jednotkovou klauzuli, víme, jak musí být ohodnocenena výroková proměnná obsažená v této klauzuli. A tuto znalost můžeme propagovat-využít k zjednodušení výroku. 

Náš výrok $\varphi$ obsahuje jednotkovou klauzuli $p_4$. Víme tedy, že $\mathrm{v}$ každém jeho modelu $v \in \mathrm{M}(\varphi)$ musí platit $v\left(p_4\right)=1$. To ale znamená, že $\mathrm{v}$ libovolném modelu výroku $\varphi$ 
- každá klauzule obsahující pozitivní literál $p_4$ je splněna, můžeme ji tedy z výroku odstranit, 
- negativní literál $\neg p_4$ nemůže být splněn, můžeme ho tedy odstranit ze všech klauzulí, které ho obsahují. 

Tomu kroku se říká jednotková propagace. Výsledkem je následující zjednodušený výrok, který označíme $\varphi^{p_4}$ (obecně $\varphi^{\ell}$ máme-li jednotkovou klauzuli $\ell$ ): 
$$ 
\varphi^{p_4}=\left(\neg p_1 \vee p_2\right) \wedge\left(\neg p_1 \vee \neg p_2 \vee p_3\right) \wedge\left(\neg p_3 \vee \neg p_4\right) \wedge \neg p_5 
$$ 
Pozorování 3.3.2. Všimněte si, že $\varphi^{\ell}$ už neobsahuje literál $\ell$ ani $\ell$, a zřejmě platí, že modely $\varphi$ jsou právě modely $\left\{\varphi^{\ell}, \ell\right\}$, neboli modely $\varphi^{\ell}$ v původním jazyce $\mathbb{P}$, ve kterých platí $\ell$. 

Jednotkovou propagací jsme získali ve výroku $\varphi^{p_4}$ novou jednotkovou klauzuli $\neg p_5$, můžeme tedy pokračovat nastavením $v\left(p_5\right)=0$ a další jednotkovou propagací: 
$$ 
\left(\varphi^{p_4}\right)^{\neg p_5}=\left(\neg p_1 \vee p_2\right) \wedge\left(\neg p_1 \vee \neg p_2 \vee p_3\right) \wedge\left(\neg p_3 \vee \neg p_4\right) 
$$ 
${ }^6$ Matematik Alfred Horn objevil význam tohoto tvaru logických formulí (a položil tak základ logickému programování) v roce 1951 . 
${ }^7$ Nebot dokazujeme sporem, více v pozdější kapitole o rezoluci a Prologu. 
Výsledný výrok už neobsahuje jednotkovou klauzuli. To ale znamená, že každá klauzule obsahuje alespoň dva literály, a nejvýše jeden z nich může být pozitivní! (Zde potřebujeme hornovskost výroku.) Protože každá klauzule obsahuje negativní literál, stačí ohodnotit všechny zbývající proměnné 0 , a výrok bude splněn: $v\left(p_1\right)=v\left(p_2\right)=v\left(p_3\right)=0$. Dostáváme tedy model $v=(0,0,0,1,1)$. 
Přiklad 3.3.3. Co by se stalo, pokud by výrok nebyl splnitelný? Podívejme se na výrok 
$$ 
\psi=p \wedge(\neg p \vee q) \wedge(\neg q \vee r) \vee \neg r 
$$ 
a provádějme jednotkovou propagaci jako $\mathrm{v}$ předchozím příkladě: máme $v(p)=1$ a $\psi^p=$ $q \wedge(\neg q \vee r) \wedge \neg r$, dále $v(q)=1$ a $\left(\psi^p\right)^q=r \vee \neg r$. Tento výrok je nesplnitelný, nebot obsahuje dvojici opačných jednotkových klauzulí. 8 
Shrňme si nyní algoritmus pro řešení problému Horn-SAT: 
Algoritmus (Horn-SAT). vstup: výrok $\varphi$ v Hornově tvaru, výstup: model $\varphi$ nebo informace, že $\varphi$ není splnitelný 
1. Pokud $\varphi$ obsahuje dvojici opačných jednotkových klauzulí $\ell, \bar{\ell}$, není splnitelný. 
2. Pokud $\varphi$ neobsahuje žádnou jednotkovou klauzuli, je splnitelný, ohodnot všechny zbývající proměnné 0 . 
3. Pokud $\varphi$ obsahuje jednotkovou klauzuli $\ell$, ohodnot literál $\ell$ hodnotou 1 , proved' jednotkovou propagaci, nahrad' $\varphi$ výrokem $\varphi^{\ell}$, a vrat' se na začátek.
4. 
**Tvrzení** 3.3.4. Algoritmus je korektní. 
**Důkaz**. Korektnost plyne z Pozorování a z předchozí diskuze. 

### (L5) Algoritmus DPLL pro řešení SAT. 
3.4 DPLL algoritmus pro řešení problému SAT 
Na závěr kapitoly o problému splnitelnosti si představíme zdaleka nejpoužívanější algoritmus pro řešení obecného problému SAT, algoritmus DPLL. ${ }^9$ Ačkoliv v nejhorším případě má exponenciální složitost, v praxi funguje velmi efektivně. 

Algoritmus používá jednotkovou propagaci spolu s následujícím pozorováním: Řekneme, že literál $\ell$ má čistý výskyt $\mathrm{v} \varphi$, pokud se vyskytuje ve $\varphi$, ale opačný literál $\bar{\ell}$ se ve $\varphi$ nevyskytuje. Máme-li literál s čistým výskytem, můžeme jeho hodnotu nastavit na 1 , a splnit (a odstranit) tak všechny klauzule, které ho obsahují. Pokud výrok neumíme takto zjednodušit, rozvětvíme výpočet dosazením obou možných hodnot pro vybranou výrokovou proměnnou. 
${ }^8$ Jinými slovy, v dalším kroku bychom provedli jednotkovou propagaci $r$, odstranili jednotkovou klauzuli $r$, a ze zbývající jednotkové klauzule $\neg r$ bychom odstranili literál $\neg r$, čímž by vznikla prázdná klauzule, která je nesplnitelná. 
${ }^9$ Pojmenovaný po svých tvůrcích, Davis-Putnam-Logemann-Loveland, pochází z roku 1961. 
Algoritmus (DPLL). vstup: výrok $\varphi$ v CNF, výstup: model $\varphi$ nebo informace, že $\varphi$ není splnitelný 
1. Dokud $\varphi$ obsahuje jednotkovou klauzuli $\ell$, ohodnot' literál $\ell$ hodnotou 1 , proved' jednotkovou propagaci, a nahrad' $\varphi$ výrokem $\varphi^{\ell}$. 
2. Dokud existuje literál $\ell$, který má ve $\varphi$ čistý výskyt, ohodnot $\ell$ hodnotou 1 , a odstran̆ klauzule obsahující $\ell$. 
3. Pokud $\varphi$ neobsahuje žádnou klauzuli, je splnitelný. 
4. Pokud $\varphi$ obsahuje prázdnou klauzuli, není splnitelný. 
5. Jinak zvol dosud neohodnocenou výrokovou proměnnou $p$, a zavolej algoritmus rekurzivně na $\varphi \wedge p$ a na $\varphi \wedge \neg p$. 

To, že je algoritmus v nejhorším případě exponenciální, lze snadno nahlédnout na příkladě jediné klauzule $p_1 \vee p_2 \vee \cdots \vee p_n$. Korektnost není těžké ověřit. 
**Tvrzení** 3.4.1. Algoritmus DPLL řeší problém SAT. 

### (L6) **Věta** o konstantách. 
6.6.1 **Věta** o konstantách 
**Věta** o konstantách ř́íká (neformálně), že splnit formuli s volnou proměnnou je totéž, co splnit sentenci, ve které je tato volná proměnná nahrazena (substituována) novým konstantním symbolem (který není nijak svázaný žádnými axiomy). Klíčem je fakt, že tento nový symbol může být v modelech interpretován jako libovolný (tj. každý) prvek. Tento trik později využijeme v tablo metodě. 

**Věta** 6.6.15 (O konstantách). Mějme formuli $\varphi$ v jazyce $L$ s volnými proměnnými $x_1, \ldots, x_n$. Označme $L^{\prime}$ rozšíření jazyka o nové konstantní symboly $c_1, \ldots, c_n$ a bud' T' stejná teorie jako $T$ ale v jazyce $L^{\prime}$. Potom platí: 
$$ 
T \models \varphi \text { právě } k d y \check{z} T^{\prime} \models \varphi\left(x_1 / c_1, \ldots, x_n / c_n\right) 
$$ 
**Důkaz**. **Tvrzení** stačí dokázat pro jednu volnou proměnnou $x$ a jednu konstantu $c$, indukcí se snadno rozšíríí na $n$ konstant. 

Předpokládejme nejprve, že $\varphi$ platí v každém modelu teorie $T$. Chceme ukázat, že $\varphi(x / c)$ platí v každém modelu $\mathcal{A}^{\prime}$ teorie $T^{\prime}$. Vezměme tedy takový model $\mathcal{A}^{\prime}$ a libovolné ohodnocení $e:$ Var $\rightarrow A$ a ukažme, že $\mathcal{A}^{\prime} \models \varphi(x / c)[e]$ 

Označme jako $\mathcal{A}$ redukt $\mathcal{A}^{\prime}$ na jazyk $L$ ('zapomeneme' konstantu $\left.c^{\mathcal{A}^{\prime}}\right)$. Všimněte si, že $\mathcal{A}$ je model teorie $T$ (axiomy $T$ jsou tytéž jako $T^{\prime}$, neobsahují symbol $c$ ) tedy v něm platí $\varphi$. Protože dle předpokladu platí $\mathcal{A} \models \varphi\left[e^{\prime}\right]$ pro libovolné ohodnocení $e^{\prime}$, platí i pro ohodnocení $e\left(x / c^{\mathcal{A}^{\prime}}\right)$ ve kterém ohodnotíme proměnnou $x$ interpretací konstantního symbolu $c$ ve struktuře $\mathcal{A}^{\prime}$, máme tedy $\mathcal{A} \models \varphi\left[e\left(x / \mathcal{A}^{\mathcal{A}^{\prime}}\right)\right]$. To ale znamená, že $\mathcal{A}^{\prime} \models \varphi(x / c)[e]$, což jsme chtěli dokázat. 
Naopak, předpokládejme, že $\varphi(x / c)$ platí v každém modelu teorie $T^{\prime}$ a ukažme, že $\varphi$ platí v každém modelu $\mathcal{A}$ teorie $T$. Zvolme tedy takový model $\mathcal{A}$ a nějaké ohodnocení $e:$ Var $\rightarrow A$ a ukažme, že $\mathcal{A} \models \varphi[e]$ 

Označme jako $\mathcal{A}^{\prime}$ expanzi $\mathcal{A}$ do jazyka $L^{\prime}$, kde konstantní symbol $c$ interpretujeme jako prvek $c^{\mathcal{A}^{\prime}}=e(x)$. Protože dle předpokladu platí $\mathcal{A}^{\prime} \models \varphi(x / c)\left[e^{\prime}\right]$ pro všechna ohodnocení $e^{\prime}$, platí i $\mathcal{A}^{\prime} \models \varphi(x / c)[e]$, což ale znamená, že $\mathcal{A}^{\prime} \models \varphi[e]$. (Nebot' $e=e(x / c)$ a $\mathcal{A}^{\prime} \models \varphi(x / c)[e(x / c)]$ platí právě když $\mathcal{A}^{\prime} \models \varphi[e(x / c)]$.) Formule $\varphi$ ale neobsahuje $c$ (zde používáme, že $c$ je nový), máme tedy i $\mathcal{A} \models \varphi[e]$. 

### (L7) Vlastnosti extenze o definice. 
**Důsledek** 6.7.7. $T^{\prime}$ je konzervativní extenze $T$. 
Ukážeme si ještě, že nový symbol lze ve formulích nahradit jeho definicí, a získat tak ( $T^{\prime}$-ekvivalentní) formuli v původním jazyce: 
**Tvrzení** 6.7.8. Pro kaz̆dou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 
**Důkaz**. Je třeba nahradit atomické podformule s novým symbolem $R$, tj. tvaru $R\left(t_1, \ldots, t_n\right)$. Takovou podformuli nahradíme formulí $\psi^{\prime}\left(x_1 / t_1, \ldots, x_n / t_n\right)$, kde $\psi^{\prime}$ je varianta $\psi$ zaručující substituovatelnost všech termů, tj. například přejmenujeme všechny vázané proměnné $\psi$ na zcela nové (nevyskytující se ve formuli $\varphi^{\prime}$ ). 
**Důsledek** 6.7.11. $T^{\prime}$ je konzervativni extenze $T$. 
A platí také analogické tvrzení o rozvádění definic: 
**Tvrzení** 6.7.12. Pro kaz̆dou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 
**Důkaz**. Stačí dokázat pro formuli $\varphi^{\prime}$ s jediným výskytem symbolu $f$; je-li výskytů více, aplikujeme postup induktivně, v případě vnořených výskytů v jednom termu $f(\ldots f(\ldots) \ldots)$ postupujeme od vnitřních $\mathrm{k}$ vnějším. 

Označme $\varphi^*$ formuli vzniklou $\mathrm{z} \varphi^{\prime}$ nahrazením termu $f\left(t_1, \ldots, t_n\right)$ novou proměnnou $z$. Formuli $\varphi$ zkonstruujeme takto: 
$$ 
(\exists z)\left(\varphi^* \wedge \psi^{\prime}\left(x_1 / t_1, \ldots, x_n / t_n, y / z\right)\right) 
$$ 
kde $\psi^{\prime}$ je varianta $\psi$ zaručující substituovatelnost všech termů. 
Mějme model $\mathcal{A}$ teorie $T^{\prime}$ a ohodnocení e. Označme $a=f^{\mathcal{A}}\left(t_1, \ldots, t_n\right)[e]$. Díky existenci a jednoznačnosti platí: 
$$ 
\mathcal{A} \models \psi^{\prime}\left(x_1 / t_1, \ldots, x_n / t_n, y / z\right)[e] \text { právě když } e(z)=a 
$$ 
Máme tedy $\mathcal{A} \models \varphi[e]$, právě když $\mathcal{A} \models \varphi^*[e(z / a)]$, právě když $\mathcal{A} \models \varphi^{\prime}[e]$. To platí pro libovolné ohodnocení $e$, tedy $\mathcal{A}=\varphi^{\prime} \leftrightarrow \varphi$ pro každý model $T^{\prime}$, tedy $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 
Extenze o definice 
Máme-li $L$-teorii $T$ a $L^{\prime}$-teorii $T^{\prime}$, potom řekneme, že $T^{\prime}$ je extenzí $T$ o definice, pokud vznikla z $T$ postupnou extenzí o definice relačních a funkčních (příp. konstantních) symbolů. Vlastnosti, které jsme dokázali o extenzích o jeden symbol (at už relační nebo funkční), se snadno rozšíríi indukcí na více symbolů: 
**Důsledek** 6.7.14. Je-li $T^{\prime}$ extenze teorie $T$ o definice, potom platí: 
- Každý model teorie T lze jednoznačně expandovat na model $T^{\prime}$. 
- $T^{\prime}$ je konzervativni extenze $T$. 
- Pro každou $L^{\prime}$-formuli $\varphi^{\prime}$ existuje L-formule $\varphi$ taková, že $T^{\prime} \models \varphi^{\prime} \leftrightarrow \varphi$. 

### (L8) Vztah definovatelných množin a automorfismů. 
**Tvrzení** 9.2.8. Je-li $D \subseteq A^n$ definovatelná ve struktuře $\mathcal{A}$, potom pro každý automorfismus $h \in \operatorname{Aut}(\mathcal{A})$ platí $h[D]=D(k d e 
 h[D]$ značí $\{(h(\bar{a}) \mid \bar{a} \in D\})$. 

Je-li $D$ definovatelná s parametry $\bar{b}$, platí totéž pro automorfismy identické na $\bar{b}$, tj. takové, $\check{z} e h(\bar{b})=\bar{b}\left(\right.$ neboli $h\left(b_i\right)=b_i$ pro všechna $\left.i\right)$. 

**Důkaz**. Ukážeme jen verzi s parametry. Nechł $D=\varphi^{\mathcal{A}, \bar{b}}(\bar{x}, \bar{y})$. Potom pro každé $\bar{a} \in A^n$ platí následující ekvivalence: 
$$ 
\begin{aligned} 
\bar{a} \in D & \Leftrightarrow \mathcal{A} \models \varphi[e(\bar{x} / \bar{a}, \bar{y} / \bar{b})] \\ 
& \Leftrightarrow \mathcal{A}=\varphi[(e \circ h)(\bar{x} / \bar{a}, \bar{y} / \bar{b})] \\ 
& \Leftrightarrow \mathcal{A}=\varphi[e(\bar{x} / h(\bar{a}), \bar{y} / h(\bar{b}))] \\ 
& \Leftrightarrow \mathcal{A}=\varphi[e(\bar{x} / h(\bar{a}), \bar{y} / \bar{b})] \\ 
& \Leftrightarrow h(\bar{a}) \in D . 
\end{aligned} 
$$ 

### (L9) Tablo metoda v jazyce s rovností. 
**Definice** 7.3.3 (Axiomy rovnosti). Axiomy rovnosti pro jazyk $L$ s rovností jsou následující: 
(i) $x=x$ 
(ii) $x_1=y_1 \wedge \cdots \wedge x_n=y_n \rightarrow f\left(x_1, \ldots, x_n\right)=f\left(y_1, \ldots, y_n\right)$ pro každý $n$-ární funkční symbol $f$ jazyka $L$, 
(iii) $x_1=y_1 \wedge \cdots \wedge x_n=y_n \rightarrow\left(R\left(x_1, \ldots, x_n\right) \rightarrow R\left(y_1, \ldots, y_n\right)\right)$ pro každý $n$-ární relační symbol $R$ jazyka $L$ včetně rovnosti. 
$\mathrm{Z}$ axiomů $(i)$ a $($ iii $)$ tedy plyne, že relace $=\mathcal{A}$ je ekvivalence na $A$, a axiomy (ii) a (iii) vyjadřují, že $={ }^{\mathcal{A}}$ je kongruencí $\mathcal{A}$. $\mathrm{V}$ tablo metodě $\mathrm{v}$ případě jazyka s rovností implicitně přidáme všechny axiomy rovnosti: 

**Definice** 7.3.4 (Tablo důkaz s rovností). Je-li $T$ teorie v jazyce $L$ s rovností, potom označme jako $T^*$ rozšíření teorie $T$ o generální uzávěry ${ }^9$ axiomů rovnosti pro jazyk $L$. Tablo důkaz z teorie $T$ je tablo důkaz z $T^*$, podobně pro tablo zamítnutí (a obecně jakékoliv tablo). 
Platí následující jednoduché pozorování: 
Pozorování 7.3.5. Jestliže $\mathcal{A} \models T^*$, potom platí $i \mathcal{A} /=\mathcal{A} \models T^*$, a ve struktuře $\mathcal{A} /=\mathcal{A}$ je symbol rovnosti interpretován jako identita. Na druhou stranu, v každém modelu, ve kterém je symbol rovnosti interpretován jako identita, platí axiomy rovnosti. 

Toto pozorování využijeme při konstrukci kanonického modelu, který budeme potřebovat v důkazu Věty o úplnosti. Nejprve ale dokážeme Větu o korektnosti. 

### (L10) **Věta** o kompaktnosti a její aplikace. 
**Důsledek** 4.4.5 (Konečnost důkazů). Pokud $T \vdash \varphi$, potom existuje $i$ konečný tablo důkaz $\varphi$ $z T$. 

**Důkaz**. Snadno plyne z Důsledku 4.4.4: stačí při konstrukci $\tau$ ignorovat kroky, které by prodloužily spornou větev. 
4.7 **Věta** o kompaktnosti 
Důležitým důsledkem vět o korektnosti a úplnosti je také tzv. **Věta** o kompaktnosti. ${ }^9$ Tento princip umožňuje převádět tvrzení o nekonečných objektech/procesech na tvrzení o (všech) jejich konečných částech. 

**Věta** 4.7.1 (O kompaktnosti). Teorie má model, právě když každá jeji konečná část má model. 

**Důkaz**. Každý model teorie $T$ je zjevně modelem každé její části. Druhou implikaci dokážeme nepřímým důkazem: Předpokládejme, že $T$ nemá model, tj. je sporná, a najděme konečnou část $T^{\prime} \subseteq T$, která je také sporná. 

Protože je $T$ sporná, platí $T \vdash \perp$ (zde potřebujeme Větu o úplnosti). Podle Důsledku 4.4.5 potom existuje konečný tablo důkaz $\tau$ výroku $\perp$ z $T$. Konstrukce tohoto důkazu má jen konečně mnoho kroků, použili jsme tedy jen konečně mnoho axiomů z $T$. Definujeme-li $T^{\prime}=\{\alpha \in T \mid$ T $\alpha$ je položka $\mathrm{v}$ tablu $\tau\}$, potom $\tau$ je také tablo důkaz sporu z teorie $T^{\prime}$. Teorie $T^{\prime}$ je tedy sporná konečná část $T$. 
4.7.1 Aplikace kompaktnosti 
Následující jednoduchou aplikaci Věty o kompaktnosti můžete chápat jako šablonu, kterou následuje i mnoho dalších, složitějších aplikací této věty. 

**Důsledek** 4.7.2. Spočetně nekonečný graf je bipartitní, právě když je každý jeho konečný podgraf bipartitní. 

**Důkaz**. Každý podgraf bipartitního grafu je zjevně také bipartitní. Ukažme opačnou implikaci. Graf je bipartitní, právě když je obarvitelný 2 barvami. Označme barvy 0,1 . 

Sestrojíme výrokovou teorii $T$ v jazyce $\mathbb{P}=\left\{p_v \mid v \in V(G)\right\}$, kde hodnota výrokové proměnné $p_v$ reprezentuje barvu vrcholu $v$. 
$$ 
T=\left\{p_u \rightarrow \neg p_v \mid\{u, v\} \in E(G)\right\} 
$$ 
Zřejmě platí, že $G$ je bipartitní, právě když $T$ má model. Podle Věty o kompaktnosti stačí ukázat, že každá konečná část $T$ má model. Vezměme tedy konečnou $T^{\prime} \subseteq T$. Bud' G' podgraf $G$ indukovaný na množině vrcholů, o kterých se zmiňuje teorie $T^{\prime}, \mathrm{tj} . V\left(G^{\prime}\right)=\{v \in$ $\left.V(G) \mid p_v \in \operatorname{Var}\left(T^{\prime}\right)\right\}$. Protože je $T^{\prime}$ konečná, je $G^{\prime}$ také konečný, a podle předpokladu je 2-obarvitelný. Libovolné 2-obarvení $V\left(G^{\prime}\right)$ ale určuje model teorie $T^{\prime}$. 
${ }^9$ Slovo kompaktnost pochází z kompaktních (tj. omezených a uzavr̃ených) mnoz̃in v Euklidovských prostorech, ve kterých lze z každé posloupnosti vybrat konvergentní podposloupnost. Můžete si představit posloupnost zvětšujících se konečných částí 'konvergující' k nekonečnému celku. 
7.5.2 **Věta** o kompaktnosti 
Stejně jako ve výrokové logice platí **Věta** o kompaktnosti, stejný je i její důkaz: 
**Věta** 7.5.3 (O kompaktnosti). Teorie má model, právě když každá její konečná část má model. 

**Důkaz**. Model teorie je zřejmě modelem každé její části. Naopak, pokud $T$ nemá model, je sporná, tedy $T \vdash \perp$. Vezměme nějaký konečný tablo důkaz $\perp$ z $T$. K jeho konstrukci stačí konečně mnoho axiomů $T$, ty tvoří konečnou podteorii $T^{\prime} \subseteq T$, která nemá model. 

### (L11) **Věta** o korektnosti rezoluce ve výrokové logice. 
5.3.1 Korektnost rezoluce 
Korektnost dokážeme snadno indukcí podle délky rezolučního důkazu. 
**Věta** 5.3.1 (O korektnosti rezoluce). Je-li formule $S$ rezolucí zamítnutelná, potom je $S$ nesplnitelná. 

**Důkaz**. Necht’ $S \vdash_R \square$ a vezměme nějaký rezoluční důkaz $C_0, C_1, \ldots, C_n=\square$. Předpokládejme pro spor, že $S$ je splnitelná, tedy $\mathcal{V} \models S$ pro nějaké ohodnocení $\mathcal{V}$. Indukcí podle $i$ dokážeme, že $\mathcal{V} \models C_i$. Pro $i=0$ to platí, nebot $C_0 \in S$. Pro $i>0$ máme dva případy: 
- $C_i \in S$, v tom případě $\mathcal{V} \models C_i$ plyne z předpokladu, že $\mathcal{V} \models S$, 
- $C_i$ je rezolventou $C_j, C_k$, kde $j, k<i$ : z indukčního předpokladu víme $\mathcal{V} \models C_j$ a $\mathcal{V} \models C_k$, $\mathcal{V} \models C_i$ plyne z korektnosti rezolučního pravidla. 
(Alternativně bychom mohli v důkazu postupovat indukcí podle hloubky rezolučního stromu.) 

### (L12) **Věta** o korektnosti rezoluce v predikátové logice. 
**Věta** 8.6.2 (O korektnosti rezoluce). Pokud je CNF formule $S$ rezolucí zamítnutelná, potom je nesplnitelná. 

**Důkaz**. Víme, že $S \vdash_R \square$, vezměme tedy nějaký rezoluční důkaz $\square$ z $S$. Kdyby existoval model $\mathcal{A} \models S$, díky korektnosti rezolučního pravidla bychom mohli dokázat indukcí podle délky důkazu, že i $\mathcal{A} \models \square$, což ale není možné. 

### (L13) Souvislost stromu dosazení a splnitelnosti CNF formule. 
5.3.2 Strom dosazení 
$\mathrm{V}$ důkazu úplnosti budeme potřebovat zkonstruovat rezoluční strom, jeho konstrukce je založena na tzv. stromu dosazení. Dosazením literálu do formule myslíme zjednodušení formule za předpokladu, že daný literál platí. Dosazení jsme už potkali v Sekci 3.3 při jednotkové propagaci: odstraníme klauzule obsahující tento literál, a z ostatních klauzulí odstraníme literál opačný. 

**Definice** 5.3.2 (Dosazení literálu). Je-li $S$ formule a $\ell$ literál, potom dosazením $\ell$ do $S$ myslíme formuli: 
$$ 
S^{\ell}=\{C \backslash\{\bar{\ell}\} \mid l \notin C \in S\} 
$$ 
Pozorování 5.3.3. Zde shrneme několik jednoduchých faktů o dosazení: 
- $S^{\ell}$ je výsledkem jednotkové propagace aplikované na $S \cup\{\{\ell\}\}$. 
- Pokud $S$ neobsahovala literál $\ell$ ani $\bar{\ell}$, potom $S^{\ell}=S$. 
- Pokud $S$ obsahovala jednotkovou klauzuli $\{\bar{\ell}\}$, potom $\square \in S^{\ell}$, tedy $S^{\ell}$ je sporná.
  
Klíčovou vlastnost dosazení vyjadřuje následující lemma: 

Lemma 5.3.4. $S$ je splnitelná, právě když je splnitelná $S^{\ell}$ nebo $S^{\bar{\ell}}$.

**Důkaz**. Mějme ohodnocení $\mathcal{V} \models S$, to nemůže obsahovat $\ell$ i $\bar{\ell}$ (musí být konzistentní); bez újmy na obecnosti předpokládejme, že $\bar{\ell} \notin \mathcal{V}$, a ukažme, že $\mathcal{V} \models S^{\ell}$. Vezměme libovolnou klauzuli v $S^{\ell}$. Ta je tvaru $C \backslash\{\bar{\ell}\}$ pro klauzuli $C \in S$ (neobsahující literál $\ell$ ). Víme, že $\mathcal{V} \models C$, protože ale $\mathcal{V}$ neobsahuje $\bar{\ell}$, muselo ohodnocení $\mathcal{V}$ splnit nějaký jiný literál $C$, takže platí i $\mathcal{V} \equiv C \backslash\{\bar{\ell}\}$ 

Naopak, předpokládejme že existuje ohodnocení $\mathcal{V}$ splňující $S^{\ell}$ (opět bez újmy na obecnosti). Protože se $\bar{\ell}$ (ani $\ell$ ) nevyskytuje $\mathrm{v} S^{\ell}$, platí také $\mathcal{V} \backslash\{\bar{\ell}\} \models S^{\ell}$. Ohodnocení $\mathcal{V}^{\prime}=$ $(\mathcal{V} \backslash\{\bar{\ell}\}) \cup\{\ell\}$ potom splňuje každou klauzuli $C \in S$ : pokud $\ell \in C$, potom $\ell \in C \cap \mathcal{V}^{\prime}$ a $C \cap \mathcal{V}^{\prime} \neq \emptyset$, jinak $C \cap \mathcal{V}^{\prime}=(C \backslash\{\bar{\ell}\}) \cap \mathcal{V}^{\prime} \neq \emptyset$ nebot $\mathcal{V} \backslash\{\bar{\ell}\} \models C \backslash\{\bar{\ell}\} \in S^{\ell}$. Ověřili jsme, že $\mathcal{V}^{\prime} \models S$, tedy $S$ je splnitelná. 

Zda je daná konečná formule splnitelná bychom tedy mohli zjišt’ovat rekurzivně (metodou rozděl a panuj), dosazením obou možných literálů pro (nějakou, třeba první) výrokovou proměnnou vyskytující se ve formuli, a rozvětvením výpočtu. V zásadě jde o podobný princip jako v algoritmu DPLL. Výslednému stromu říkáme strom dosazení.

**Důsledek** 5.3.6. Formule $S$ (nad spočetným jazykem) je nesplnitelná, právě když každá větev stromu dosazení obsahuje prázdnou klauzuli $\square$.

Důkaz. Pro konečnou formuli $S$ plyne z diskuze výše, můžeme snadno dokázat indukcí podle velikosti $\operatorname{Var}(S)$ :
- Je-li $|\operatorname{Var}(S)|=0$, máme $S=\emptyset$ nebo $S=\{\square\}$, v obou případech je strom dosazení jednoprvkový a tvrzení platí.
- V indukčním kroku vybereme libovolný literál $\ell \in \operatorname{Var}(S)$ a aplikujeme Lemma ??.
Je-li $S$ nekonečná a splnitelná, potom má splňující ohodnocení, to se 'shoduje' s odpovídající (nekonečnou) větví ve stromu dosazení. Je-li nekonečná a nesplnitelná, potom podle Věty o kompaktnosti existuje konečná část $S^{\prime} \subseteq S$, která je také nesplnitelná. Po dosazení pro všechny proměnné z $\operatorname{Var}\left(S^{\prime}\right)$ bude v každé větvi $\square$, to nastane po konečně mnoha krocích.


### (L14) Unifikační algoritmus (korektnost stačí vyslovit). 
Algoritmus (Unifikační algoritmus). 
- vstup: konečná množina výrazů $S \neq \emptyset$, 
- výstup: nejobecnější unifikace $\sigma$ pro $S$ nebo informace, že $S$ není unifikovatelná 
(0) nastav $S_0:=S, \sigma_0:=\emptyset, k:=0$ 
(1) pokud $\left|S_k\right|=1$, vrat' $\sigma=\sigma_0 \sigma_1 \cdots \sigma_k$ 
(2) zjisti, zda v $D\left(S_k\right)$ existuje proměnná $x$ a term $t$ neobsahující $x$ 
(3) pokud ano, nastav $\sigma_{k+1}:=\{x / t\}, S_{k+1}:=S_k \sigma_{k+1}, k:=k+1$, a jdi na (1) 
(4) pokud ne, odpověz, že $S$ není unifikovatelná 
**Poznámka** 8.4.11. Hledání proměnné $x$ a termu $t \mathrm{v}$ kroku (2) může být relativně výpočetně náročné. 

**Tvrzení** 8.4.13. Unifikační algoritmus je korektní. Pro každý vstup S skončí v konečně mnoha krocích, a je-li $S$ unifikovatelná, odpoví nejobecnější unifikaci $\sigma$, jinak odpoví, že $S$ neni unifikovatelná. 
Je-li S unifikovatelná, potom pro sestrojenou nejobecnější unifikaci $\sigma$ navíc platí, že je-li $\tau$ libovolná unifikace, potom $\tau=\sigma \tau$. 

### (L15) Nestandardní model pr̆irozených čísel. 
7.5.3 Nestandardní model přirozených čísel 
Na závěr této sekce si ukážeme, že existuje tzv. nestandardní model přirozených čísel. Klíčem je **Věta** o kompaktnosti. 

Necht $\underline{\mathbb{N}}=\langle\mathbb{N}, S,+, \cdot, 0, \leq\rangle$ je standardní model přirozených čísel. Označme $T h(\underline{\mathbb{N}})$ množinu všech sentencí pravdivých ve struktuře $\underline{\mathbb{N}}$ (tzv. teorii struktury $\underline{\mathbb{N}}$ ). Pro $n \in \mathbb{N}$ definujme $n$-tý numerál jako term $\underline{n}=S(S(\cdots(S(0) \cdots))$, kde $S$ je aplikováno $n$-krát. 

Vezměme nový konstantní symbol $c$ a vyjádřeme, že je ostře větší než každý $n$-tý numerál: 
$$ 
T=\operatorname{Th}(\underline{\mathbb{N}}) \cup\{\underline{n}<c \mid n \in \mathbb{N}\} 
$$ 
Všimněte si, že každá konečná část teorie $T$ má model. Z věty o kompaktnosti tedy plyne, že i teorie $T$ má model. Ř́́káme mu nestandardní model (označme ho $\mathcal{A}$ ). Platí v něm tytéž sentence, které platí ve standardním modelu, ale zároveň obsahuje prvek $c^{\mathcal{A}}$, který je větší než každé $n \in \mathbb{N}$ (čímž zde myslíme hodnotu termu $\underline{n}$ v nestandardním modelu $\mathcal{A})$. 

### (L16) Kompletní jednoduché extenze DeLO*. 

Teorie uspořádání
Teorie uspořádání je teorie v jazyce uspořádání $L=\langle\leq\rangle$ s rovností, jejíž axiomy jsou:
$$
\begin{aligned}
T= & \{x \leq x, \\
& x \leq y \wedge y \leq x \rightarrow x=y, \\
& x\leq y \wedge y \leq z \rightarrow x \leq z\}
\end{aligned}
$$
Těmto axiomům říkáme reflexivita, antisymetrie, tranzitivita. Modely $T$ jsou $L$-struktury $\left\langle S, \leq^S\right\rangle$, ve kterých platí axiomy $T$, tzv. (částečně) uspořádané množiny. Např: $\mathcal{A}=\langle\mathbb{N}, \leq\rangle$, $\mathcal{B}=\langle\mathcal{P}(X), \subseteq\rangle$ pro $X=\{0,1,2\}$
- Formule $x \leq y \vee y \leq x$ (linearita) platí v $\mathcal{A}$, ale neplatí v $\mathcal{B}$, nebot neplatí např. při ohodnocení kde $e(x)=\{0\}, e(y)=\{1\}$ (píšeme $\mathcal{B} \not \models \varphi[e]$ ). Je tedy nezávislá v $T$.
- Sentence $(\exists x)(\forall y)(y \leq x)$ (označme ji $\psi$ ) je pravdivá $\mathrm{v} \mathcal{B}$ a lživá $\mathrm{v} \mathcal{A}$, píšeme $\mathcal{B} \models \psi$, $\mathcal{A} \models \neg \psi$. Je tedy také nezávislá v $T$.
- Formule $(x \leq y \wedge y \leq z \wedge z \leq x) \rightarrow(x=y \wedge y=z$ ) (označme ji $\chi$ ) je pravdivá $\mathrm{v} T$, píšeme $T \models \chi$. Totéž platí pro její generální uzávěr $(\forall x)(\forall y)(\forall z) \chi$.


Teorie hustého lineárniho uspořádání (DeLO*) je extenze teorie uspořádání o následující axiomy:
- axiom linearity (někdy se mu říká také dichotomie):
$$
x \leq y \vee y \leq x
$$
- axiom hustoty
$$
x \leq y \wedge \neg x=y \rightarrow(\exists z)(x \leq z \wedge z \leq y \wedge \neg z=x \wedge \neg z=y)
$$


**Tvrzení** 9.1.6. Mějme sentence $\varphi=(\exists x)(\forall y)(x \leq y)$ a $\psi=(\exists x)(\forall y)(y \leq x)$ vyjadřující existenci minimálního resp. maximálního prvku. Následující čtyři teorie jsou právě všechny kompletní jednoduché extenze teorie DeLO*: 
- $\operatorname{DeLO}=\operatorname{DeLO}^* \cup\{\neg \varphi, \neg \psi\}$ 
- $\mathrm{DeLO}^{+}=\mathrm{DeLO}^* \cup\{\neg \varphi, \psi\}$ 
- $\mathrm{DeLO}^{-}=\mathrm{DeLO}^* \cup\{\varphi, \neg \psi\}$ 
- $\operatorname{DeLO}^{ \pm}=\operatorname{DeLO}^* \cup\{\varphi, \psi\}$ 
Stačí ukázat, že tyto čtyři teorie jsou kompletní. Potom už je zřejmé, že žádná další kompletní jednoduchá extenze DeLO* nemůže existovat. Jak vysvětlíme v Sekci 9.3, jejich kompletnost plyne z faktu, že jsou $\omega$-kategorické, tj. mají jediný spočetný model až na izomorfismus. Viz **Důsledek** 9.3.5. 

### (L17) Existence spočetného algebraicky uzavřeného tělesa. 
**Důsledek** 9.1.8. Je-li $L$ spočetný jazyk s rovností, potom ke každé nekonečné L-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura. 

**Důkaz**. Mějme nekonečnou $L$-strukturu $\mathcal{A}$. Stejně jako v důkazu Důsledku 9.1.7 najdeme spočetně nekonečnou strukturu $\mathcal{B} \equiv \mathcal{A}$. Protože $\mathrm{v} \mathcal{A}$ neplatí pro žádné $n \in \mathbb{N}$ sentence vyjadřující 'existuje nejvýše $n$ prvků' (což lze pomocí rovnosti snadno zapsat), neplatí tato sentence ani v $\mathcal{B}, \mathcal{B}$ tedy nemůže být konečná struktura. 

Spočetné algebraicky uzavřené těleso

Těleso $\mathcal{A}$ je algebraicky uzavřené, pokud každý polynom nenulového stupně v něm má kořen. Tēleso reálných čísel $\mathbb{R}$ není algebraicky uzavené, nebot $x^2+1$ nemá v $\mathbb{R}$ koṙen, stejnė tak těleso $\mathbb{Q}\left(\right.$ v něm nemá kořen ani $\left.x^2-2\right)$. Těleso komplexních čísel $\mathbb{C}$ algebraicky uzavřené je, je ale nespočetné. 

Algebraickou uzavřenost lze vyjádřit pomocí následujících sentencí $\psi_n$, pro každé $n>0$ : 
$$ 
\left(\forall x_{n-1}\right) \ldots\left(\forall x_0\right)(\exists y)\left(y^n+x_{n-1} \cdot y^{n-1}+\cdots+x_1 \cdot y+x_0)=0\right. 
$$ 
kde $y^k$ je zkratka za term $y \cdot y \cdot \cdots \cdot y$ (kde $\cdot$ je aplikováno $(k-1)$-krát). 
**Důsledek** 9.1.9. Existuje spočetné algebraicky uzavřené těleso. 
**Důkaz**. Dle Důsledku 9.1.8 existuje spočetně nekonečná struktura $\mathcal{A}$ elementárně ekvivalentní tělesu $\mathbb{C}$. Protože $\mathbb{C}$ je těleso a splňuje sentence $\psi_n$ pro všechna $n>0$, je i $\mathcal{A}$ algebraicky uzavřené těleso. 

### (L18) Tělesa charakteristiky 0 nejsou konečně axiomatizovatelná. 
Příklad: tělesa charakteristiky 0 
Necht $T$ je teorie těles. Charakteristika tělesa je nejmenší počet jedniček, které je třeba sečíst, abychom dostali nulu (v tom případě musí být charakteristika prvočíslo-dokažte si!), nebo, pokud nikdy nedostaneme sčítáním jedniček nulu, říkáme že je charakteristika 0 . Trochu formálněji: 
**Definice** 9.4.7 (Charakteristika tělesa). Říkáme, že těleso $\mathcal{A}=\langle A,+,-, 0, \cdot, 1\rangle$ je 
- charakteristiky $p$, je-li $p$ nejmenší prvočíslo takové, že $\mathcal{A} \models p 1=0$, kde $p 1$ označuje term $1+1+\cdots+1 \mathrm{~s} p$ jedničkami, nebo 
- charakteristiky 0 , pokud není charakteristiky $p$ pro žádné prvočíslo $p$. 
Necht $T$ je teorie těles. Potom třída těles charakteristiky $p$ je konečně axiomatizována teorií $T \cup\{p 1=0\}$. Třída těles charakteristiky 0 je axiomatizována následující (nekonečnou) teorií: 
$$ 
T^{\prime}=T \cup\{\neg p 1=0 \mid p \text { je prvočíslo }\} 
$$ 
Konečná axiomatizace ale neexistuje. 
**Tvrzení** 9.4.8. Tř́́da $K$ těles charakteristiky 0 není konečně axiomatizovatelná. 
**Důkaz**. Díky Větě 9.4.6 stačí ukázat, že $\bar{K}$ (tělesa nenulové charakteristiky) není axiomatizovatelná, což dokážeme sporem. Necht' existuje teorie $S$ taková, že $\mathrm{M}(S)=\bar{K}$. Potom teorie $S^{\prime}=S \cup T^{\prime}$ má model, nebot' každá její konečná část má model: stačí vzít těleso prvočíselné charakteristiky větší než jakékoliv $p$ z axiomu $T^{\prime}$ tvaru $\neg p 1=0$. Necht $\mathcal{A}$ je model $S^{\prime}$. Potom je i $\mathcal{A} \in \mathrm{M}(S)=\bar{K}$. Zároveň je ale $\mathcal{A} \in \mathrm{M}\left(T^{\prime}\right)=K$, což je spor. 
**Věta** 9.4.6 (O konečné axiomatizovatelnosti). Mějme třŕdu struktur $K \subseteq \mathrm{M}_L$ a uvažme také jeji doplněk $\bar{K}=\mathrm{M}_L \backslash K$. Potom $K$ je konečně axiomatizovatelná, právě když $K i \bar{K}$ jsou axiomatizovatelné. 

### (L19) Kritérium otevřené axiomatizovatelnosti. 
9.4.2 Otevřená axiomatizovatelnost 
Pro otevřenou axiomatizovatelnost existuje jednoduché sémantické kritérium: třída jejích modelů musí být uzavřená na podstruktury. Platí dokonce ekvivalence, dokážeme ale jen jednu implikaci (důkaz druhé je obtížnějǒí). 

**Věta** 9.4.9. Pokud je teorie T otevřeně axiomatizovatelná, potom je každá podstruktura modelu $T$ také modelem $T$. 

**Poznámka** 9.4.10. Platí i obrácená implikace: Je-li každá podstruktura modelu $T$ také modelem, potom je $T$ otevřeně axiomatizovatelná. **Důkaz** zde ale neuvedeme. 

**Důkaz**. Necht $T^{\prime}$ je otevřená axiomatizace $T$. Mějme model $\mathcal{A} \models T^{\prime}$ a podstrukturu $\mathcal{B} \subseteq \mathcal{A}$. Pro každou formuli $\varphi \in T^{\prime}$ platí $\mathcal{B} \models \varphi$ (nebot' $\varphi$ je otevřená), tedy i $\mathcal{B} \models T^{\prime}$. 
Přıklad 9.4.11. Uved'me několik příkladů: 
- Teorie DeLO není otevřeně axiomatizovatelná, například žádná konečná podstruktura modelu DeLO nemůže být hustá. 
- Teorie těles není otevřeně axiomatizovatelná, podstruktura $\mathbb{Z} \subseteq \mathbb{Q}$ tělesa celých čísel není tělesem, v $\mathbb{Z}$ neexistuje inverzní prvek vůči násobení $\mathrm{k}$ číslu 2 . 
- Pro dané $n \in \mathbb{N}$ jsou nejvýše $n$-prvkové grupy otevřeně axiomatizovatelné(podgrupy jsou jistě také nejvýše $n$-prvkové). Jako otevřenou axiomatizaci lze vzít následující extenzi (otevřené) teorie grup $T$ : 
$$ 
T \cup\left\{\bigvee_{1 \leq i<j \leq n+1} x_i=x_j\right\} 
$$ 

### (L20) Rekurzivně axiomatizovaná teorie je částečně rozhodnutelná, kompletní je rozhodnutelná. 
10.1 Rekurzivní axiomatizace a rozhodnutelnost 
V důkazových systémech, kterými jsme se zabývali (tablo metoda, rezoluce, hilbertův kalkulus) jsme povolili, aby teorie $T$, ve které dokazujeme, byla nekonečná. Vůbec jsem se ale zatím nezabývali tím, jak je zadaná. Pokud chceme ověřit, že je daný objekt (tablo, rezoluční strom, posloupnost formulí) korektním důkazem, potřebujeme nějaký algoritmický přístup ke všem axiomům $T$. 

Jednou z možností by bylo požadovat enumerátor $T$, tj. algoritmus, který vypisuje na výstup axiomy z $T$, a každý axiom někdy vypíše. ${ }^2$ Potom by bylo snadné potvrdit, že je daný důkaz korektní. Pokud bychom ale dostali důkaz, který použil chybný axiom, který v $T$ není, nikdy bychom se to nedozvěděli: nekonečně dlouho bychom čekali, zda jej enumerátor přeci jen nevypíše. Požadujeme proto silnější vlastnost, která umožňuje rozpoznat i chybné důkazy rekurzivní axiomatizaci $:^3$ 

**Definice** 10.1.1 (Rekurzivní axiomatizace). Teorie $T$ je rekurzivně axiomatizovaná, pokud existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $\varphi \in T$. 

Zaměříme se na otázku, zda můžeme v dané teorii $T$ 'algoritmicky rozhodovat pravdu' (tj. platnost vstupní formule). Pokud ano, říkáme, že je teorie rozhodnutelná. To je ale poměrně silná vlastnost, definujeme proto také částečnou rozhodnutelnost, která znamená, že pokud formule platí, algoritmus nám to řekne, ale pokud neplatí, nikdy se nemusíme dočkat odpovědi. 
**Definice** 10.1.3 (Rozhodnutelnost). O teorii $T$ říkáme, že je 
- rozhodnutelná, pokud existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $T \models \varphi$, 
- částečně rozhodnutelná, pokud existuje algoritmus, který pro každou vstupní formuli: 
- pokud $T \models \varphi$, doběhne a odpoví "ano", 
- pokud $T \not \models \varphi$, bud' nedoběhne, nebo doběhne a odpoví "ne".
  
Můžeme jako obvykle předpokládat, že $\varphi$ v definici je sentence. Ukážeme si jednoduché tvrzení: 

**Tvrzení** 10.1.4. Necht T je rekurzivně axiomatizovaná. Potom: 
(i) T je částečně rozhodnutelná, 
(ii) je-li $T$ navíc kompletní, potom je rozhodnutelná. 
**Důkaz**. Algoritmem ukazujícím částečnou rozhodnutelnost je konstrukce systematického tabla pro F $\varphi .^4$ Pokud $\varphi$ v $T$ platí, konstrukce skončí v konečně mnoha krocích a snadno ověříme, že je tablo sporné, jinak ale skončit nemusí. 

Je-li $T$ kompletní, víme, že $T \vdash \varphi$ právě když $T \nvdash \varphi$. Budeme tedy paralelně konstruovat tablo pro $\mathrm{F} \varphi$ a tablo pro $\mathrm{T} \varphi$ (důkaz a zamítnutí $\varphi$ z $T$ ): jedna z konstrukcí po konečně mnoha krocích skončí. 

### (L21) Teorie konečné struktury v konečném jazyce s rovností je rozhodnutelná. 
10.1.2 Rekurzivní axiomatizovatelnost 
V předchozí kapitole, konkrétně v Sekci 9.4, jsme se zabývali otázkou, kdy lze popsat nějakou třídu struktur [resp. teorii] pomocí axiomů [určitého tvaru]. Nyní se zaměřme na otázku, kdy to lze udělat algoritmicky. 

**Definice** 10.1.8 (Rekurzivní axiomatizovatelnost). Třída $L$-struktur $K \subseteq \mathrm{M}_L$ je rekurzivně axiomatizovatelná, pokud existuje rekurzivně axiomatizovaná $L$-teorie $T$ taková, že $K=M_L(T)$. Teorie $T^{\prime}$ je rekurzivně axiomatizovatelná, pokud je rekurzivně axiomatizovatelná třída jejích modelů, neboli pokud je $T^{\prime}$ ekvivalentní nějaké rekurzivně axiomatizované teorii. 

**Poznámka** 10.1.9. Podobně bychom mohli definovat rekurzivně spočetnou axiomatizovatelnost. 
Ukažme si následující jednoduché tvrzení: 
**Tvrzení** 10.1.10. Je-li $\mathcal{A}$ konečná struktura v konečném jazyce s rovností, potom je teorie $\operatorname{Th}(\mathcal{A})$ rekurzivně axiomatizovatelná. 

**Poznámka** 10.1.11. Z toho plyne i že $\operatorname{Th}(\mathcal{A})$ je rozhodnutelná, což ale není překvapivé: platnost sentence $\varphi \mathrm{v}$ konečné struktuře $\mathcal{A}$ můžeme snadno ověřit. 

**Důkaz**. Očíslujme prvky domény jako $A=\left\{a_1, \ldots, a_n\right\}$. Teorii $\operatorname{Th}(\mathcal{A})$ lze axiomatizovat jedinou sentencí, která je tvaru "existuje právě $n$ prvků $a_1, \ldots, a_n$ splňujících právě ty základní vztahy o funkčních hodnotách a relacích, které platí ve struktuře $\mathcal{A}$ ". 9 
9.1 Elementární ekvivalence 
Nejprve se podíváme na několik vlastností souvisejících s pojmem elementární ekvivalence. Připomeňme, že $L$-struktury $\mathcal{A}$ a $\mathcal{B}$ jsou elementárně ekvivalentní $(\mathcal{A} \equiv \mathcal{B})$, pokud v nich platí tytéž $L$-sentence. 

V teorii modelů nás často zajímá, jaké vlastnosti (sentence) platí v dané, konkrétní struktuře: 

**Definice** 9.1.1 (Teorie struktury). Mějme $L$-strukturu $\mathcal{A}$. Teorie struktury $\mathcal{A}$, značíme $T h(\mathcal{A})$ je množina všech $L$-sentencí platných v $\mathcal{A}$ : 
$$ 
\operatorname{Th}(\mathcal{A})=\{\varphi \mid \varphi \text { je } L \text {-sentence a } \mathcal{A} \models \varphi\} 
$$ 
Přiklad 9.1.2. Jako důležitý příklad vezměme standardní model aritmetiky, strukturu $\underline{\mathbb{N}}=$ $\langle\mathbb{N}, S,+, \cdot, 0, \leq\rangle$. Teorii $\mathrm{Th}(\underline{\mathbb{N}})$ říkáme aritmetika přirozených čísel. $\mathrm{V}$ následující kapitole si ukážeme, že je (algoritmicky) nerozhodnutelná. ${ }^2$ 

### (L22) Gödelovy věty o neúplnosti a jejich důsledky (bez důkazı̊). 
10.4 Gödelovy věty 
Na závěr přednášky představíme slavné Gödelovy věty o neúplnosti, jejichž pochopení by mělo být samozřejmou součástí vzdělání každého informatika. Pokusíme se vysvětlit i princip důkazů, ale vynecháme veškeré technické detaily. 
10.4.1 První věta o neúplnosti 
Nejprve vyslovíme Gödelovu První větu o neúplnosti, a vysvětlíme smysl jejích předpokladů. 
**Věta** 10.4.1 (První věta o neúplnosti). Pro každou bezespornou rekurzivně axiomatizovanou extenzi $T$ Robinsonovy aritmetiky existuje sentence, která je pravdivá $v \mathbb{N}$, ale není dokazatelná $v T$ 

Takové sentenci se říká Gödelova sentence. Velmi neformálně řečeno, Gödelova První věta o neúplnosti říká, že vlastnosti aritmetiky přirozených čísel nelze 'rozumně', efektivně popsat (v logice 1. řádu), každý takový popis je nutně 'neúplný'. Je důležité si uvědomit, že mluvíme o pravdivosti ve standardním modelu aritmetiky, tj. ve struktuře $\underline{\mathbb{N}}$, zatímco dokazatelnost je v teorii $T$. (Z Věty o úplnosti samozřejmě plyne, že každá sentence pravdivá $v T$ je v $T$ i dokazatelná.) 

Bezespornost je nutným předpokladem, nebot' ve sporné teorii je dokazatelná každá sentence. Připomeňme, že rekurzivní axiomatizovanost můžeme chápat jako 'efektivní zadání' axiomů (pomocí algoritmu), bez této vlastnosti by taková teorie nebyla užitečná. Požadavek aby teorie byla extenzí Robinsonovy aritmetiky chápejte jako předpoklad, že má alespoň 'základní aritmetickou sílu', že v ní lze určitým způsobem 'mluvit' o přirozených číslech. Existují různé varianty tohoto předpokladu, s jinými teoriemi než je Robinsonova aritmetika, a není například nutné, aby šlo přímo o extenzi, stačí, když je v teorii Robinsonova aritmetika v jistém smyslu 'definovatelná'. Ale teorie, ve které 'nelze zakódovat přirozená čísla' (a zde je důležité, že můžeme mluvit nejen o sčítání, ale i o násobení), je 'příliš slabá'. 

Je dobré si uvědomit, že speciálně platí i následující tvrzení 'o nekompletnosti': 
**Důsledek** 10.4.2. Splňuje-li teorie $T$ předpoklady První věty o neúplnosti a je-li navíc $\mathbb{N}$ modelem teorie $T$, potom $T$ není kompletní. 

10.4.3 Druhá věta o neúplnosti 

Druhá Gödelova věta o neúplnosti říká, neformálně řečeno, že efektivně daná, dostatečně bohatá teorie nemůže sama dokázat svou bezespornost. Bezespornost ("konzistenci") vyjádříme následující sentencí, kterou označíme jako $C o n_T$ : 
$$ 
\neg(\exists y) \operatorname{Prf}_T(\underline{0=S(0)}, y) 
$$ 
Všimněte si, že platí $\underline{\mathbb{N}} \models C_T$, právě když $T \nvdash 0=S(0)$. Neboli sentence $C_0 n_T$ opravdu vyjadřuje, že "Teorie T je bezesporná". 

**Věta** 10.4.13 (Druhá věta o neúplnosti). Pro každou bezespornou rekurzivně axiomatizovanou extenzi $T$ Peanovy aritmetiky platí, že $C_T$ není dokazatelná v T. 

Všimněte si, že sentence $\operatorname{Con}_T$ je přitom pravdivá v $\underline{\mathbb{N}}$ (nebot $T$ je opravdu bezesporná). Zmiňme také, že není třeba plná síla Peanovy aritmetiky, stačí slabší předpoklad. Nyní si **Důsledek** 10.4.14. Existuje model PA, ve kterém platí sentence $(\exists y) \operatorname{Prf}_{P A}(0=S(0), y)$. 
**Důsledek** 10.4.15. Existuje bezesporná rekurzivně axiomatizovaná extenze $T$ Peanovy aritmetiky, která 'dokazuje svou spornost', tj. taková, že $T \vdash \neg C_T$. 

**Důsledek** 10.4.16. Je-li teorie množin $Z F C$ bezesporná, nemůže být sentence Con$_{Z F C}$ v teorii $Z F C$ dokazatelná. 

## Seznam těžkých otázek 
### (T1) **Věta** o korektnosti tablo metody ve výrokové logice. 
4.5.1 **Věta** o korektnosti 
Řekneme, model $v$ se shoduje s položkou $P$, pokud $P=\mathrm{T} \varphi$ a $v \models \varphi$, nebo $P=\mathrm{F} \varphi$ a $v \not \models \varphi$. Dále $v$ se shoduje s větví $V$, pokud se shoduje s každou položkou na této větvi. 

Jak už jsme zmínili, design atomických tabel zaručuje, že shoduje-li se model s položkou v kořeni tabla, shoduje se s některou větví. Není těžké indukcí podle konstrukce tabla ukázat následující lemma: 

Lemma 4.5.1. Shoduje-li se model teorie $T$ s položkou v kořeni tabla z teorie $T$, potom se shoduje s některou větví. 

**Důkaz**. Mějme tablo $\tau=\bigcup_{i \geq 0} \tau_i$ z teorie $T$ a model $v \in \mathrm{M}(T)$ shodující se s kořenem $\tau$, tedy s (jednoprvkovou) větví $V_0$ v  (jednoprvkovém) $\tau_0$. 
Indukcí podle $i$ (podle kroků v při konstrukci tabla) najdeme posloupnost $V_0 \subseteq V_1 \subseteq \ldots$ takovou, že $V_i$ je větev $\mathrm{v}$ tablu $\tau_i$ shodující se s modelem $v$, a $V_{i+1}$ je prodloužením $V_i$. Požadovaná větev tabla $\tau$ je potom $V=\bigcup_{i \geq 0} V_i$. 
- Pokud $\tau_{i+1}$ vzniklo z $\tau_i$ bez prodloužení větve $V_i$, definujeme $V_{i+1}=V_i$. 
- Pokud $\tau_{i+1}$ vzniklo z $\tau_i$ připojením položky T $\alpha$ (pro nějaký axiom $\alpha \in T$ ) na konec větve $V_i$, definujeme $V_{i+1}$ jako tuto prodlouženou větev. Protože $v$ je model $T$, platí v něm axiom $\alpha$, tedy shoduje se i s novou položkou T $\alpha$. 
- Necht' $\tau_{i+1}$ vzniklo z $\tau_i$ připojením atomického tabla pro nějakou položku $P$ na konec větve $V_i$. Protože se model $v$ shoduje s položkou $P$ (která leží na větvi $V_i$ ), shoduje se i s kořenem připojeného atomického tabla, a proto se shoduje i s některou z jeho větví. (Tuto vlastnost snadno ověříme pro všechna atomická tabla.) Definujeme $V_{i+1}$ jako prodloužení $V_i$ o tuto větev atomického tabla. ${ }^7$ 

Nyní už můžeme dokázat Větu o korektnosti. Zkráceně řečeno, pokud by existoval důkaz a zároveň protipříklad, protipříklad by se musel shodovat s některou větví důkazu, ty jsou ale všechny sporné. 

**Věta** 4.5.2 (O korektnosti). Je-li výrok $\varphi$ tablo dokazatelný $z$ teorie $T$, potom je $\varphi$ pravdivý v $T, t j . T \vdash \varphi \Rightarrow T \models \varphi$. 

**Důkaz**. Dokážeme sporem. Předpokládejme, že $\varphi$ v $T$ neplatí, tj. existuje protipříklad: model $v \in \mathrm{M}(T)$, ve kterém $\varphi$ neplatí. 
Protože je $\varphi$ dokazatelná z $T$, existuje tablo důkaz $\varphi$ z T, což je sporné tablo z $T$ s položkou $\mathrm{F} \varphi$ v kořeni. Model $v$ se shoduje s položkou $\mathrm{F} \varphi$, tedy podle Lemmatu 4.5.1 se shoduje s nějakou větví $V$. Všechny větve jsou ale sporné, včetně $V$. Takže $V$ obsahuje položky T $\psi$ a F $\psi$ (pro nějaký výrok $\psi$ ), a model $v$ se s těmito položkami shoduje. Máme tedy $v \models \psi$ a zároven̆ $v \not \models \psi$, což je spor. 

### (T2) **Věta** o korektnosti tablo metody v predikátové logice. 
7.4 Korektnost a úplnost 
V této sekci dokážeme, že tablo metoda je i v predikátové logice korektní a úplná. **Důkaz**y obou vět mají stejnou strukturu jako ve výrokové logice, liší se jen v implementačních detailech. 

7.4.1 **Věta** o korektnosti 
Model (struktura) $\mathcal{A}$ se shoduje s položkou $P$, pokud $P=\mathrm{T} \varphi$ a $\mathcal{A} \models \varphi$, nebo $P=\mathrm{F} \varphi$ a $\mathcal{A} \not \models \varphi$. 
Dále $\mathcal{A}$ se shoduje s větví $V$, pokud se shoduje s každou položkou na této větvi. 

Ukážeme nejprve pomocné lemma analogické Lemmatu 4.5.1: 

Lemma 7.4.1. Shoduje-li se model $\mathcal{A}$ teorie $T$ s položkou v kořeni tabla z teorie $T$ (v jazyce L), potom lze $\mathcal{A}$ expandovat do jazyka $L_C$ tak, že se shoduje s některou větví $v$ tablu. 

Všimněte si, že stačí expandovat $\mathcal{A}$ o nové konstanty $\mathcal{C}^{\mathcal{A}}$ vyskytující se na větvi $V$. Ostatní konstantní symboly lze interpretovat libovolně. 

**Důkaz**. Mějme tablo $\tau=\bigcup_{i>0} \tau_i$ z teorie $T$ a model $\mathcal{A} \in \mathrm{M}_L(T)$ shodující se s kořenem $\tau$, tedy $\mathrm{s}$ (jednoprvkovou) větví $V_0 \mathrm{v}$ (jednoprvkovém) $\tau_0$. 

Indukcí podle $i$ najdeme posloupnost větví $V_i$ a expanzí $\mathcal{A}_i$ modelu $\mathcal{A}$ o konstanty $c^{\mathcal{A}} \in C$ vyskytující se na $V_i$ takových, že $V_i$ je větev v tablu $\tau_i$ shodující se s modelem $\mathcal{A}_i, V_{i+1}$ je prodloužením $V_i$, a $\mathcal{A}_{i+1}$ je expanzí $\mathcal{A}_i$ (mohou si být i rovny). Požadovaná větev tabla $\tau$ je 
potom $V=\bigcup_{i \geq 0} V_i$. Expanzi modelu $\mathcal{A}$ do jazyka $L_C$ získáme jako 'limitu' expanzí $\mathcal{A}_i$, tj. vyskytuje-li se symbol $c \in C$ na $V$, vyskytuje se na nějaké z větví $V_i$ a interpretujeme ho stejně jako $\mathrm{v} \mathcal{A}_i$ (ostatní pomocné symboly interpretujeme libovolně). 
- Pokud $\tau_{i+1}$ vzniklo z $\tau_i$ bez prodloužení větve $V_i$, definujeme $V_{i+1}=V_i$ a $\mathcal{A}_{i+1}=\mathcal{A}_i$. 
- Pokud $\tau_{i+1}$ vzniklo z $\tau_i$ připojením položky T $\alpha$ (pro nějaký axiom $\alpha \in T$ ) na konec větve $V_i$, definujeme $V_{i+1}$ jako tuto prodlouženou větev a $\mathcal{A}_{i+1}=\mathcal{A}_i$ (nepřidali jsme žádný nový pomocný konstantní symbol). Protože $\mathcal{A}_{i+1}$ je modelem $T$, platí v něm axiom $\alpha$, tedy shoduje se i s novou položkou $\mathrm{T} \alpha$. 
- Necht $\tau_{i+1}$ vzniklo z $\tau_i$ připojením atomického tabla pro nějakou položku $P$ na konec větve $V_i$. Protože se model $\mathcal{A}_i$ shoduje s položkou $P$ (která leží na větvi $V_i$ ), shoduje se i s kořenem připojeného atomického tabla. 
- Pokud jsme připojili atomické tablo pro logickou spojku, položíme $\mathcal{A}_{i+1}=\mathcal{A}_i$ (nepřidali jsme nový pomocný symbol). Protože $\mathcal{A}_{i+1}$ se shoduje $\mathrm{s}$ kořenem atomického tabla, shoduje se i s některou z jeho větví (stejně jako ve výrokové logice); definujeme $V_{i+1}$ jako prodloužení $V_i$ o tuto větev. 
- Je-li položka $P$ typu 'svědek': Pokud je $P=\mathrm{T}(\exists x) \varphi(x)$, potom $\mathcal{A}_i \models(\exists x) \varphi(x)$, tedy existuje $a \in A$ takové, že $\mathcal{A}_i \models \varphi(x)[e(x / a)]$. Větev $V_{i+1}$ definujeme jako prodloužení $V_i$ o nově přidanou položku $\mathrm{T} \varphi(x / c)$ a model $\mathcal{A}_{i+1}$ jako expanzi $\mathcal{A}_i \mathrm{o}$ konstantu $c^A=a$. Př́pad $P=\mathrm{F}(\forall x) \varphi(x)$ je obdobný. 
- Je-li položka $P$ typu 'všichni', větev $V_{i+1}$ definujeme jako prodloužení $V_i$ o atomické tablo. Nově přidaná položka je $\mathrm{T} \varphi(x / t)$ nebo $\mathrm{F} \varphi(x / t)$ pro nějaký $L_C$-term $t$. Předpokládejme, že jde o první z těchto dvou možností, pro druhou je důkaz analogický. Model $\mathcal{A}_{i+1}$ definujeme jako libovolnou expanzi $\mathcal{A}_i$ o nové konstanty vyskytující se v $t$. Protože $\mathcal{A}_i \models(\forall x) \varphi(x)$, platí i $\mathcal{A}_{i+1} \models(\forall x) \varphi(x)$ a tedy i $\mathcal{A}_{i+1} \models \varphi(x / t) ;$ model $\mathcal{A}_{i+1}$ se tedy shoduje s větví $V_i$. 

Připomeňme stručně myšlenku důkazu Věty o korektnosti: Pokud by existoval důkaz a zároveň protipříklad, protipříklad by se musel shodovat s některou větví důkazu, ty jsou ale všechny sporné. **Důkaz** je tedy téměř stejný jako ve výrokové logice. 

**Věta** 7.4.2 (O korektnosti). Je-li sentence $\varphi$ tablo dokazatelná $z$ teorie $T$, potom je $\varphi$ pravdivá $v T, t j . T \vdash \varphi \Rightarrow T \models \varphi$. 

**Důkaz**. Předpokládejme pro spor, že $T \not \models \varphi$, tj. existuje $\mathcal{A} \in \mathrm{M}(T)$ takový, že $\mathcal{A} \not \models \varphi$. Protože $T \vdash \varphi$, existuje sporné tablo z $T$ s F $\varphi$ v kořeni. Model $\mathcal{A}$ se shoduje s $\mathrm{F} \varphi$, tedy podle Lemmatu 7.4.1 lze expandovat do jazyka $L_C$ tak, že se expanze shoduje s nějakou větví $V$. Všechny větve jsou ale sporné. 

### (T3) **Věta** o úplnosti tablo metody ve výrokové logice. 
4.5.2 **Věta** o úplnosti 
Ukážeme, že bezesporná větev v dokončeném tablo důkazu poskytuje protipříklad: model teorie $T$, který se shoduje s položkou $\mathrm{F} \varphi$ v kořeni tabla, tj. neplatí v něm $\varphi$. Takových modelů může být více, definujeme proto jeden konkrétní: 

**Definice** 4.5.3 (Kanonický model). Je-li $V$ bezesporná větev dokončeného tabla, potom kanonický model pro $V$ je model definovaný předpisem (pro $p \in \mathbb{P})$ : 
$$ 
v(p)=\left\{\begin{array}{l} 
1 \text { pokud se na } V \text { vyskytuje položka } \mathrm{T} p, \\ 
0 \text { jinak. } 
\end{array}\right. 
$$ 
Lemma 4.5.4. Kanonický model pro (bezespornou dokončenou) větev $V$ se shoduje $s V$. 
**Důkaz**. Ukážeme, že kanonický model $v$ se shoduje se všemi položkami $P$ na větvi $V$, a to indukcí podle struktury výroku v položce. ${ }^8$ Nejprve základ indukce: 
- Je-li $P=\mathrm{T} p$ pro nějaký prvovýrok $p \in \mathbb{P}$, máme podle definice $v(p)=1 ; v$ se s $P$ shoduje. 
- Je-li $P=\mathrm{F} p$, potom se na větvi $V$ nemůže vyskytovat položka $\mathrm{T} p$, jinak by $V$ byla sporná. Podle definice máme $v(p)=0$ a $v$ se s $P$ opět shoduje. 
Nyní indukční krok. Rozebereme dva případy, ostatní se dokáží obdobně. 
- Necht $P=\mathrm{T} \varphi \wedge \psi$. Protože je $V$ dokončená větev, je na ní položka $P$ redukovaná. To znamená, že se na $V$ vyskytují i položky T $\varphi$ a T $\psi$. Podle indukčního předpokladu se $\mathrm{s}$ nimi model $v$ shoduje, tedy $v \models \varphi$ a $v \models \psi$. Takže platí i $v \models \varphi \wedge \psi$ a $v$ se shoduje $\mathrm{s}$. 
- Necht $P=\mathrm{F} \varphi \wedge \psi$. Protože je $P$ na $V$ redukovaná, vyskytuje se na $V$ položka $\mathrm{F} \varphi$ nebo položka $\mathrm{F} \psi$. Platí tedy $v \not \models \varphi$ nebo $v \not \models \psi$, z čehož plyne $v \not \models \varphi \wedge \psi$ a $v$ se shoduje s $P$.
  
**Věta** 4.5.5 (O úplnosti). Je-li výrok $\varphi$ pravdivý $v$ teorii $T$, potom je tablo dokazatelný z $T$, $t j . T \models \varphi \Rightarrow T \vdash \varphi$. 

**Důkaz**. Ukážeme, že libovolné dokončené (tedy např. i systematické) tablo z $T$ s položkou $\mathrm{F} \varphi \mathrm{v}$ kořeni je nutně sporné. **Důkaz** provedeme sporem: kdyby takové tablo nebylo sporné, existovala by $\mathrm{v}$ něm bezesporná (dokončená) větev $V$. Uvažme kanonický model $v$ pro tuto větev. Protože je $V$ dokončená, obsahuje T $\alpha$ pro všechny axiomy $\alpha \in T$. Model $v$ se podle Lemmatu 4.5.4 shoduje se všemi položkami na $V$, splňuje tedy všechny axiomy a máme $v \models T$. Protože se ale $v$ shoduje i s položkou $\mathrm{F} \varphi$ v kořeni, máme $v \not \models \psi$, což znamenám, že $T \not \models \psi$, spor. Tablo tedy muselo být sporné, tj. být tablo důkazem $\varphi$ z $T$. 

### (T4) **Věta** o úplnosti tablo metody v predikátové logice. 
Pozorování 7.4.4. Pro každou formuli $\varphi$ máme $\mathcal{B} \models \varphi$ (kde symbol $=$ je interpretován jako binární relace $\left.=^B\right)$, právě kdyż $\mathcal{A}=\mathcal{B} /=^B \models \varphi(k d e=$ je interpretován jako identita). 

Všimněte si, že v jazyce bez rovnosti je kanonický model vždy spočetně nekonečný. $\mathrm{V}$ jazyce s rovností může ale být konečný, jak uvidíme v následujících příkladech. 

Lemma 7.4.7. Kanonický model pro (bezespornou dokončenou) vĕtev $V$ se shoduje $s V$. 
**Důkaz**. Nejprve uvažme jazyky bez rovnosti. Ukážeme indukcí podle struktury sentencí v položkách, že kanonický model $\mathcal{A}$ se shoduje se všemi položkami $P$ na větvi $V$. 

Základ indukce, tj. případ, kdy $\varphi=R\left(s_1, \ldots, s_n\right)$ je atomická sentence, je jednoduchý: Je-li na $V$ položka T $\varphi$, potom $\left(s_1, \ldots, s_n\right) \in R^{\mathcal{A}}$ plyne přímo z definice kanonického modelu, máme tedy $\mathcal{A} \models \varphi$. Je-li na $V$ položka $\mathrm{F} \varphi$, potom na $V$ není položka $\mathrm{T} \varphi(V$ je bezesporná), $\left(s_1, \ldots, s_n\right) \notin R^{\mathcal{A}}$, a $\mathcal{A} \not \models \varphi$ 
Nyní indukční krok. Rozebereme jen několik případů, ostatní se dokáží obdobně. 
Pro logické spojky je důkaz zcela stejný jako ve výrokové logice, například je-li $P=\mathrm{F} \varphi \wedge \psi$, potom protože je $P$ na $V$ redukovaná, vyskytuje se na $V$ položka $\mathrm{F} \varphi$ nebo položka F $\psi$. Platí tedy $\mathcal{A} \forall \varphi$ nebo $\mathcal{A} \forall \psi$, z čehož plyne $\mathcal{A} \forall \varphi \wedge \psi$ a $\mathcal{A}$ se shoduje s $P$. 

Máme-li položku typu "všichni", například $P=\mathrm{T}(\forall x) \varphi(x)$ (případ $P=\mathrm{F}(\exists x) \varphi(x)$ je obdobný), potom jsou na $V$ i položky $T \varphi(x / t)$ pro každý konstantní $L_C$-term, tj. pro každý prvek " $t$ " $\in A$. Dle indukčního předpokladu je $\mathcal{A} \models \varphi(x / t)$ pro každé "t" $\in A$, tedy $\mathcal{A} \models$ $(\forall x) \varphi(x)$ 

Máme-li položku typu "svědek", například $P=\mathrm{T}(\exists x) \varphi(x)$ (případ $P=\mathrm{F}(\forall x) \varphi(x)$ je obdobný), potom je na $V$ i položka $T \varphi(x / c)$ pro nějaké " $c$ " $\in A$. Dle indukčního předpokladu je $\mathcal{A} \models \varphi(x / c)$, tedy i $\mathcal{A} \models(\exists x) \varphi(x)$. 

Je-li jazyk s rovností, máme kanonický model $\mathcal{A}=\mathcal{B} /=B$, důkaz výše platí pro $\mathcal{B}$, a zbytek plyne z Pozorování 7.4.4. 

**Věta** 7.4.8 (O úplnosti). Je-li sentence $\varphi$ pravdivá $v$ teorii $T$, potom je tablo dokazatelná $z$ $T, t j . T \models \varphi \Rightarrow T \vdash \varphi$. 

**Důkaz**. Ukážeme, že libovolné dokončené tablo z $T$ s položkou F $\varphi$ v kořeni je nutně sporné. **Důkaz** provedeme sporem: kdyby takové tablo nebylo sporné, existovala by v něm bezesporná (dokončená) větev $V$. Uvažme kanonický model $\mathcal{A}$ pro tuto větev, a označme jako $\mathcal{A}^{\prime}$ jeho redukt na jazyk $L$. Protože je $V$ dokončená, obsahuje T $\alpha$ pro všechny axiomy $\alpha \in T$. Model $\mathcal{A}$ se podle Lemmatu 7.4.7 shoduje se všemi položkami na $V$, splňuje tedy všechny axiomy a máme i $\mathcal{A}^{\prime} \models T$. Protože se ale $\mathcal{A}$ shoduje i s položkou $\mathrm{F} \varphi$ v kořeni, platí i $\mathcal{A}^{\prime} \not \models \varphi$, což znamená, že $\mathcal{A}^{\prime} \in \mathrm{M}_L(T) \backslash \mathrm{M}_L(\varphi)$, tedy $T \not \models \varphi$, a to je spor. Tablo tedy muselo být sporné, tj. být tablo důkazem $\varphi \mathrm{z} T$. 

### (T5) **Věta** o konečnosti sporu, důsledky o konečnosti a systematičnosti dükazů. 
Lemma 4.2.3 (Köenigovo lemma). Nekonečný, konečně větvíci strom má nekonečnou větev. 
(Strom je konečně větvící, pokud má každý vrchol konečně mnoho synů.) 
**Věta** 4.4.3 (Konečnost sporu). Je-li $\tau=\bigcup_{i \geq 0} \tau_i$ sporné tablo, potom existuje $n \in \mathbb{N}$ takové, že $\tau_n$ je sporné konečné tablo. 

**Důkaz**. Uvažme množinu $S$ všech vrcholů stromu $\tau$, které nad sebou (ve stromovém uspořádání) neobsahují spor, tj. dvojici položek $\mathrm{T} \psi, \mathrm{F} \psi$. 

Kdyby množina $S$ byla nekonečná, podle Königova lemmatu použitého na podstrom $\tau$ na množině $S$ bychom měli nekonečnou, bezespornou větev v $S$. To by ale znamenalo, že máme i bezespornou větev v $\tau$, což je ve sporu s tím, že $\tau$ je sporné. (Podrobněji: Větev na $S$ by byla podvětví nějaké větve $V$ v $\tau$, která je sporná, tj. obsahuje nějakou (konkrétní) spornou dvojici položek, která ale existuje už v nějakém konečném prefixu $V$.) 

Množina $S$ je tedy konečná. To znamená, že existuje $d \in \mathbb{N}$ takové, že celá $S$ leží v hloubce nejvýše $d$. Každý vrchol na úrovni $d+1$ má tedy nad sebou spor. Zvolme $n$ tak, že $\tau_n$ už obsahuje všechny vrcholy $\tau$ z prvních $d+1$ úrovní: každá větev $\tau_n$ je tedy sporná. 

**Důsledek** 4.4.4. Pokud při konstrukci tabla nikdy neprodlužujeme sporné větve, napr̆. pro systematické tablo, potom sporné tablo je konečné. 
**Důkaz**. Použijeme Větu 4.4.3, máme $\tau=\tau_n$ nebot sporné tablo už neměníme. 
**Důsledek** 4.4.5 (Konečnost důkazů). Pokud $T \vdash \varphi$, potom existuje $i$ konečný tablo důkaz $\varphi$ z $T$ 

**Důkaz**. Snadno plyne z Důsledku 4.4.4: stačí při konstrukci $\tau$ ignorovat kroky, které by prodloužily spornou větev. 
Vyslovíme zde také následující důsledek. Dokážeme ho ale až v příští sekci. 
**Důsledek** 4.4.6 (Systematičnost důkazů). PokudT $\vdash \varphi$, potom systematické tablo je (konečným) tablo důkazem $\varphi$ z T. 
K důkazu budeme potřebovat dvě fakta: pokud je $\varphi$ dokazatelná z $T$, potom v $T$ platí (**Věta** o korektnosti), tj. nemůže existovat protipříklad. A dále pokud by systematické tablo mělo bezespornou větev, znamenalo by to, že existuje protipříklad (to je klíčem k Větě o úplnosti). 

**Důkaz** Důsledku 4.4.6. Z předchozího důkazu(o uplnosti) také dostáváme 'systematičnost důkazů', tj. že důkaz můžeme vždy hledat konstrukcí systematického tabla: Pokud $T \models \varphi$, tak je i systematické tablo pro položku $\mathrm{F} \varphi$ nutně sporné, a je tedy tablo důkazem $\varphi \mathrm{z} T$. 

### (T6) **Věta** o úplnosti rezoluce ve výrokové logice. 
5.3.2 Strom dosazení 
V důkazu úplnosti budeme potřebovat zkonstruovat rezoluční strom, jeho konstrukce je založena na tzv. stromu dosazení. Dosazením literálu do formule myslíme zjednodušení formule za předpokladu, že daný literál platí. Dosazení jsme už potkali v Sekci 3.3 při jednotkové propagaci: odstraníme klauzule obsahující tento literál, a z ostatních klauzulí odstraníme literál opačný. 

**Definice** 5.3.2 (Dosazení literálu). Je-li $S$ formule a $\ell$ literál, potom dosazením $\ell$ do $S$ myslíme formuli: 
$$ 
S^{\ell}=\{C \backslash\{\bar{\ell}\} \mid l \notin C \in S\} 
$$ 
Pozorování 5.3.3. Zde shrneme několik jednoduchých faktůo dosazení: 
- $S^{\ell}$ je výsledkem jednotkové propagace aplikované na $S \cup\{\{\ell\}\}$. 
- Pokud $S$ neobsahovala literál $\ell$ ani $\bar{\ell}$, potom $S^{\ell}=S$. 
- Pokud $S$ obsahovala jednotkovou klauzuli $\{\bar{\ell}\}$, potom $\square \in S^{\ell}$, tedy $S^{\ell}$ je sporná.
  
Klíčovou vlastnost dosazení vyjadřuje následující lemma:
  
Lemma 5.3.4. $S$ je splnitelná, právě když je splnitelná $S^{\ell}$ nebo $S^{\bar{\ell}}$. 

**Důkaz**. Mějme ohodnocení $\mathcal{V} \models S$, to nemůže obsahovat $\ell$ i $\bar{\ell}$ (musí být konzistentní); bez újmy na obecnosti předpokládejme, že $\bar{\ell} \notin \mathcal{V}$, a ukažme, že $\mathcal{V} \models S^{\ell}$. Vezměme libovolnou klauzuli v $S^{\ell}$. Ta je tvaru $C \backslash\{\bar{\ell}\}$ pro klauzuli $C \in S$ (neobsahující literál $\ell$ ). Víme, že $\mathcal{V} \models C$, protože ale $\mathcal{V}$ neobsahuje $\bar{\ell}$, muselo ohodnocení $\mathcal{V}$ splnit nějaký jiný literál $C$, takže platí i $\mathcal{V} \models C \backslash\{\bar{\ell}\}$ 

Naopak, předpokládejme že existuje ohodnocení $\mathcal{V}$ splňující $S^{\ell}$ (opět bez újmy na obecnosti). Protože se $\bar{\ell}$ (ani $\ell$ ) nevyskytuje $\mathrm{v} S^{\ell}$, platí také $\mathcal{V} \backslash\{\bar{\ell}\} \models S^{\ell}$. Ohodnocení $\mathcal{V}^{\prime}=$ $(\mathcal{V} \backslash\{\bar{\ell}\}) \cup\{\ell\}$ potom splňuje každou klauzuli $C \in S$ : pokud $\ell \in C$, potom $\ell \in C \cap \mathcal{V}^{\prime}$ a $C \cap \mathcal{V}^{\prime} \neq \emptyset$, jinak $C \cap \mathcal{V}^{\prime}=(C \backslash\{\bar{\ell}\}) \cap \mathcal{V}^{\prime} \neq \emptyset$ nebot $\mathcal{V} \backslash\{\bar{\ell}\} \models C \backslash\{\bar{\ell}\} \in S^{\ell}$. Ověřili jsme, že $\mathcal{V}^{\prime} \models S$, tedy $S$ je splnitelná. 

Zda je daná konečná formule splnitelná bychom tedy mohli zjištovat rekurzivně (metodou rozděl a panuj), dosazením obou možných literálů pro (nějakou, třeba první) výrokovou proměnnou vyskytující se ve formuli, a rozvětvením výpočtu. V zásadě jde o podobný princip jako v algoritmu DPLL (viz Sekce 3.4). Výslednému stromu říkáme strom dosazení. 

**Důsledek** 5.3.6. Formule $S$ (nad spočetným jazykem) je nesplnitelná, právě když každá větev stromu dosazení obsahuje prázdnou klauzuli $\square$. 

**Důkaz**. Pro konečnou formuli $S$ plyne z diskuze výše, můžeme snadno dokázat indukcí podle velikosti $\operatorname{Var}(S)$ : 
- Je-li $|\operatorname{Var}(S)|=0$, máme $S=\emptyset$ nebo $S=\{\square\}$, v obou případech je strom dosazení jednoprvkový a tvrzení platí. 
- V indukčním kroku vybereme libovolný literál $\ell \in \operatorname{Var}(S)$ a aplikujeme Lemma 5.3.4. 
Je-li $S$ nekonečná a splnitelná, potom má splňující ohodnocení, to se 'shoduje' s odpovídající (nekonečnou) větví ve stromu dosazení. Je-li nekonečná a nesplnitelná, potom podle Věty o kompaktnosti existuje konečná část $S^{\prime} \subseteq S$, která je také nesplnitelná. Po dosazení pro všechny proměnné z $\operatorname{Var}\left(S^{\prime}\right)$ bude v každé větvi $\square$, to nastane po konečně mnoha krocích. 

**Věta** 4.7.1 (O kompaktnosti). Teorie má model, právě když každá její konečná část má model. 

**Důkaz**. Každý model teorie $T$ je zjevně modelem každé její části. Druhou implikaci dokážeme nepřímým důkazem: Předpokládejme, že $T$ nemá model, tj. je sporná, a najděme konečnou část $T^{\prime} \subseteq T$, která je také sporná. 

Protože je $T$ sporná, platí $T \vdash \perp$ (zde potřebujeme Větu o úplnosti). Podle Důsledku 4.4.5 potom existuje konečný tablo důkaz $\tau$ výroku $\perp$ z T. Konstrukce tohoto důkazu má jen konečně mnoho kroků, použili jsme tedy jen konečně mnoho axiomů z $T$. Definujeme-li $T^{\prime}=\{\alpha \in T \mid$ T $\alpha$ je položka $\mathrm{v}$ tablu $\tau\}$, potom $\tau$ je také tablo důkaz sporu z teorie $T^{\prime}$. Teorie $T^{\prime}$ je tedy sporná konečná část $T$. 

5.3.3 Úplnost rezoluce 
**Věta** 5.3.7 (O úplnosti rezoluce). Je-li $S$ nesplnitelná, je rezolucí zamítnutelná (tj. $\left.S \vdash_R \square\right)$. 
**Důkaz**. Je-li $S$ nekonečná, má z Věty o kompaktnosti konečnou nesplnitelnou část $S^{\prime}$. Rezoluční zamítnutí $S^{\prime}$ je také rezolučním zamítnutím $S$. Předpokládejme tedy, že $S$ je konečná. 
**Důkaz** provedeme indukcí podle počtu proměnných v $S$. Je-li $|\operatorname{Var}(S)|=0$, jediná možná nesplnitelná formule bez proměnných je $S=\{\square\}$ a máme jednokrokový důkaz $S \vdash_R \square$. Jinak vyberme $p \in \operatorname{Var}(S)$. Podle Lemmatu 5.3.4 jsou $S^p$ i $S^{\bar{p}}$ nesplnitelné. Mají o jednu proměnnou méně, tedy podle indukčního předpokladu existují rezoluční stromy $T$ pro $S^p \vdash_R \square$ a $T^{\prime}$ pro $S^{\bar{p}} \vdash_R \square$. 

Ukážeme, jak ze stromu $T$ vyrobit rezoluční strom $\widehat{T}$ pro $S \vdash_R \neg p$. Analogicky vyrobíme $\widehat{T}^{\prime}$ pro $S \vdash_R p$ a potom už snadno vyrobíme rezoluční strom pro $S \vdash_R \square$ : ke kořeni $\square$ připojíme kořeny stromů $\widehat{T}$ a $\widehat{T}^{\prime}$ jako levého a pravého syna (tj. v posledním kroku rezolučního důkazu získáme $\square$ rezolucí z $\{\neg p\}$ a $\{p\})$. 

Zbývá ukázat konstrukci stromu $\widehat{T}$ : množina vrcholů i uspořádání jsou stejné, změníme jen některé klauzule ve vrcholech, a to přidáním literálu $\neg p$. Na každém listu stromu $T$ je nějaká klauzule $C \in S^p$, a bud' je $C \in S$, nebo není, ale $C \cup\{\neg p\} \in S$. V prvním případě necháme label stejný. Ve druhém případě přidáme do $C$ a do všech klauzulí nad tímto listem literál $\neg p$. V listech jsou nyní jen klauzule z $S$, v kořeni jsme $\square$ změnili na $\neg p$. A každý vnitřní vrchol je nadále rezolventou svých synů. 

### (T7) Vĕta o úplnosti LI-rezoluce pro výrokové Hornovy formule. 
5.4.3 Úplnost LI-rezoluce pro Hornovy formule 
Jak si nyní ukážeme, LI-rezoluce je úplná pro Hornovy formule. A jak uvidíme v následující sekci, je základem interpreterů jazyka Prolog, který s Hornovými formulemi pracuje. Nejprve připomeňme terminologii týkající se hornovskosti a také programů, a to v množinové reprezentaci: 
- Hornova klauzule je klauzule obsahující nejvýše jeden pozitivní literál. 
- Hornova formule je (konečná, nebo i nekonečná) množina Hornových klauzulí. 
- Fakt je pozitivní jednotková (Hornova) klauzule, tj. $\{p\}$, kde $p$ je výroková proměnná. 
- Pravidlo je (Hornova) klauzule s právě jedním pozitivním a alespoň jedním negativním literálem. 
- Pravidlům a faktům říkáme programové klauzule. 
- Cil je neprázdná (Hornova) klauzule bez pozitivního literálu. 
  
Bude se nám hodit následující jednoduché pozorování: 
Pozorování 5.4.6. Je-li Hornova formule $S$ nesplnitelná a $\square \notin S$, potom obsahuje fakt $i$ cíl. 

**Důkaz**. Neobsahuje-li fakt, můžeme ohodnotit všechny proměnné 0 ; neobsahuje-li cíl, ohodnotíme 1. 

Nyní vyslovíme a dokážeme Větu o úplnosti LI-rezoluce pro Hornovské formule. **Důkaz** dává také návod, jak LI-zamítnutí zkonstruovat, a to na základě průběhu jednotkové propagace. Tento postup ilustrujeme na příkladu níže, který můžete sledovat souběžně s čtením důkazu. 

**Věta** 5.4.7 (O úplnosti LI-rezoluce pro Hornovy formule). Je-li Hornova formule $T$ splnitelná, a $T \cup\{G\}$ je nesplnitelná pro cil $G$, potom $T \cup\{G\} \vdash_{L I} \square$, a to LI-zamítnutím, které začíná cilem $G$. 

**Důkaz**. Podobně jako ve Větě o úplnosti rezoluce můžeme díky Věte o kompaktnosti předpokládat, že $T$ je konečná. **Důkaz** (konstrukci LI-zamítnutí) provedeme indukcí podle počtu proměnných v $T$. 

Z Pozorování 5.4.6 plyne, že $T$ obsahuje fakt $\{p\}$ pro nějakou výrokovou proměnnou $p$. Protože $T \cup\{G\}$ je nesplnitelná, je podle Lemmatu 5.3.4 nesplnitelná také $(T \cup\{G\})^p=$ $T^p \cup\left\{G^p\right\}$, kde $G^p=G \backslash\{\neg p\}$ 

Pokud $G^p=\square$, potom $G=\{\neg p\}, \square$ je rezolventa $G$ a $\{p\} \in T$, a máme jednokrokové LI-zamítnutí $T$ (to je báze indukce). 

Jinak je formule $T^p$ splnitelná (stejným ohodnocením jako $T$, nebot to musí obsahovat $p$ kvůli faktu $\{p\}$, tedy neobsahuje $\neg p$ ) a má méně proměnných než $T$. Tedy podle indukčního př̌dpokladu existuje LI-odvození $\square \mathrm{z} T^p \cup\left\{G^p\right\}$ začínající $G^p=G \backslash\{\neg p\}$. 

Hledané LI-zamítnutí $T \cup\{G\}$ začínající $G$ zkonstruujeme (podobně jako v důkazu Věty o úplnosti rezoluce) přidáním literálu $\neg p$ do všech listů, které už nejsou v $T \cup\{G\}$ (tedy vznikly odebráním $\neg p$, a do všech vrcholů nad nimi. Tím získáme $T \cup\{G\} \vdash_{L I} \neg p$, na závěr přidáme boční klauzuli $\{p\}$ a odvodíme $\square$. 

Lemma 5.3.4. $S$ je splnitelná, právě když je splnitelná $S^{\ell}$ nebo $S^{\bar{\ell}}$. 

**Důkaz**. Mějme ohodnocení $\mathcal{V} \models S$, to nemůže obsahovat $\ell$ i $\bar{\ell}$ (musí být konzistentní); bez újmy na obecnosti předpokládejme, že $\bar{\ell} \notin \mathcal{V}$, a ukažme, že $\mathcal{V} \models S^{\ell}$. Vezměme libovolnou klauzuli v $S^{\ell}$. Ta je tvaru $C \backslash\{\bar{\ell}\}$ pro klauzuli $C \in S$ (neobsahující literál $\ell$ ). Víme, že $\mathcal{V} \models C$, protože ale $\mathcal{V}$ neobsahuje $\bar{\ell}$, muselo ohodnocení $\mathcal{V}$ splnit nějaký jiný literál $C$, takže platí i $\mathcal{V} \models C \backslash\{\bar{\ell}\}$ 

Naopak, předpokládejme že existuje ohodnocení $\mathcal{V}$ splňující $S^{\ell}$ (opět bez újmy na obecnosti). Protože se $\bar{\ell}$ (ani $\ell$ ) nevyskytuje v $S^{\ell}$, platí také $\mathcal{V} \backslash\{\bar{\ell}\} \models S^{\ell}$. Ohodnocení $\mathcal{V}^{\prime}=$ $(\mathcal{V} \backslash\{\bar{\ell}\}) \cup\{\ell\}$ potom splňuje každou klauzuli $C \in S$ : pokud $\ell \in C$, potom $\ell \in C \cap \mathcal{V}^{\prime}$ a $C \cap \mathcal{V}^{\prime} \neq \emptyset$, jinak $C \cap \mathcal{V}^{\prime}=(C \backslash\{\bar{\ell}\}) \cap \mathcal{V}^{\prime} \neq \emptyset$ nebot' $\mathcal{V} \backslash\{\bar{\ell}\} \models C \backslash\{\bar{\ell}\} \in S^{\ell}$. Ověřili jsme, že $\mathcal{V}^{\prime} \models S$, tedy $S$ je splnitelná. 

### (T8) **Věta** o úplnosti rezoluce v predikátové logice (Lifting lemma stačí vyslovit) 
**Definice** 8.3.1 (Základní instance). Mějme otevřenou formuli $\varphi$ ve volných proměnných $x_1, \ldots, x_n$. Řekneme, že instance $\varphi\left(x_1 / t_1, \ldots, x_n / t_n\right)$ je základní (ground) instance, jsou-li všechny termy $t_1, \ldots, t_n$ konstantní (ground). 

8.6.2 **Věta** o úplnosti 
Větu o úplnosti rezoluce v predikátové logice, totiž že nesplnitelné formule lze zamítnout rezolucí, dokážeme převedením na případ výrokové logiky. Ukážeme, že rezoluční důkaz 'na úrovni výrokové logiky' je možné 'zvednout' ('lift') na úroveň predikátové logiky. 

Klíčem je následující lemma, které zaručuje takové 'zvednutí' v jednom rezolučním kroku. Jeho důkaz je poněkud technický. 

Lemma 8.6.3 (Lifting lemma). Mějme klauzule $C_1$ a $C_2$ s disjunktní množinou proměnných. Jsou-li $C_1^*$ a $C_2^*$ základní instance klauzulí $C_1$ a $C_2$ a je-li $C^*$ je rezolventou $C_1^*$ a $C_2^*$, potom existuje rezolventa $C$ klauzulí $C_1$ a $C_2$ taková, že $C^*$ je základní instancí $C$. 

**Důsledek** 8.6.4. Mějme CNF formuli $S$ a označme jako $S^*$ množinu všech jejích základních instancí. Pokud $S^* \vdash_R C^*$ ('na úrovni výrokové logiky') pro nějakou základni klauzuli $C^*$, potom existuje klauzule $C$ a základní substituce $\sigma$ taková, že $C^*=C \sigma$ a $S \vdash_R C$ ('na úrovni predikátové logiky'). 
Nyní už je snadné dokázat úplnost: 
**Věta** 8.6.5 (O úplnosti rezoluce). Je-li CNF formule $S$ nesplnitelná, potom je zamítnutelná rezolucí. 

**Důkaz**. Označme jako $S^*$ množinu všech základních instancí klauzulí z $S$. Protože je $S$ nesplnitelná, je díky Herbrandově větě (konkrétně **Důsledek** 8.3.9) nesplnitelná i $S^*$. Z věty o úplnosti výrokové rezoluce víme, že $S^* \vdash_R \square$ ('na úrovni výrokové logiky'). Z Lifting lemmatu (resp. z Důsledku 8.6.4) dostáváme klauzuli $C$ a základní substituci $\sigma$ takové, že $C \sigma=\square$ a $S \vdash_R C$ ('na úrovni predikátové logiky'). Ale protože prázdná klauzule $\square$ je instancí $C$, musí být $C=\square$. Tím jsme našli rezoluční zamítnutí $S \vdash_R \square$. 

### (T9) Skolemova věta. 
**Definice** 8.2.9 (Skolemova varianta). Mějme $L$-sentenci $\varphi$ v PNF, a necht všechny její vázané proměnné jsou různé. Necht existenční kvantifikátory z prefixu $\varphi$ jsou $\left(\exists y_1\right), \ldots,\left(\exists y_n\right)$ (v tomto pořadí), a necht pro každé $i$ jsou $\left(\forall x_1\right), \ldots,\left(\forall x_{n_i}\right)$ právě všechny univerzální kvantifikátory předcházející kvantifikátor $\left(\exists y_i\right)$ v prefixu $\varphi$. 

Označme $L^{\prime}$ rozšírǐení $L$ o nové $n_i$-ární funkční symboly $f_1, \ldots, f_n$, kde symbol $f_i$ je arity $n_i$, pro každé $i$. Skolemova varianta sentence $\varphi$ je $L^{\prime}$-sentence $\varphi_S$ vzniklá z $\varphi$ tak, že pro každé $i=1, \ldots, n$ : 
- odstraníme z prefixu kvantifikátor $\left(\exists y_i\right)$, a 
- substituujeme za proměnnou $y_i \operatorname{term} f_i\left(x_1, \ldots, x_{n_i}\right)$.
  
Tomuto procesu říkáme také skolemizace. 
**Poznámka** 8.2.11. Nezapomeňte, že při skolemizaci musíme vycházet ze sentence! Například, máme-li formuli $(\exists y) E(x, y)$, není $E(x, c)$ její Skolemova varianta. Musíme napřed provést generální uzávěr $(\forall x)(\exists y) E(x, y)$, a potom správně skolemizovat jako $(\forall x) E(x, f(x))$, což je ekvivalentní otevřené formuli $E(x, f(x))$ (která říká něco mnohem slabšího než $E(x, c)$ ). 
Je také důležité, aby každý symbol použitý při skolemizaci byl opravdu nový, jeho jedinou 'rolí' v celé teorii musí být reprezentovat 'existující' prvky v této formuli. 

V následujícím lemmatu ukážeme klíčovou vlastnost skolemovy varianty: 
Lemma 8.2.12. Mějme L-sentenci $\varphi=\left(\forall x_1\right) \ldots\left(\forall x_n\right)(\exists y) \psi$ a necht' $\varphi^{\prime}$ je sentence 
$$ 
\left(\forall x_1\right) \ldots\left(\forall x_n\right) \psi\left(y / f\left(x_1, \ldots, x_n\right)\right) 
$$ 
kde f je nový funkční symbol. Potom: 
(i) L-redukt každého modelu $\varphi^{\prime}$ je modelem $\varphi, a$ 
(ii) každý model $\varphi$ lze expandovat na model $\varphi^{\prime}$. 
**Důkaz**. Nejprve dokažme část (i): Mějme model $\mathcal{A}^{\prime} \models \varphi^{\prime}$ a necht $\mathcal{A}$ je jeho redukt na jazyk $L$. Pro každé ohodnocení proměnných $e$ platí $\mathcal{A} \models \psi[e(y / a)]$ pro $a=\left(f\left(x_1, \ldots, x_n\right)\right)^{\mathcal{A}^{\prime}}[e]$, tedy $\mathcal{A} \models \varphi$ 

Nyní část (ii): Protože $\mathcal{A} \models \varphi$, existuje funkce $f^A: A^n \rightarrow A$ taková, že pro každé ohodnocení proměnných $e$ platí $\mathcal{A} \models \psi[e(y / a)]$, kde $a=f^A\left(e\left(x_1\right), \ldots, e\left(x_n\right)\right)$. To znamená, že expanze struktury $\mathcal{A}$ vzniklá přidáním funkce $f^A$ je modelem $\varphi^{\prime}$. 

**Poznámka** 8.2.13. Expanze modelu ve druhé části tvrzení nemusí být (a typicky není) jednoznačná, na rozdíl od extenze o definici nového funkčního symbolu. 

Aplikujeme-li předchozí lemma opakovaně (postupně pro všechny existenční kvantifikátory), získáme následující důsledek: 
**Důsledek** 8.2.14. Sentence $\varphi$ a její skolemova varianta $\varphi_S$ jsou ekvisplnitelné. 
8.2.3 Skolemova věta 
V této podsekci shrneme celý postup popsaný v předchozích podsekcích. Kličem je následující věta norského logika Thoralfa Skolema: 
**Věta** 8.2.15 (Skolemova věta). Každá teorie má otevřenou konzervativní extenzi. 
**Důkaz**. Mějme $L$-teorii $T$. Každý axiom nahradíme jeho generálním uzávěrem (není-li to už sentence) a převedeme do PNF, tím získáme ekvivalentní teorii $T^{\prime}$. Nyní nahradíme každý axiom teorie $T^{\prime}$ jeho Skolemovou variantou. Tím získáme teorii $T^{\prime \prime}$ v rozšířném jazyce $L^{\prime}$. Z Lemmatu 8.2.12 plyne, že $L$-redukt každého modelu $T^{\prime \prime}$ je modelem $T^{\prime}$, tedy $T^{\prime \prime}$ je extenzí $T^{\prime}$, a že každý model $T^{\prime}$ lze expandovat do jazyka $L^{\prime}$ na model $T^{\prime \prime}$, tedy jde o konzervativní extenzi. Teorie $T^{\prime \prime}$ je axiomatizovaná univerzálními sentencemi, odstraníme-li kvantifikátorové prefixy (tj. vezmeme-li jádra axiomů), získáme otevřenou teorii $T^{\prime \prime \prime}$, která ekvivalentní s $T^{\prime \prime}$ a tedy je také konzervativní extenzí $T$. 

Ze sémantické charakterizace konzervativní extenze snadno plyne následující důsledek: 
**Důsledek** 8.2.16. Ke každé teorii můžeme pomocí skolemizace najít ekvisplnitelnou otevřenou teorii. 

Otevřenou teorii už můžeme snadno převést do CNF (vyjádřit formulí $S$ v množinové reprezentaci) pomocí ekvivalentních syntaktických úprav, stejně jako ve výrokové logice (viz Sekce 2.32$)$ 

### (T10) Herbrandova vĕta. 
8.3.2 Herbrandova věta 
V této podsekci vyslovíme a dokážeme Herbrandovu větu. Budeme předpokládat, že jazyk obsahuje nějaký konstantní symbol: pokud v jazyce žádný není, jeden přidáme. Konstantní symbol potřebujeme k tomu, aby existovaly konstantní termy, a my mohli vytvořit tzv. Herbrandův model. Jde o konstrukci sémantického objektu (modelu) ze syntaktických objektů (konstantních termů) velmi podobnou kanonickému modelu (**Definice** 7.4.3). ${ }^6$ 

**Definice** 8.3.4 (Herbrandův model). Mějme jazyk $L=\langle\mathcal{R}, \mathcal{F}\rangle$ s alespoň jedním konstantním symbolem. $L$-struktura $\mathcal{A}=\left\langle A, \mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}}\right\rangle$ je Herbrandův model, jestliže: 
- $A$ je množina všech konstantních $L$-termů (tzv. Herbrandovo univerzum), a 
- pro každý $n$-ární funkční symbol $f \in \mathcal{F}$ a konstantní termy " $t_1 ", \ldots$, " $t_n " \in A$ platí: 
$$ 
f^{\mathcal{A}}\left(" t_1 ", \ldots, " t_n "\right)=" f\left(t_1, \ldots, t_n\right) " 
$$ 
- Speciálně, pro každý konstantní symbol $c \in \mathcal{F}$ je $c^{\mathcal{A}}=$ "c".
  
Na interpretace relačních symbolů neklademe žádné podmínky. 

Připomeňme, že uvozovky okolo termů píšeme jen neformálně, abychom jasněji odlišili termy jako syntaktické objekty (řetězce symbolů) od jejich interpretací (funkcí). 

Přiklad 8.3.5. Mějme jazyk $L=\langle P, f, c\rangle$, kde $P$ je unární relační, $f$ je binární funkční, a $c$ konstantní symbol. Herbrandovo univerzum pro tento jazyk je množina 
$$ 
A=\{" c ", " f(c, c) ", " f(c, f(c, c)) ", " f(f(c, c), c) " \ldots\} 
$$ 
Struktura $\mathcal{A}=\left\langle A, P^{\mathcal{A}}, f^{\mathcal{A}}, c^{\mathcal{A}}\right\rangle$ je Herbrandův model, jestliže $c^{\mathcal{A}}=$ "c" a funkce $f^{\mathcal{A}}$ splňuje: 
- $f^{\mathcal{A}}(" c ", " c ")=" f(c, c) "$ 
- $f^{\mathcal{A}}(" c ", " f(c, c) ")=" f(c, f(c, c)) "$ 
- $f^{\mathcal{A}}(" f(c, c) ", " c ")=" f(f(c, c), c) "$, atd. 
Nyní jsme připraveni vyslovit Herbrandovu větu. Neformálně řečeno, je-li teorie splnitelná, tj. má-li model, potom má dokonce Herbrandův model, a v opačném případě najdeme nesplnitelnou konjunkci základních instancí axiomů, použitelnou pro rezoluční zamítnutí 'na úrovni výrokové logiky'. 

**Věta** 8.3.6 (Herbrandova věta). Mějme otevřenou teorii $T$ v jazyce L bez rovnosti a s alespoň jedním konstantním symbolem. Potom bud’ má T Herbrandův model, nebo existuje konečně mnoho základních instancí axiomů $T$, jejichž konjunkce je nesplnitelná. 


**Důkaz.** Označme jako $T_{\text {ground }}$ množinu všech základních instancí axomů teorie T. Zkonstruujeme systematické tablo z teorie $T_{\text {ground }}$ s položkou $\mathrm{F} \perp \mathrm{v}$ kořeni, ale z jazyka $L$, bez rozšíření o pomocné konstantní symboly na jazyk $L_C \cdot{ }$
Pokud tablo obsahuje bezespornou větev, potom je kanonický model pro tuto větev (opět bez přidání pomocných konstantních symbolů) Herbrandovým modelem $T$. V opačném případě máme tablo důkaz sporu, tedy teorie $T_{\text {ground }}$, a tím pádem i $T$, je nesplnitelná. Protože je tablo důkaz konečný, použili jsme $\mathrm{v}$ něm jen konečně mnoho základních instancí axiomů $\alpha_{\text {ground }} \in T_{\text {ground. }}$ Jejich konjunkce je tedy nesplnitelná.

**Poznámka** 8.3.7. Máme-li jazyk s rovností, potom nejprve teorii $T$ rozšíríme o axiomy rovnosti na teorii $T^*$, a má-li $T^*$ Herbrandův model $\mathcal{A}$, faktorizujeme ho podle kongruence $={ }^A$, stejně jako v případě kanonického modelu. 

### (T11) Löwenheim-Skolemova vĕta včetnĕ varianty s rovností, jejich důsledky. 
7.5.1 Löwenheim-Skolemova věta 
**Věta** 7.5.2 (Löwenheim-Skolemova). Je-li L spočetný jazyk bez rovnosti, potom každá bezesporná L-teorie má spočetně nekonečný model. 

**Důkaz**. Vezměme nějaké dokončené (např. systematické) tablo z teorie $T$ s položkou $\mathrm{F} \perp$ v kořeni. Protože $T$ je bezesporná, není v ní dokazatelný spor, tedy tablo musí obsahovat bezespornou větev. Hledaný spočetně nekonečný model je $L$-redukt kanonického modelu pro tuto větev. 

Tato věta má následující jednoduchý důsledek: 
**Důsledek** 9.1.7. Je-li L spočetný jazyk bez rovnosti, potom ke každé L-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura. 

**Důkaz**. Mějme $L$-strukturu $\mathcal{A}$. Teorie $\operatorname{Th}(\mathcal{A})$ je bezesporná (má model $\mathcal{A})$, tedy dle LöwenheimSkolemovy má spočetně nekonečný model $\mathcal{B} \models T h(\mathcal{A})$. To ale znamená, že $\mathcal{B} \equiv \mathcal{A}$. 

V jazyce bez rovnosti tedy nemůžeme vyjádřit například 'model má právě 42 prvků'. 
V důkazu Löwenheim-Skolemovy věty jsme sestrojený model získali jako kanonický model pro bezespornou větev tabla z $T$ pro položku $\mathrm{F} \perp$. Stejným způsobem se dokáže následující verze pro jazyky s rovností, stačí faktorizovat dle relace $={ }^A$ : 

**Věta** (Löwenheim-Skolemova s rovností). Je-li L spočetný jazyk s rovností, potom každá bezesporná L-teorie má spočetný model (tj. konečný, nebo spočetně nekonečný). 
I tato verze má snadný důsledek pro konkrétní struktury: 
**Důsledek** 9.1.8. Je-li L spočetný jazyk s rovností, potom ke každé nekonečné L-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura. 

**Důkaz**. Mějme nekonečnou $L$-strukturu $\mathcal{A}$. Stejně jako v důkazu Důsledku 9.1.7 najdeme spočetně nekonečnou strukturu $\mathcal{B} \equiv \mathcal{A}$. Protože v $\mathcal{A}$ neplatí pro žádné $n \in \mathbb{N}$ sentence vyjadřující 'existuje nejvýše $n$ prvků' (což lze pomocí rovnosti snadno zapsat), neplatí tato sentence ani v $\mathcal{B}, \mathcal{B}$ tedy nemůže být konečná struktura. 

### (T12) Vztah izomorfismu a elementární ekvivalence. 
9.2 Izomorfismus struktur 
Podívejme se blíže na pojem izomorfismu struktur, který zobecňuje izomorfismus grafi̊, vektorových prostorů, apod. Neformálně řečeno, struktury jsou izomorfní, pokud se liší jen pojmenováním konkrétních prvků. 

**Definice** 9.2.1. Mějme struktury $\mathcal{A}, \mathcal{B}$ jazyka $L=\langle\mathcal{R}, \mathcal{F}\rangle$. Izomorfismus $\mathcal{A}$ a $\mathcal{B}$ (nebo ' $\mathcal{A}$ na $\left.\mathcal{B}^{\prime}\right)$ je bijekce $h: A \rightarrow B$ splňující následující vlastnosti: 
- Pro každý (n-ární) funkční symbol $f \in \mathcal{F}$ a pro všechna $a_i \in A$ platí: 
$$ 
h\left(f^{\mathcal{A}}\left(a_1, \ldots, a_n\right)\right)=f^{\mathcal{B}}\left(h\left(a_1\right), \ldots, h\left(a_n\right)\right) 
$$ 
(Speciálně, je-li $c \in \mathcal{F}$ konstantní symbol, platí $h\left(c^{\mathcal{A}}\right)=c^{\mathcal{B}}$.) 
- Pro každý (n-ární) relační symbol $R \in \mathcal{R}$ a pro všechna $a_i \in A$ platí: 
$$ 
R^{\mathcal{A}}\left(a_1, \ldots, a_n\right) \text { právě když } R^{\mathcal{B}}\left(h\left(a_1\right), \ldots, h\left(a_n\right)\right) 
$$ 
Pokud existuje, říkáme, že $\mathcal{A}$ a $\mathcal{B}$ jsou izomorfní (nebo ' $\mathcal{A}$ je izomorfni s $\mathcal{B}$ via $h$ ') a píšeme $\mathcal{A} \simeq \mathcal{B}$ (nebo $\left.\mathcal{A} \simeq{ }_h \mathcal{B}\right)$. Automorfismus $\mathcal{A}$ je izomorfismus $\mathcal{A}$ na $\mathcal{A}$ 
Všimněte si, že relace 'býti izomorfní' je ekvivalence. Ukažme si jeden příklad: Nyní ukážeme, že izomorfismus je bijekce 'zachovávající sémantiku': 
**Tvrzení** 9.2.3. Mějme struktury $\mathcal{A}, \mathcal{B}$ jazyka $L=\langle\mathcal{R}, \mathcal{F}\rangle$. Bijekce $h: A \rightarrow B$ je izomorfismus $\mathcal{A}$ a $\mathcal{B}$, právě když platí následující: 
(i) pro každý L-term $t$ a ohodnocení proměnných $e$ : $\operatorname{Var} \rightarrow A$ : 
$$ 
h\left(t^{\mathcal{A}}[e]\right)=t^{\mathcal{B}}[e \circ h] 
$$ 
(ii) pro každou L-formuli $\varphi$ a ohodnocení proměnných e : $\operatorname{Var} \rightarrow A$ : 
$$ 
\mathcal{A} \models \varphi[e] \quad p r a ́ v e \check{ } k d y \check{z} \quad \mathcal{B} \models \varphi[e \circ h] 
$$ 
**Důkaz**. Je-li $h$ izomorfismus, vlastnosti snadno dokážeme indukcí podle struktury termu resp. formule. Naopak, je-li $h$ bijekce splňující (i) a (ii), dosazením $t=f\left(x_1, \ldots, x_n\right)$ resp. $\varphi=$ $R\left(x_1, \ldots, x_n\right)$ dostáváme vlastnosti z definice izomorfismu. 

Jako okamžitý důsledek dostáváme fakt, že izomorfní struktury jsou elementárně ekvivalentní: 
**Důsledek** 9.2.4. Pokud $\mathcal{A} \simeq \mathcal{B}$, potom $\mathcal{A} \equiv \mathcal{B}$ 
**Poznámka** 9.2.5. Obrácená implikace ale obecně neplatí, například pro uspořádané množiny racionálních a reálných čísel platí $\langle\mathbb{Q}, \leq\rangle \equiv\langle\mathbb{R}, \leq\rangle$ ale $\langle\mathbb{Q}, \leq\rangle \nsucceq\langle\mathbb{R}, \leq\rangle$ nebot $\mathbb{Q}$ je spočetná množina zatímco $\mathbb{R}$ není (neexistuje tedy mezi nimi žádná bijekce). 

Pro konečné modely ale platí, že izomorfismus je totéž co elementární ekvivalence, máme-li jazyk s rovností, jak dokážeme v následujícím tvrzení: 
**Tvrzení** 9.2.6. Je-li $L$ jazyk s rovností a $\mathcal{A}, \mathcal{B}$ konečné L-struktury, potom platí: 
$$ 
\mathcal{A} \simeq \mathcal{B} \quad \text { prave } k d y \check{z} \mathcal{A} \equiv \mathcal{B} 
$$ 
**Důkaz**. Jednu implikaci jsme dokázali v Důsledku 9.2.4. Předpokládejme, že $\mathcal{A} \equiv \mathcal{B}$ a ukažme, že existuje izomorfismus $\mathcal{A}$ na $\mathcal{B}$. Protože je jazyk s rovností, můžeme vyjádřit sentencí, že 'existuje právě $n$ prvků'. Z toho plyne, že $|A|=|B|$. 

Označme jako $\mathcal{A}^{\prime}$ expanzi $\mathcal{A}$ o jména prvků z $A$; jde o strukturu v jazyce $L^{\prime}=L \cup\left\{c_a \mid\right.$ $a \in A\}$. Ukážeme, že $\mathcal{B}$ lze expandovat na $L^{\prime}$-strukturu $\mathcal{B}$ tak, že $\mathcal{A}^{\prime} \equiv \mathcal{B}^{\prime}$. Potom, jak lze snadno ověřit, je zobrazení $h(a)=c_a^{\mathcal{B}^{\prime}}$ izomorfismem $\mathcal{A}^{\prime}$ na $\mathcal{B}^{\prime}$, a tedy i izomorfismem jejich $L$-reduktı̊ a $\mathcal{A} \simeq \mathcal{B}$ 

Stačí ukázat, že pro každé $c_a^{\mathcal{A}^{\prime}}=a \in A$ existuje prvek $b \in B$ takový, že pro expanze o interpretaci konstantního symbolu $c_a$ platí $\langle\mathcal{A}, a\rangle \equiv\langle\mathcal{B}, b\rangle$. Označme jako $\Omega$ množinu formulí $\varphi(x)$ takových, že $\langle\mathcal{A}, a\rangle \models \varphi\left(x / c_a\right)$, neboli $\mathcal{A} \models \varphi[e(x / a)]$. Protože je $A$ konečná množina, existuje konečně mnoho formulí $\varphi_1(x), \ldots, \varphi_m(x)$ takových, že pro každou formuli $\varphi \in \Omega$ existuje $i$ takové, že $\mathcal{A} \models \varphi \leftrightarrow \varphi_i$. Potom i $\mathcal{B} \models \varphi \leftrightarrow \varphi_i$ (nebot' $\mathcal{A} \equiv \mathcal{B}$, stačí vzít generální uzávěr této formule, což je sentence). 

Protože v $\mathcal{A}$ platí sentence $(\exists x) \bigwedge_{i=1}^m \varphi_i$ (je splněna díky prvku $a \in A$ ) a $\mathcal{B} \equiv \mathcal{A}$, máme $\mathrm{i}$ $\mathcal{B} \models(\exists x) \bigwedge_{i=1}^m \varphi_i$. Jinými slovy, existuje $b \in B$ takové, že $\mathcal{B} \models(\exists x) \bigwedge_{i=1}^m \varphi_i[e(x / b)]$. Tedy pro každou $\varphi \in \Omega$ platí $\mathcal{B} \models \varphi[e(x / b)]$, tj. $\langle\mathcal{B}, b\rangle \models \varphi\left(x / c_a\right)$, což jsme chtěli dokázat. 

**Důsledek** 9.2.7. Pokud má kompletní teorie v jazyce s rovností konečný model, potom jsou všechny její modely izomorfní. 

### (T13) w-kategorické kritérium kompletnosti. 
$9.3 \omega$-kategorické teorie 
Nyní se podíváme na teorie, které mají jediný spočetně nekonečný model (až na izomorfismus), ř́́káme jim $\omega$-kategorické. ${ }^6$ $I(\kappa, T)$ modelů $T$ kardinality $\kappa$ až na izomorfismus, pro každou kardinalitu $\kappa$ (včetně transfinitnich). Teorie $T$ je $\kappa$-kategorická, pokud $I(\kappa, T)=1$. 

Nadále nás bude zajímat jen případ $\kappa=\omega$, totiž teorie s jediným spočetně nekonečným modelem (až na izomorfismus). Jako příklad uved'me teorii hustého lineárního uspořádání bez konců: 
**Tvrzení** 9.3.2. Teorie DeLO je $\omega$-kategorická. 
Di̊kaz. Vezměme dva spočetně nekonečné modely $\mathcal{A}, \mathcal{B}$ a očíslujme jejich prvky: $A=\left\{a_i \mid\right.$ $i \in \mathbb{N}\}, B=\left\{b_i \mid i \in \mathbb{N}\right\}$. Indukcí podle $n$ lze díky hustotě nalézt posloupnost $h_0 \subseteq h_1 \subseteq$ $h_2 \subseteq \ldots$ prostých (parciálních) funkcí z $A$ do $B$, takových, že $\left\{a_0, \ldots, a_{n-1}\right\} \subseteq \operatorname{dom} h_n$, $\left\{b_0, \ldots, b_{n-1}\right\} \subseteq \operatorname{rng} h_n,{ }^7$ a zachovávají uspořádáni ${ }^8$ Potom $\mathcal{A} \simeq \mathcal{B}$ via $h=\bigcup_{n \in \mathbb{N}} h_n$. 

Pojem $\omega$-kategoricity lze chápat jako zeslabení pojmu kompletnosti. Platí následující užitečné kritérium: 
TOD

jazyce L. Je-li 
- L bez rovnosti, nebo 
- L s rovností a $T$ nemá konečné modely, potom je teorie $T$ kompletní.
  
**Důkaz**. Pro jazyk bez rovnosti víme z Důsledku 9.1.7 Löwenheim-Skolemovy věty, že každý model je elementárně ekvivalentní nějakému spočetně nekonečnému modelu. Ten je ale až na izomorfismus jediný, takže všechny modely jsou elementárně ekvivalentní, což je sémantická definice kompletnosti. 

Máme-li jazyk s rovností, použijeme podobně **Důsledek** 9.1.8 a dostaneme, že všechny nekonečné modely jsou elementárně ekvivalentní. Mohly by existovat elementárně neekvivalentní konečné modely, to jsme ale zakázali. 
**Věta** (Löwenheim-Skolemova). Je-li L spočetný jazyk bez rovnosti, potom každá bezesporná L-teorie má spočetně nekonečný model. 
Tato věta má následující jednoduchý důsledek: 
**Důsledek** 9.1.7. Je-li L spočetný jazyk bez rovnosti, potom ke každé L-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura. 

**Důkaz**. Mějme $L$-strukturu $\mathcal{A}$. Teorie $\operatorname{Th}(\mathcal{A})$ je bezesporná (má model $\mathcal{A}$ ), tedy dle LöwenheimSkolemovy má spočetně nekonečný model $\mathcal{B} \models \operatorname{Th}(\mathcal{A})$. To ale znamená, že $\mathcal{B} \equiv \mathcal{A}$. 

**Věta** (Löwenheim-Skolemova s rovností). Je-li L spočetný jazyk s rovností, potom každá bezesporná L-teorie má spočetný model (tj. konečný, nebo spočetně nekonečný). 
I tato verze má snadný důsledek pro konkrétní struktury: 
**Důsledek** 9.1.8. Je-li L spočetný jazyk s rovností, potom ke každé nekonečné L-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura. 

**Důkaz**. Mějme nekonečnou $L$-strukturu $\mathcal{A}$. Stejně jako v důkazu Důsledku 9.1.7 najdeme spočetně nekonečnou strukturu $\mathcal{B} \equiv \mathcal{A}$. Protože $\mathrm{v} \mathcal{A}$ neplatí pro žádné $n \in \mathbb{N}$ sentence vyjadřující 'existuje nejvýše $n$ prvků' (což lze pomocí rovnosti snadno zapsat), neplatí tato sentence ani $\mathrm{v} \mathcal{B}, \mathcal{B}$ tedy nemůže být konečná struktura. 

### (T14) Neaxiomatizovatelnost konečných modelů. 
Z věty o kompaktnosti snadno získáme následující tvrzení, pomocí kterého lze ukázat neaxiomatizovatelnost např. konečných grafů, konečných grup, konečných těles. 

**Věta** 9.4.4. Pokud má teorie libovolně velké konečné modely, potom má i nekonečný model. $V$ tom případě není třída všech jejích konečných modelů axiomatizovatelná. 

**Důkaz**. Je-li jazyk bez rovnosti, stačí vzít kanonický model pro některou bezespornou větev v tablu z $T$ pro položku $\mathrm{F} \perp$ ( $T$ je bezesporná, nebot má model(y), tedy tablo není sporné). 
Mějme jazyk s rovností a označme jako $T^{\prime}$ následující extenzi teorie $T^{\prime}$ do jazyka rozšířeného o spočetně mnoho nových konstantních symbolů $c_i$ : 
$$ 
T^{\prime}=T \cup\left\{\neg c_i=c_j \mid i \neq j \in \mathbb{N}\right\} 
$$ 
Každá konečná část teorie $T^{\prime}$ má model: necht $k$ je největší takové, že symbol $c_k$ se vyskytuje v $T^{\prime}$. Potom stačí vzít libovolný alespoň $(k+1)$-prvkový model $T$ a interpretovat konstanty $c_0, \ldots, c_k$ jako navzájem různé prvky tohoto modelu. 

Dle věty o kompaktnosti má potom i $T^{\prime}$ model. Ten je nutně nekonečný. Jeho redukt na původní jazyk (zapomenutí konstant $c_i^{\mathcal{A}}$ ) je nekonečným modelem $T$. 

**Poznámka** 9.4.5. Třída všech nekonečných modelů teorie ale je vždy axiomatizovatelná, máme-li jazyk s rovností: stačí k teorii přidat pro každé $n \in \mathbb{N}$ axiom vyjadřující 'existuje alespoň $n$ prvků'. 

### (T15) **Věta** o konečné axiomatizovatelnosti. 
9.4.1 Konečná axiomatizovatelnost 
Ukážeme následující kritérium konečné axiomatizovatelnosti: jak třída struktur $K$ tak i $\bar{K}$ musí být axiomatizovatelné. 

**Věta** 9.4.6 (O konečné axiomatizovatelnosti). Mějme třídu struktur $K \subseteq \mathrm{M}_L$ a uvažme také jeji doplněk $\bar{K}=\mathrm{M}_L \backslash K$. Potom $K$ je konečně axiomatizovatelná, právě když $K i \bar{K}$ jsou axiomatizovatelné. 

**Důkaz**. Je-li $K$ konečně axiomatizovatelná, potom je axiomatizovatelná i konečně mnoha sentencemi $\varphi_1, \ldots, \varphi_n$ (nahradíme formule jejich generálními uzávěry). Jako axiomatizaci $\bar{K}$ stačí vzít sentenci $\psi=\neg\left(\varphi_1 \wedge \varphi_2 \wedge \cdots \wedge \varphi_n\right)$. Zřejmě platí $\mathrm{M}(\psi)=\bar{K}$. 

Naopak, necht $T$ a $S$ jsou teorie takové, že $\mathrm{M}(T)=K$ a $\mathrm{M}(S)=\bar{K}$. Uvažme teorii $T \cup S$. Tato teorie je sporná, nebot: 
$$ 
\mathrm{M}(T \cup S)=\mathrm{M}(T) \cap \mathrm{M}(S)=K \cap \bar{K}=\emptyset 
$$ 
Podle věty o kompaktnosti ${ }^9$ existují konečné podteorie $T^{\prime} \subseteq T$ a $S^{\prime} \subseteq S$ takové, že: 
$$ 
\emptyset=\mathrm{M}\left(T^{\prime} \cup S^{\prime}\right)=\mathrm{M}\left(T^{\prime}\right) \cap \mathrm{M}\left(S^{\prime}\right) 
$$ 
Nyní si všimněme, že platí 
$$ 
\mathrm{M}(T) \subseteq \mathrm{M}\left(T^{\prime}\right) \subseteq \overline{\mathrm{M}\left(S^{\prime}\right)} \subseteq \overline{\mathrm{M}(S)}=\mathrm{M}(T) 
$$ 
tím jsme dokázali, že $M(T)=M\left(T^{\prime}\right)$, tj. teorie $T^{\prime}$ je hledanou konečnou axiomatizací $K$. 

### (T16) Rekurzivně axiomatizovaná teorie s rekurzivnĕ spočetnou kompletací je rozhodnutelná. 
**Definice** 10.1.1 (Rekurzivní axiomatizace). Teorie $T$ je rekurzivně axiomatizovaná, pokud existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $\varphi \in T$. 

**Poznámka** 10.1.2. Ve skutečnosti by nám stačil enumerátor pro $T$, pokud by bylo garantováno, že vypisuje axiomy v lexikografickém uspořádání. To už je ekvivalentní rekurzivní axiomatizaci. (Rozmyslete si proč.) 
10.1.1 Rekurzivně spočetná kompletace 
Požadavek kompletnosti je příliš silný, ukážeme, že stačí pokud jsme schopni efektivně popsat všechny kompletní jednoduché extenze. ${ }^5$ 

**Definice** 10.1.5 (Rekurzivně spočetná kompletace). Řekneme, že teorie $T$ má rekurzivně spočetnou kompletaci, pokud (nějaká) množina až na ekvivalenci všech jednoduchých kompletních extenzí teorie $T$ je rekurzivně spočetná, tj. existuje algoritmus, který pro danou vstupní dvojici přirozených čísel $(i, j)$ vypíše na výstup $i$-tý axiom $j$-té extenze (v nějakém pevně daném uspořádání ${ }^6$ ), nebo odpoví, že takový axiom už neexistuje. ${ }^7$ 

**Tvrzení** 10.1.6. Pokud je teorie $T$ rekurzivně axiomatizovaná a má rekurzivně spočetnou kompletaci, potom je $T$ rozhodnutelná. 

**Důkaz**. Pro danou sentenci $\varphi$ bud' $T \vdash \varphi$, nebo existuje protipříklad $\mathcal{A} \not \models \varphi$, tedy kompletní jednoduchá extenze $T_i$ teorie $T$ taková, že $T_i \nvdash \varphi$. Z kompletnosti ale plyne, že $T_i \vdash \neg \varphi$. Náš algoritmus bude paralelně konstruovat tablo důkaz $\varphi$ z $T$ a (postupně) tablo důkazy $\neg \varphi$ ze všech kompletních jednoduchých extenzí $T_1, T_2, \ldots$ teorie $T .^8$ Víme, že alespoň jedno z paralelně konstruovaných tabel je sporné, a můžeme předpokládat, že konečné (neprodlužujeme-li sporné větve tabla), tedy algoritmus ho po konečně mnoha krocích zkonstruuje. 

### (T17) Nerozhodnutelnost predikátové logiky. 
**Věta** 10.3.1 (O nerozhodnutelnosti predikátové logiky). Neexistuje algoritmus, který by pro danou vstupní formuli $\varphi$ rozhodl, zda je logicky platná. ${ }^{13}$ 

Protože zatím neznáme potřebný formalismus týkající se algoritmů, např. pojem Turingova stroje, zvolíme jako výchozí bod jiný nerozhodnutelný problém. Nejznámějším je tzv. Halting problem, tj. otázka, zda se daný program zastaví na daném vstupu. ${ }^{14} \mathrm{My}$ si ale usnadníme práci tím, že zvolíme jiný nerozhodnutelný problém, tzv. Hilbertův desátý problém. ${ }^{15}$ 
10.3.1 Hilbertův desátý problém 
Mějme polynom $p\left(x_1, \ldots, x_n\right) \mathrm{s}$ celočíselnými koeficienty. Hilbertův desátý problém se ptá po algoritmu, který rozhodne, zda má takový vstupní polynom celočíselný kořen, neboli zda má Diofantická rovnice $p\left(x_1, \ldots, x_n\right)=0$ (celočíselné) řešení: 
"Nalezněte algoritmus, který po konečně mnoha krocích určí, zda daná Diofantická rovnice s libovolným počtem proměnných a celočíselnými koeficienty má celočíselné řěšení." 
Kdyby se Hilbert dožil vyřešení svého desátého problému v roce 1970, byl by překvapen, že žádný takový algoritmus neexistuje. 

**Věta** 10.3.2 (Matiyasevich, Davis, Putnam, Robinson). Problém existence celočíselného reseení dané Diofantické rovnice s celočíselnými koeficienty je (algoritmicky) nerozhodnutelný. 
**Důkaz** zde pro nedostatek místa neuvedeme. K důkazu nerozhodnutelnosti ve skutečnosti použijeme následující důsledek, který mluvío polynomech s přirozenými koeficienty, a o řešení v přirozených číslech 

**Důsledek** 10.3.3. Neexistuje algoritmus, který by pro danou dvojici polynomů $p\left(x_1, \ldots, x_n\right)$, $q\left(x_1, \ldots, x_n\right) s$ přirozenými koeficienty rozhodl, zda mají přirozené řešení, tj. zda platí: 
$$ 
\underline{\mathbb{N}} \models\left(\exists x_1\right) \ldots\left(\exists x_n\right) p\left(x_1, \ldots, x_n\right)=q\left(x_1, \ldots, x_n\right) 
$$ 
**Důkaz** důsledku. **Důkaz** je snadný, využívá faktu, že každé celé číslo lze vyjádřit jako rozdíl dvojice přirozených čísel, a naopak, každé přirozené č́slo lze vyjádřit jako součet čtyř čtverců (celých č́sel). ${ }^{16}$ Každou Diofantickou rovnici lze tedy transformovat na rovnici z dủsledku, a naopak. 
10.3.2 **Důkaz** nerozhodnutelnosti 
Připomeňme, že Robinsonova aritmetika $Q$ má jen konečně mnoho axiomů, $\mathbb{N}$ je jejím modelem, a lze v ní dokázat všechna existenční tvrzení o numerálech platná v $\underline{\mathbb{N}}$. Nyní jsme připraveni dokázat Větu o nerozhodnutelnosti predikátové logiky. 

**Důkaz** věty o nerozhodnutelnosti predikátové logiky. Uvažme formuli $\varphi$ tvaru 
$$ 
\left(\exists x_1\right) \ldots\left(\exists x_n\right) p\left(x_1, \ldots, x_n\right)=q\left(x_1, \ldots, x_n\right) 
$$ 
kde $p$ a $q$ jsou polynomy s přirozenými koeficienty. Dle **Tvrzení** 10.2.3 platí: 
$$ 
\underline{\mathbb{N}} \models \varphi \text { právě když } Q \vdash \varphi 
$$ 
Označme jako $\psi_Q$ konjunkci (generálních uzávěrů) všech axiomů $Q$. Zřejmě $Q \vdash \varphi$, právě když $\psi_Q \vdash \varphi$, což platí právě když $\vdash \psi_Q \rightarrow \varphi$. Dle Věty o úplnosti je to ale ekvivalentní $\models \psi_Q \rightarrow \varphi$. Dostáváme tedy následující ekvivalenci: 
$$ 
\underline{\mathbb{N}} \models \varphi \text { právě když } \vdash \psi_Q \rightarrow \varphi 
$$ 
To znamená, že pokud existoval algoritmus rozhodující logickou platnost, mohli bychom rozhodovat i existenci přirozeného řešení rovnice $p\left(x_1, \ldots, x_n\right)=q\left(x_1, \ldots, x_n\right)$, neboli Hilbertův desátý problém by byl rozhodnutelný. ${ }^{17}$ Což by byl spor. 
Vlastnosti přirozených čísel hrají důležitou roli nejen v matematice, ale například také v kryptografii. Pr̆ipomeňme, že jazyk aritmetiky je jazyk $L=\langle S,+, \cdot 0, \leq\rangle$ s rovností. Jak jsme zmínili v Poznámce 10.1.14, tzv. standardní model aritmetiky $\mathbb{N}=\langle\mathbb{N}, S,+, \cdot, 0, \leq\rangle$ nemá rekurzivně axiomatizovatelnou teorii. Proto používáme rekurzivně axiomatín vlastnosti $\mathbb{N}$ popsat částečně; těmto teoriím říkáme aritmetiky. 
**Definice** 10.2.1 (Robinsonova aritmetika). Robinsonova aritmetika je teorie $Q$ v jazyce aritmetiky sestávající z následujících (konečně mnoha) axiomů: 
$$ 
\begin{array}{ll} 
\neg S(x)=0 & x \cdot 0=0 \\ 
S(x)=S(y) \rightarrow x=y & x \cdot S(y)=x \cdot y+x \\ 
x+0=x & \neg x=0 \rightarrow(\exists y)(x=S(y)) \\ 
x+S(y)=S(x+y) & x \leq y \leftrightarrow(\exists z)(z+x=y) 
\end{array} 
$$ 
$$ 
\begin{aligned} 
& x \cdot 0=0 \\ 
& x \cdot S(y)=x \cdot y+x \\ 
& \neg x=0 \rightarrow(\exists y)(x=S(y)) \\ 
& x \leq y \leftrightarrow(\exists z)(z+x=y) 
\end{aligned} 
$$ 
Robinsonova aritmetika je velmi slabá, nelze v ní dokázat například komutativitu ani asociativitu sčítání či násobení, nebo tranzitivitu uspořádání. 

Na druhou stranu v ní lze dokázat všechna existenční tvrzení o numerálech, která jsou pravdivá $\mathrm{v} \underline{\mathbb{N}}$. Tím myslíme formule, které v prenexním tvaru mají pouze existenční kvantifikátory, a do kterých jsme za volné proměnné substituovali numerály $\underline{n}=S(\ldots S(0) \ldots)$. 
Přiklad 10.2.2. Například, pro formuli $\varphi(x, y)$ tvaru $(\exists z)(x+z=y)$ je $Q \vdash \varphi(\underline{1}, \underline{2})$, kde $\underline{1}=S(0)$ a $\underline{2}=S(S(0))$. 
Platí tedy následující tvrzení, které ponecháme bez důkazu. 
**Tvrzení** 10.2.3. Je-li $\varphi\left(x_1, \ldots, x_n\right)$ existenční formule a $a_1, \ldots, a_n \in \mathbb{N}$, potom platí: 
$$ 
Q \vdash \varphi\left(x_1 / \underline{a_1}, \ldots, x_n / \underline{a_n}\right) \text { právě } k d y \check{~} \underline{\mathbb{N}} \models \varphi\left[e\left(x_1 / a_1, \ldots, x_n / a_n\right)\right] 
$$ 
Užitečným rozšíř́ním Robinsonovy aritmetiky je tzv. Peanova aritmetika, ve které lze dokazovat indukci: 
