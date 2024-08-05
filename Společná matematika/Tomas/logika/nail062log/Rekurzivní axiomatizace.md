---
tags:
  - nail062log
---
**(P24) Rekurzivní axiomatizace, rekurzivní axiomatizovatelnost, rekurzivně spočetná kompletace.**
- **Rekurzivní axiomatizace**
	- Enumerátor - algoritmus, který vypíše axiomy ze spočetné $T$
		- nikdy se nedočkáme, ale kdyby vypisoval v lexikografickém pořadí, budeme vědět, kdy ho má vypsat
	- $T$ je rekurzivně axiomatizovaná <=> existuje algoritmus, který pro každou vstupní formuli $\varphi$ doběhne a odpoví, zda $\varphi\in T$
- **Rekurzivně spočetná kompletace**
	- Teorie $T$ má RSK <=> nějaká množina všech jejích jednoduchých kompletních extenzí (až na ekvivalenci) je **rekurzivně spočetná** - existuje algoritmus, který pro danou vstupní dvojici $(i,j)$
		- vypíše na výstup $i$-tý axiom $j$-té extenze
		- nebo odpoví, že neexistuje, je-li extenzí méně než $j$ nebo $j$-tá má $<i$ axiomů
		- potřebujeme spočetný jazyk
- **Rekurzivní axiomatizovatelnost**
	- Třída $L$-struktur $K \subseteq M_{L}$ je rekurzivně axiomatizovatelná, pokud existuje rekurzivně axiomatizovatelná L-teorie $T: K=M_{L}(T)$
	- Teorie $T'$ je RA, pokud je RA třída jejích modelů nebo pokud je $T'$ ekvivalentí nějaké RA teorii

**(P25) Rozhodnutelná a částečně rozhodnutelná teorie.**
- Teorie je **rozhodnutelná**, pokud existuje algoritmus, který pro každou $\varphi$ doběhne a řejne, zda $T \models \varphi$
- Teorie je **částečně rozhodnutelná**, pokud existuje algoritmus, který pro každou platnou formuli odpoví "ano" a pro neplatnou buď nedoběhne nebo odpoví "ne"
- Předpokládáme, že $\varphi$ je sentence

**(L18) Rekurzivně axiomatizovaná teorie je částečně rozhodnutelná, kompletní je rozhodnutelná.**
- Důkaz:
	- Algoritmem pro částečnou je konstrukce systematického tabla pro $F \varphi$. Pokud platí, konstrukce skončí v konečně mnoha krocích, jinak nemusí skončit
	- Je-li $T$ kompletní, víme, že buď $T \vdash \varphi$ nebo $T \vdash \neg \varphi$, pak paralelně konstruujeme obě tabla, jedna konstrukce doběhne po konečně mnoha krocích

**(T16) Rekurzivně axiomatizovaná teorie s rekurzivně spočetnou kompletací je rozhodnutelná.**
- RA teorie s RSK je rozhodnutelná
- Důkaz:
	- Pro sentenci $\varphi$ buď $T \vdash \varphi$ nebo existuje protipříklad $\mathcal{A}\not\models \varphi$, tedy kompletní jednoduchá extenze $T_{i} \not\vdash \varphi$ 
	- Z kompletnosti extenzí plyne, že $T_{i} \vdash \neg \varphi$ - algoritmus paralelně konstruuje tabla pro $\varphi$ z $T$ a $\neg \varphi$ ze všech kompletních jednoduchých extenzí $T_{1},\dots$
	- Víme, že alespoň 1 je sporné a algoritmus doběhne
- Příklady:
	- Booleovy algebry
	- Algebraicky uzavřená tělesa
	- Komutativní grupy
	- Jsou nekompletní, ale rekurzivně axiomatizované s rekurzivně spočetnou kompletaci

**(L19) Teorie konečné struktury v konečném jazyce s rovností je rozhodnutelná.**
- Tvrzení: Je-li $\mathcal{A}$ konečná struktura v konečném jazyce $L_{=}$, je $Th(\mathcal{A})$ rekurzivně axiomatizovatelná
	- Důkaz:
		- očíslujeme prvky domény
		- $Th(\mathcal{A})$ axiomatizujeme sentencí ve tvaru "existuje právě $n$ prvků $a_{1},\dots a_{n}$ splňujících základní vztahy o funkčních hodnotách a relacích z $\mathcal{A}$"
	- Důsledek:
		- Teorie konečné struktury v konečném jazyce je rozhodnutelná
			- $Th(\mathcal{A})$ je kompletní z definice
	- Rekurzivní axiomatizovanost a kompletnost => rozhodnutelnost
	- Příklady:
		- $Th(\mathcal{A})$ je rekurzivně axiomatizovatelná a kompletní => je rozhodnutelná
		- DeLO
		- diskrétní lineární uspořádání
		- následník s nulou
		- [!] Standardní model aritmetiky nemá RA teorii