---
tags:
  - nail062log
---
**(L20) Gödelovy věty o neúplnosti a jejich důsledky (bez důkazů).**
- Pro každou bezespornou rekurzivně axiomatizovanou extenzi $T$ Robinsonovy aritmetiky existuje sentence, která je pravdivá v $\underline{\mathbb{N}}$, ale není dokazatelná v $T$
	- Jde o pravdivost v $\underline{\mathbb{N}}$, ale dokazatelnost je v $T$
- Důsledky:
	- je-li navíc $\underline{\mathbb{N}}\in M(T)$, pak ani $T$ není kompletní
		- nechť $\varphi$ je pravdivá v $\underline{\mathbb{N}}$, ale není dokazatelná v $T$
		- pak bychom dokázali $T \vdash \neg \varphi$ díky kompletnosti, což je ve sporu s pravdivosti $\varphi$
	- teorie $Th(\underline{\mathbb{N}})$ není rekurzivně axiomatizovatelná
		- jinak by nemohla být kompletní, ale je
	- Rosserův trik - v každé bezesporné rekurzivně axiomatizované extenzi Robinzonovy aritmetiky existuje nezávislá sentence = taková extenze není kompletní
	- 2. věta o neúplnosti - Pro každou bezespornou RA extenzi $T$ Peanovy aritmetiky platí, že $Con_{T}$ není dokazatelná v $T$
		- $Con_{T}$ je sentence vyjadřující bezespornost teorie $T$
		- bezespornost není dokazatelná v bezesporné RA extenzi Peanovy aritmetiky
	- Existuje bezesporná RA extenze Peanovy aritmetiky, která dokazuje svou spornost: $T \vdash \neg Con_{T}$
	- Je-li ZFC bezesporná, nemůže být $Con_{ZFC}$ dokazatelná