---
tags:
  - nail062log
---
**Extenze teorie** (VL)
- Libovolná teorie T' v nadjazyku P', která splňuje všechny důsledky původní teorie $$Csq_{\mathbb{P}}(T) \subseteq Csq_{\mathbb{P'}}(T'); \ \mathbb{P} \subseteq \mathbb{P}'$$
	- <=> $M_{\mathbb{P'}}\subseteq M_{\mathbb{P'}}(T)$ nad rozšířeným jazykem
	- ekvivalentní teorie $T' \sim T$ jsou si navzájem extenzí
	- modely **kompletní jednoduché extenze** jednoznačně odpovídají modelům T až na ekvivalenci
	- má-li teorie **kompletní konzervativní extenzi**, je sama nutně kompletní
- **Restrikce** na původní jazyk musí být modelem $T$, $$\{ v\upharpoonright_\mathbb{P} | v \in M_{\mathbb{P'}}(T') \} \subseteq M_{\mathbb{P}}(T)$$
	- odstraňuje nadbytečné proměnné z modelů
- **Jednoduchá** - nad stejným jazykem
	- $\mathbb{P'}=\mathbb{P}$ a $M_{\mathbb{P}}(T')\subseteq M_{\mathbb{P}}(T)$ 
- **Konzervativní** - $$Csq_{\mathbb{P}}(T)=Csq_{\mathbb{P}}(T')=Csq_{\mathbb{P'}}(T')\cap VF_{\mathbb{P}}$$
	- každý nový důsledek $\varphi'$ musí obsahovat novou proměnnou z $\mathbb{P}'$, jinak bychom měnili platnost předchozích
	- <=> $T'$ konzervativní, když je extenzí a každý původní model $v \in M_{\mathbb{P}}(T)$ lze rozšířit na model $M_{\mathbb{P'}}(T')$: $$\{ v\upharpoonright_\mathbb{P} | v \in M_{\mathbb{P'}}(T') \} = M_{\mathbb{P}}(T)$$
		- každý model T získáme restrikcí T' na jazyk P

**Extenze teorie** (PL)
- $L' \supseteq L$, $Csq_{L}(T) \supseteq Csq_{L'}(T')$
	- $M_{L}(T')\subseteq M_{L}(T)$
	- redukt každého modelu $T'$ na $L$ je modelem $T$
		- máme model $\mathcal{A'} \models T'_{L'}$
		- $T'_{L'}$ je extenze $T_{L}$, tedy $\mathcal{A'}\models \varphi\in T_{L}$
		- $\mathcal{A}\models \varphi$, protože ty obsahují pouze symboly z $L$
- **jednoduchá** - $L'=L$
- **konzervativní** - $Csq_{L}(T)=Csq_{L}(T')$ - teorie $T$ redukovaná na formule $Fm_{L}$
	- $M_{L}(T') = M_{L}(T)$
	- každý model $T$ lze expandovat do $L'$ na model $T'$
		- Pro libovolnou sentenci $T'_{L'} \models \varphi$, chceme $T_{L} \models \varphi$ 
		- Každý model $\mathcal{A}\models T_{L}$ lze expandovat na $\mathcal{A'}\models T'_{L}$
		- $\mathcal{A'}\models \varphi \Rightarrow \mathcal{A}\models \varphi \Rightarrow T_{L} \models \varphi$
		- => $M_{L}(T') = M_{L}(T)$
- Teorie jsou ekvivalentní, když jsou si navzájem extenzí, $M_{L}(T')=M_{L}(T)$
