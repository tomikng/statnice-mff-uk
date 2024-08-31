---
dg-publish: true
tags:
  - tomas
  - spolecna_matematika
  - past
---
> [!danger] **Upozornění:** 
> Poznámky jsou od [Tomáše Slámy](https://www.slama.dev), kde jsou upravený do tohohle formátu pro tisk

### Úvod

**Definice (prostor jevů)** je $\mathcal{F} \subseteq \mathcal{P}(\Omega)$, pokud

- $\emptyset \in \mathcal{F}$ a $\Omega \in \mathcal{F}$
- je uzavřený na doplňky: $A \in \mathcal{F} \implies \Omega \setminus A \in \mathcal{F}$ a
- je uzavřený na sjednocení: $A_1, A_2, \ldots\ \in \mathcal{F} \implies \bigcup_{i = 1}^{\infty} A_i \in \mathcal{F}$

Množině $\Omega$ říkáme prostor elementárních jevů.

**Definice (pravděpodobnost)** je funkce $P : \mathcal{F} \mapsto \left[0, 1\right]$ se nazývá pravděpodobnost, pokud

- $P(\emptyset) = 0, P(\Omega) = 1$ a
- $P\left(\bigcup_{i = 1}^{\infty} A_i\right) = \sum_{i = 1}^{\infty} P(A_i)$ pro libovolnou posloupnost **po dvou** disjunktních jevů $A_1, A_2, \ldots \in \mathcal{F}$

**Definice (pravděpodobnostní prostor)** je trojice $\left(\Omega, \mathcal{F}, P\right)$ taková, že

- $\Omega \neq \emptyset$ je libovolná množina (prostor elementárních jevů),
- $\mathcal{F} \subseteq \mathcal{P}(\Omega)$ je prostor jevů, a  
- $P$ je pravděpodobnost přiřazující každému jevu pravděpodobnost.

**Příklad (pravděpodobností prostory):**
- **konečný s uniformní pravděpodobností:** $\Omega$ je libovolná konečná množina, $P(A) = |A| / |\Omega|$
- **diskrétní:** $\Omega$ je libovolná *spočetná* množina
- **spojitý:** $\Omega \subseteq \mathbb{R}^n$, $\mathcal{F}$ vhodná, $P$ definován přes integrál (viz dále)

![[Pasted image 20240831073338.png]]
Znázornění konečného prostoru s uniformní pravděpodobností. dvojice hodů kostkou jsou elementární jevy ($\in \Omega$), vyznačené množiny jsou měřené jevy ($\in \mathcal{F}$).

**Lemma (základní vlastnosti):** *$\forall A, B \in \mathcal{F}$ platí*

- $P(A) + P(A^C) = 1$
- $A \subseteq B \implies P(A) \le P(B)$  
- $P(A \cup B)$ = $P(A) + P(B) - P(A \cap B)$
- $P(A_1 \cup A_2 \cup \ldots) \le \sum P(A_i)$

**Definice (podmíněná pravděpodobnost):** pokud $A, B \in \mathcal{F}$ a $P(B) > 0$, tak definujeme podmíněnou pravděpodobnost $A$ při $B$ jako 

$$P(A \mid B) = \frac{P(A \cap B)}{P(B)}$$

**Věta (o úplně pravděpodobnosti):** *Pokud $A_1, \ldots, A_n \in \mathcal{F}$ a $P(A_1 \cap A_2 \cap \ldots \cap A_n) > 0$, tak 

$$P(A_1 \cap A_2 \cap \ldots \cap  A_n) = P(A_1)\ P(A_2 \mid A_1)\ P(A_3 \mid A_2 \cup A_1) \ldots$$

**Definice (rozklad):** spočetný systém množin $B_i \in \mathcal{F}$ je rozklad $\Omega$, pokud

- $B_i \cap B_j = \emptyset$ pro $i \neq j$ a
- $\bigcup_{i} B_i = \Omega$

**Věta (rozbor všech možností):** *Pokud $A_1, \ldots, A_n \in \mathcal{F}$ je rozklad $\Omega$ a $A \in \mathcal{F}$, pak 

$$P(A) = \sum_{i } P(A \mid B_i) P(B_i)$$

**Věta (Bayesova):** *pokud $B_1, B_2, \ldots$ je rozklad $\Omega$, $A \in \mathcal{F}$ a $P(A), P(B_j) >0 $, tak 

$$P(B_j \mid A) = \frac{P(B_j) P(A \mid B_j)}{P(A)}  = \frac{P(A \mid B_j) P(B_j)}
{\sum_{i} P(A \mid B_i) P(B_i)}$$

Věta řeší problém, kdy máme jev $H$ (hypotézu), který chceme spočítat, když platí jev $E$ (evidence). Použitím Bayesova vzorce dostáváme 

$$P(H \mid E) = \frac{P(E \mid H) P(H)}{P(E)}$$

což intuitivně dává smysl – při pravděpodobnosti $H \mid E$ musíme zohlednit pravděpodobnost $E$.

![[Pasted image 20240831073621.png]]

**Poznámka:** 3b1b udělal o Bayesově větě [pěkné video](https://www.youtube.com/watch?v=HZGCoVF3YvM), ze kterého jsem vykradl obrázek výše.

**Definice (nezávislost jevů):** dva jevy jsou nezávislé, pokud $P(A \cap B) = P(A) P(B)$

### Diskrétní náhodné veličiny

**Definice (diskrétní náhodná veličina):** Pro pravděpodobnostní prostor $\Omega, \mathcal{F}, P$ mějme funkci $X : \Omega \mapsto \mathbb{R}$ nazvene diskrétní náhodná veličina, pokud $\mathrm{Im}(X)$ (obor hodnot) je spočetná množina a pokud $\forall x$ platí 

$$\left\{\omega \in \Omega: X(\omega) = x\right\} \in \mathcal{F}$$

**Příklad (použití náhodných veličin):**
- hodíme na terč a měříme vzdálenost od středu
- házíme kostkou, dokud nepadne šestka a pak nás zajímá počet hodů

**Definice (pravděpodobnostní funkce)** (pmf) diskrétní náhodné veličiny $X$ je funkce $p_X : \mathbb{R} \mapsto \left[0, 1\right]$ taková, že

$$p_X(x) = P(X = x) = P(\left\{\omega \in \Omega : X (\omega) = x\right\})$$

#### Rozdělení 

##### Bernoulli
- $X \cdot$ počet orlů při jednom hodu nespravedlivou mincí (značíme $X \sim \mathrm{Bern}(p)$)
- $p_X (1) = p$ a $p_X(0) = 1 - p$, jinak $p_X(k) = 0$

##### Binomiální
- $X \ldots$ počet orlů při $n$ hodech nespravedlivou mincí (značíme $X \sim \mathrm{Bin}(n, p)$)
- méně očivivně $p_X(k) = \binom{n}{k} p^k (1 - p)^{n - k}$
  - chceme, aby se $k$ hodů trefilo a $n - k$ netrefilo

##### Poissonovo
- limita $\mathrm{Bin}(n, \lambda / n)$, popisuje např. počet mailů za hodinu

##### Geometrické
- $X \ldots$ kolikátým hodem mincí padl první orel (značíme $X \sim \mathrm{Geom}(p)$)
- $p_X(k) = (1 - p)^{k-1} p$
  - chceme, aby se prvních $k$ hodů trefilo a poslední netrefil

#### Střední hodnota
**Definice (střední hodnota diskrétní n.v.)** $\mathbb{E}(X)$ je definována jako 

$$\mathbb{E}(X) = \sum_{x \in \mathrm{Im}(X)} x P(X = x)$$

pokud součet dává smysl.

**Věta (LOTUS):** *pokud $X$ je n.v. a $g$ reálná funkce, tak 

$$\mathbb{E}(g(X)) = \sum_{x \in \mathrm{Im}(X)} g(x) P(X = x)$$

**Lemma (vlastnosti střední hodnoty):** *nechť $X, Y$ jsou diskrétní n.v. a $a, b \in \mathbb{R}$; pak*

- pokud $P(X \ge 0) = 1$ a $\mathbb{E}(X) = 0$, tak $P(X = 0) = 1$
- pokud $\mathbb{E}(X) \ge 0$, tak $P(X \ge 0) > 0$
- $\mathbb{E}(aX + bY) = a\mathbb{E}(X) + b\mathbb{E}(Y)$ (linearita střední hodnoty)

**Definice (rozptyl/variance)** n.v. nazveme 

$$var(X) = \mathbb{E}\left(\left(X - \mathbb{E}X\right)^2\right)$$

- má intuitivní význam – jedná se o očekávanou vzdálenost ($^2$) od střední hodnoty

**Definice (směrodatná odchylka)** je 

$$\sqrt{var(x)}$$

**Věta:** 

$$var(X) = \mathbb{E}(X^2) - \mathbb{E}(X)^2$$

Přehled parametrů známých rozdělení:

| Rozdělení | $\mathbb{E}$ | $var$ |
|-----------|-------------|-------|
| $\mathrm{Bern(p)}$ | $p$ | $p(1 - p)$ |
| $\mathrm{Bin(n,p)}$ | $np$ | $np(1 - p)$ |
| $\mathrm{Geom(p)}$ | $1/p$ | $np(\frac{1 - p}{p^2})$ |
| $\mathrm{Pois(\lambda)}$ | $\lambda$ | $\lambda$ |

#### Sdružené rozdělení
**Definice:** pro diskrétní n.v. $X, Y$ definujeme jejich sdruženou pravděpodobnostní funkci (joint pmf) $p_{X, Y} : \mathbb{R}^2 \mapsto \left[0, 1\right]$ jako 

$$p_{X, Y} (x, y) = P(\left\{\omega \in \Omega : X(\omega) = x \land Y(\omega) = y\right\})$$

**(👀):** z $p_{X, Y}$ (**sdruženého**) jde $p_X, p_Y$ (**marginální**) zjistit, jednoduše, zpětně ne vždy.

**Definice (nezávislé náhodné veličiny):** veličiny $X, Y$ jsou nezávislé, pokud $\forall x, y \in \mathbb{R}$ platí 

$$P(X = x, Y = y) = P(X = x) P(Y = y)$$

neboli

$$p_{X, Y}(x, y) = p_X(x) p_Y (y)$$

**Věta (součin n.n.v.):** *pro nezávislé diskrétní veličiny $X, Y$ platí 

$$\mathbb{E}(XY) = \mathbb{E}(X)\mathbb{E}(Y)$$

**Definice (podmíněné rozdělení):** pro $X, Y$ d.n.v. a $A \in \mathcal{F}$ definujeme 

$$p_{X \mid A} (x) = P(X = x \mid A)$$ 

$$p_{X \mid Y} (x \mid y) = P(X = x \mid Y = y)$$

**Příklad:** Pro $X, Z$ výsledky dvou nezávislých hodů šestihranou kostkou a $Y = X + Z$ nás zajímá $p_{X \mid Y} (6 \mid 10)$ (jaká je šance, že na kostce padla hodnota $6$, když součet na obou byl $10$). Můžeme spočítat ze sdruženého:

$$p_{X \mid Y}(x \mid y) = \frac{P(X = x, Y = y)}{P(Y = y)} = \frac{p_{X, Y}(x, y)}{p_Y(y)} = \frac{p_{X, Y}(x, y)}{\sum_{x' \in \mathrm{Im}(X)} p_{X, Y} (x', y)}$$

| $p_{X, Y}$ | $\ldots$ | 10 | 11 | 12 |
|:----------:|:--------:|:--:|:--:|:--:|
| 1 |  | $0$ | $0$ | $0$ |
| 2 |  | $0$ | $0$ | $0$ |
| 3 |  | $0$ | $0$ | $0$ |
| 4 |  | $\frac{1}{36}$ | $0$ | $0$ |
| 5 |  | $\frac{1}{36}$ | $\frac{1}{36}$ | $0$ |
| 6 |  | $\frac{1}{36}$ | $\frac{1}{36}$ | $\frac{1}{36}$ |

| $p_{X \mid Y}$ | $\ldots$ | 10 | 11 | 12 |
|:--------------:|:--------:|:--:|:--:|:--:|
| 1 |  | $0$ | $0$ | $0$ |
| 2 |  | $0$ | $0$ | $0$ |
| 3 |  | $0$ | $0$ | $0$ |
| 4 |  | $\frac{1}{3}$ | $0$ | $0$ |
| 5 |  | $\frac{1}{3}$ | $\frac{1}{2}$ | $0$ |
| 6 |  | $\frac{1}{3}$ | $\frac{1}{2}$ | $1$ |

### Spojité náhodné veličiny
**Definice (náhodná veličina)** na $\left(\Omega, \mathcal{F}, P\right)$ je zobrazení $X : \Omega \mapsto \mathbb{R}$, které pro každé $x \in \mathbb{R}$ splňuje 

$$\left\{\omega \in \Omega : X(\omega) \le x\right\} \in \mathcal{F}$$

**(👀):** diskrétní n.v. je náhodná veličina (pro tu platí rovnost, kterou posčítáme).

**Definice (distribuční funkce)** (DNF) n.v. je funkce 

$$F_X(x) = P(X \le x) = P(\left\{\omega \in \Omega : X(\omega) \le x\right\})$$

**(👀):**
- $F_X$ je neklesající
- $\lim_{x \to -\infty} F_X(x) = 0$
- $\lim_{x \to \infty} F_X(x) = 1$
- $F_X$ je zprava spojitá

**Definice (spojitá náhodná veličina):** n.n.v. je spojitá, pokud existuje nezáporná reálná funkce $f_x$ (hustota) t.ž. 

$$F_X(x) = P(X \le x) = \int_{-\infty}^{t} f_X(t)\ dt$$

#### Rozdělení
**Příklad (uniformní rozdělení):** n.v. $X$ má na $\left[a, b\right]$ uniformní rozdělení, pokud má hustotní funkci 

$$f_X(x) = \begin{cases} \frac{1}{b-a} & x \in \left[a, b\right] \\ 0 & \text{jindy} \end{cases}$$

![[Pasted image 20240831073718.png]]

**Příklad (exponenciální rozdělení):** n.v. $X$ má exponenciální rozdělení, pokud má distribuční funkci 

$$F_X(x) = \begin{cases} 0 & x \le 0 \\ 1 - e^{-\lambda x} & x \ge 0\end{cases}$$


![[Pasted image 20240831073729.png]]

**Příklad (normální rozdělení):** n.v. $X$ má standardní normální rozdělení, pokud má hustotní funkci 

$$f_X(x) = \frac{1}{\sqrt{2\pi}} e^{-x^2 / 2}$$

![[Pasted image 20240831073740.png]]

**Definice (kvantilová funkce):** pro distribuční funkci $F$ definujeme kvantilovou funkci $Q : \left[0, 1\right] \mapsto \mathbb{R}$ jako 

$$ Q_X(p) = \min \left\{x \in \mathbb{R} : p \le F(x)\right\} $$

**(👀):** pokud je $F_X$ spojitá, pak $Q_X = F^{-1}_X$

**Definice (střední hodnota s.n.v.)** je definována jako 

$$\mathbb{E}(X) = \int_{-\infty}^{\infty} x f_X(x)\ dx$$

pokud integrál dává smysl.

**Poznámka:** LOTUS, linearita, rozptyl fungují také (přesně tak, jak bychom čekali)

**Definice (kovariance):** pro n.v. $X, Y$ je jejich kovariance definována jako 

$$cov(X, Y) = \mathbb{E}\left(\left(X - \mathbb{E}X\right) (Y - \mathbb{E}Y)\right)$$

**Lemma:**
- $cov(X,  Y) = \mathbb{E}(XY) - \mathbb{E}(X) \mathbb{E}(Y)$
- $X, Y$ nezávislé $\implies cov(X, Y) = 0$

### Nerovnosti
**Věta (Markovova nerovnost):** *nechť náhodná veličina splňuje $X \ge 0$; pak 

$$P(X \ge a) \le \frac{\mathbb{E}(X)}{a}$$

**(👀):** říká, že pravděpodobnost, že $X$ je alespoň $a$ je nejvýše $\mathbb{E} / a$, což intuitivně dává smysl
- pro $a = \mathbb{E}$ může být $X$ střední hodnota nejhůř vždy
- pro $a = \mathbb{E} / 2$ dostáváme $\frac{1}{2}$ – kdyby byla $X$ střední hodnota častěji než $\frac{1}{2}$, tak posčítáním přes všechny hodnoty dostáváme spor, střední hodnota by musela být vyšší

### Limitní věty
**Věta (zákon velkých čísel):** *nechť $X_1, \ldots, X_n$ jsou stejně rozdělené n.n.v. se stř. hodnotou $\mu$ a rozptylem $\sigma^2$. Označme $S_n = \left(X_1 + \ldots + X_n\right) / n$ (tzv. výběrový průměr). Pak platí 

$$\lim_{n \to \infty} S_n = \mu$$

skoro jistě (tj. s pravděpodobností $1$).

Věta říká, že je smyslupné průměrovat n.n.v. (s větším $n$ se přibližuje k $\mu$).

**Věta (centrální limitní věta):** *nechť $X-1, \ldots, X_n$ jsou n.n.v. se střední hodnotou $\mu$ a rozptylem $\sigma^2$. Označme $Y_n = \left(\left(X_1 + \ldots + X_n\right) - n \mu\right) / \left(\sqrt{n} \sigma\right)$. Pak $Y_n \overset{d}{\rightarrow} N(0, 1)$. Neboli pokud $F_n$ je distribuční funkce $Y_n$, tak 

$$\lim_{n \to \infty} F_n(x) = \Phi(x) \quad \forall x \in \mathbb{R}$$

Tedy (vhodně přeškálovaný) součet n.n.v. $X_i$ konverguje ke standardnímu normálnímu rozdělení.

### Tahák
Ke zkoušce byla povolena A4 s libovolnými poznamkami, tady jsou moje (dostupné i v [PDF](/assets/pravdepodobnost-a-statistika-i/tahak.pdf)).

---
![[tahak.pdf]]
---