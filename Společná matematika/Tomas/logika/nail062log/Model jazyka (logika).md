---
tags:
  - nail062log
aliases:
  - Struktura (logika)
---
## Výroková logika
**Model jazyka** $v \in M_\mathbb{P}$
- libovolné pravdivostní ohodnocení nad [[Jazyk (logika)|jazykem]] $\mathbb{P}$ $$v: \mathbb{P} \to \{0,1\}$$, např. $v=\{(p,1),(q,0),(r,1)\}$
- $M_\mathbb{P}$ - množina všech ohodnocení nad jazykem $\mathbb{P}$ $$M_\mathbb{P} =\{v|v: \mathbb{P} \to \{0,1\}\}$$
- Mapujeme $(1,0,1) \to ((p,1),(q,0),(r,0))$ pomocí uspořádání $\iota$
	- $(1,0,1)=(v \circ \iota)(0,1,2)=(v(\iota(0)),v(\iota(1)),v(\iota(2)))$

Platnost výroku (**model výroku**) $v \models \varphi$
- model výroku je takový model jazyka, při kterém výrok dává pravdivostní hodnotu 1: $$v \in M_\mathbb{P}: f_{\varphi, \mathbb{P}}(v)=1$$
- $M_{\mathbb{P}}(\varphi)$ - množina všech modelů výroku $\varphi$, analogicky nemodelů $\overline{M_{\mathbb{P}}(\varphi)} = M_\mathbb{P} \backslash M_{\mathbb{P}}(\varphi)$:$$\begin{align*}
M_{\mathbb{P}}(\varphi) &= \{v\in M_\mathbb{P} | v \models \varphi\}=f_{\varphi,\mathbb{P}}^{-1}[1]\\
\overline{M_{\mathbb{P}}(\varphi)} =M_\mathbb{P} \backslash M_{\mathbb{P}}(\varphi)&= \{v\in M_\mathbb{P} | v \not\models \varphi\}=f_{\varphi,\mathbb{P}}^{-1}[0]
\end{align*}$$
Platnost teorie (**model teorie**) $v \models T$
- $T$ platí v modelu $v$, pokud každý její axiom v něm platí
	- $T = \emptyset$ to splňuje pro všechny modely jazyka, tedy $M_{\mathbb{P}}(T) =  M_{\mathbb{P}}$
- $M_{\mathbb{P}}(T)$ - množina všech modelů teorie $T$
- $M_{\mathbb{P}}(T, \varphi) = M_{\mathbb{P}}(T \cup \{\varphi\})$ - modely teorie $T$ s přidaným výrokem $\varphi$
	- $M_{\mathbb{P}}(T, \varphi) = M_{\mathbb{P}}(T) \cap M_{\mathbb{P}}(\varphi)$
- $M_{\mathbb{P}}(T) = \bigcap_{\varphi \in T}M_{\mathbb{P}}(\varphi)$ - modely teorie jsou sjednocením modelů všech axiomů
- $\mathrm{M}_{\mathbb{P}}\left(\varphi_1\right) \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2\right) \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2, \varphi_3\right) \supseteq \cdots \supseteq \mathrm{M}_{\mathbb{P}}\left(\varphi_1, \varphi_2, \ldots, \varphi_n\right)$. -  čím více axiomů přidáme, tím více se zmenší množina modelů teorie
	- => místo toho, abychom dělali průník množin modelů axiomů, je tedy efektivnější nahlednout, co nám vyloučí nejvíc modelů

## Predikátová logika
formule platí ve struktuře = platí při každém ohodnocení volných proměnných prvky z domény
hodnoty termů se vyhodnocují podle stromu nahrazením interpretacemi
z termů získáme pravdivostní hodnoty - je výsledná n-tice v relaci?
hodnoty formulí vyhodnoculeme podle stromu

**Signatura**
- $\langle \mathcal{R}, \mathcal{F} \rangle$ - relační a funkční symboly (včetně konstantních) bez symbolu rovnosti spolu s aritami $$ar: \mathcal{R} \cup \mathcal{F} \to \mathbb{N}$$

**Struktura** v signatuře $\langle \mathcal{R}, \mathcal{F} \rangle$
- "model" v PL
- $$\mathcal{A} = \langle A, \mathcal{R}^{\mathcal{A}}, \mathcal{F}^{\mathcal{A}} \rangle$$
- $A$ je doména/univerzum, neprázdná množina
- $\mathcal{R}^{\mathcal{A}} = \{R^{\mathcal{A}} | R \in \mathcal{R}\}$, kde $R^{\mathcal{A}} \subseteq A^{ar(R)}$ interpretace relačního symbolu $R$
	- interpretace R je nějaká podmnožina domény A vzhedem k aritě R (dvojice, trojice atp.)
- $\mathcal{F}^{\mathcal{A}} = \{f^{\mathcal{A}} | f \in \mathcal{F}\}$, kde $f^{\mathcal{A}}: A^{ar(f)} \to A$ je interpretace funkčního symbolu $f$
	- $c\in \mathcal{F}: c^{\mathcal{A}}\in A$ - konstantě se přiřadí prvek z domény, arita 0
	- vezme $ar(f)$ prvků domény A a vrátí jeden prvek z A

Model jazyka $L$ (**$L$-struktura**)
- libovolná struktura v signatuře jazyka $L$
- $M_{L}$ - třída všech modelů

**Platnost ve struktuře**
- formule $\varphi$ a struktura $\mathcal{A}$ v jazyce $L$
- $\mathcal{A} \models \varphi[e]$ - $\varphi$ **platí** ve struktuře $\mathcal{A}$: $$PH^\mathcal{A}(\varphi)[e]=1$$
	- jinak neplatí, $\mathcal{A} \not\models \varphi[e]$ neboli $PH^\mathcal{A}(\varphi)[e]=0$
- $\mathcal{A} \models \varphi$ - $\varphi$ je **pravdivá** v $\mathcal{A}$: platí v každém ohodnocení $e: Var \to A$ 
- $\mathcal{A} \models \neg \varphi$ - $\varphi$ je **lživá** v $\mathcal{A}$: neplatí v žádném ohodnocení
- vlastnosti
	- $\mathcal{A} \models \neg \varphi[e]$ <=> $\mathcal{A} \not\models \varphi[e]$
	- $\mathcal{A} \models \varphi$ => $\mathcal{A}\not\models \neg \varphi$, ekvivalence pro sentence

**Generální uzávěr**
- Sentence, která váže zbytek volných proměnných na univerzální kvantifikátor $(\forall x)$
- Formule platí ve struktuře <=> platí její generální uzávěr
