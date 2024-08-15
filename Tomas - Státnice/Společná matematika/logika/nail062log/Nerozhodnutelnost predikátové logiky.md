---
tags:
  - nail062log
---
**(T17) Nerozhodnutelnost predikátové logiky.**
- Neexistuje algoritmus, který by pro vstupní formuli $\varphi$ rozhodl, zda je logicky platná
- Prázdná teorie není rozhodnutelná
- Hilbertův desátý problém
	- neexistuje algoritmus, který by pro danou dvojici polynomů s přirozenými koeficienty rozhodl, zda mají přirozené řešení
	- zda platí $\underline{\mathbb{N}}\models \varphi$
- Důkaz:
	- $$Q\vdash \varphi \Leftrightarrow \underline{\mathbb{N}}\models \varphi$$
	- $Q$ - Robinsonova aritmetika, hledáme přirozená řešení
	- Konjunkci generálních uzávěrů všech axiomů $Q$ označíme jako $\psi_{Q}$
	- $Q \vdash \varphi \Leftrightarrow \psi_{Q} \vdash \varphi \Leftrightarrow \psi_{Q} \to \varphi \Leftrightarrow \models \psi_{Q} \to \varphi$
		- poslední ekvivalence dle věty o úplnosti tabla
	- tedy $\underline{N}\models \varphi \Leftrightarrow  \models \psi_{Q} \to \varphi$
	- Spor s důsledkem, že Hilbertův desátý problém je nerozhodnutelný
