---
tags:
  - nail062log
---
Dokazatelnost $T \vdash \varphi$
- schopnost syntakticky vyvést výrok z teorie T

Vlastnosti dokazovacího systému
- **Korektnost** - je-li dokazatelný, je pravdivý: $$T \vdash \varphi \Rightarrow T \models \varphi$$
- **Úplnost** - je-li pravdivý, dá se dokázat: $$T \models \varphi \Rightarrow T \vdash \varphi$$
[[Rezoluční metoda]]
[[Tablo metoda]]

### Aplikace vět o úplnosti a korektnosti
**(T11) Löwenheim-Skolemova věta včetně varianty s rovností, jejich důsledky.**
- Bez rovnosti:
	- $L$ je spočetný jazyk bez rovnosti =>  Každá bezesporná teorie $T_{L}$ má spočetně nekonečný model
	- Důkaz:
		- Nechť máme dokončené systematické tablo z bezesporné $T$ s $F \bot$ v kořeni
		- $T$ je bezesporná => není v ní dokazatelný spor => obsahuje bezespornou větev
		- Spočetně nekonečný model je pak $L$-redukt kanonického modelu pro tuhle větev
- S rovností:
	- Je-li $L_{=}$, pak ke každé nekonečné $L$-struktuře existuje elementárně ekvivalentní spočetně nekonečný model
	- Důkaz:
		- mějme nekonečnou $\mathcal{A}_{L}$, najdeme společně nekonečnou strukturu$\mathcal{B}\equiv \mathcal{A}$
		- protože v $\mathcal{A}$ neplatí pro žádné $n \in \mathbb{N}$ sentence "existuje nejvýš $n$ prvků", tato sentence neplatí ani v $\mathcal{B}$, tedy musí být konečná struktura
- Důsledky:
	- Je-li $L$ spočetný jazyk bez rovností, pak ke každé $L$-struktuře existuje elementárně ekvivalentní spočetně nekonečná struktura
		- $L$-struktura $\mathcal{A}$, teorie $Th(\mathcal{A})$ je bezesporná (má model $\mathcal{A}$), tedy dle LS věty má spočetně nekonečný model $\mathcal{B}\models Th(\mathcal{A})$, to ale znamená $\mathcal{B} \equiv \mathcal{A}$
