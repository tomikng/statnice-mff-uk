---
tags:
  - nail062log
---
## Výroková logika
**Jazyk** $\mathbb{P}$
- neprázdná uspořádaná množina prvovýroků (=atomických [[Výrok (výroková formule)|výroků]]) $\mathbb{P}$
- uspořádání je bijekce $\iota: \mathbb{N} \to \mathbb{P}$
	- $\iota(0)=p$, $\iota(1)=q$, $\iota(2)=r$...

> [!example] 
> $$\mathbb{P}=(\{p,q,r\}, \{\neg,\wedge ,\vee , \to, \leftrightarrow\})$$
## Predikátová logika
**Jazyk** $L$
- spočetně mnoho proměnných
- relační, funkční a konstantní symboly ze signatury a případně "="
- kvantifikátory $\forall \exists$ pro každou proměnnou $x \in Var$
- logické spojky a závorky

**Term** jazyka $L$
- Syntaktický zápis, obsahuje pouze symboly jazyka, nikoliv konkrétní struktury, nemá pravdivostní hodnotu
- induktivně:
	- každá proměnná a konstantní symbol z $L$ je term
	- pro $f \in L$ arity $n$ a termy $t_{1\dots n}$ je $f(t_{1},\dots,t_{n})$ také term
- $Term_{L}$ - množina všech termů
- $Tree(t)$ - strom termu, viz strom výroku
- Podterm - podřetězec, je sám termem
- **Konstantní term (ground)** - neobsahuje proměnné
- **Sémantika termu** - ohodnocení proměnných prvky, nahrazení symbolů interpretacemi struktury

**Univerzální množina spojek** S
- S je univerzální, pokud lze každou booleovskou funkci vyjádřit jako [[Pravdivostní funkce|pravdivostní funkcí]] nějakého výroku vybudovaného z těchto logických spojek
- S je univerzální, pokud pro každý konečný n-prvkový jazyk $\mathbb{P}$ a každou podmnožinu jeho modelů $M \subseteq  M_{\mathbb{P}}$ musí existovat odpovídající výrok $\varphi$ s množinou modelů $M_{\mathbb{P}}(\varphi)=M$
	- pro každou podmnožinu jazykových modelů existuje výrok, který ji modeluje
- Ekvivalence vzplývá z nutnosti zvolit $M_{\mathbb{P}}(\varphi)=M$ pro množinu vzoru jedničky $M=f^{-1}[1]$ ($M_{\mathbb{P}}(\varphi)$ je množina modelů, kde se výrok vyhodnotí jako 1)
- $\{\neg,\wedge ,\vee \}$ a $\{\neg, \to\}$ jsou univerzální
	- každý model lze vyjádřit v CNF a DNF
	- implikaci lze vyjádřit jako konjunkci a disjunkci