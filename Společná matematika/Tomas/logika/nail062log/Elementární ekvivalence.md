---
tags:
  - nail062log
---
**Teorie struktury** $Th(\mathcal{A})$
- všechny $L$-sentence, které platí v $\mathcal{A}$
- $$Th(\mathcal{A})=\{\varphi| \varphi\text{ je L-sentence a } \mathcal{A}\models \varphi\}$$
- Např. pro standardní model aritmetiky $\underline{\mathbb{N}}$
- $Th(\mathbb{\underline{N}})$ - aritmetika přirozených čísel
- Nechť $\mathcal{A}$ je $L$-struktura a $T$ je $L$-teorie:
	- $Th(\mathcal{A})$ je kompletní
	- je-li $\mathcal{A}\in M_{L}(T)$, pak $Th(\mathcal{A})$ je kompletní jednoduchá extenze $T$
	- Pokud $\mathcal{A}\in M_{L}(T)$ a $T$ je kompletní, pak $Th(\mathcal{A}) \sim T$, jsou ekvivalentní a $Th(\mathcal{A})=Csq_{L}(T)$

**Elementární ekvivalence**: $$\mathcal{A}\equiv \mathcal{B} \Leftrightarrow Th(\mathcal{A}) = Th(\mathcal{B})$$
- např. $\langle \mathbb{R}, \leq \rangle \equiv \langle \mathbb{Q}, \leq \rangle$
- Místo modelů stačí najít všechny kompletní jednoduché extenze
	- modely $T$ až na el. ekv. jednoznačně odpovídají kompletním jednoduchým extenzím $T$
