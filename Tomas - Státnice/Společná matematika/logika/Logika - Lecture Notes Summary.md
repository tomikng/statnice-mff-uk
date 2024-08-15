## 1. Syntaxe výrokové a predikátové logiky
### Syntaxe výrokové logiky
Syntaxe výrokové logiky zahrnuje konstrukci výroků pomocí proměnných, logických spojek (¬, ∧, ∨, →, ↔) a závorek pro určení pořadí operací. Formálně korektní formula (dobře formovaná formula, wff) ve výrokové logice musí splňovat specifická pravidla syntaktické struktury.

#### Příklad
Pro výrokovou logiku máme následující dobře formovanou formuli:
$$ (p \rightarrow q) \land (\neg p \lor r) $$
kde $p, q, r$ jsou výrokové proměnné.

Reference: Sekce 2.1, strany 18-20【7†lecture-notes (1) (2) (2).pdf】.

### Syntaxe predikátové logiky
Predikátová logika rozšiřuje výrokovou logiku zavedením kvantifikátorů a predikátů. Syntaxe zahrnuje proměnné, konstanty, funkce, predikáty, logické spojky a kvantifikátory (∀, ∃). Dobře formované formule v predikátové logice musí dodržovat pravidla pro správné použití těchto komponent.

#### Příklad
Formulace výroku "Každý, kdo má dítě, je rodič." ve formální podobě vypadá takto:
$$ (\forall x)((\exists y) \text{child\_of}(y, x) \rightarrow \text{is\_parent}(x)) $$

Reference: Sekce 6.3, strany 74-76【7†lecture-notes (1) (2) (2).pdf】.

## 2. Normální formy výrokových formulí
Normální formy jsou standardizované formáty pro logické formule. Dvě hlavní normální formy ve výrokové logice jsou:

- **Konjunktivní normální forma (CNF)**: Formula je v CNF, pokud je konjunkcí disjunkcí literálů.
- **Disjunktivní normální forma (DNF)**: Formula je v DNF, pokud je disjunkcí konjunkcí literálů.

#### Příklady
- Výrok $p \lor q \lor \neg r$ je v CNF (je to jediná klauzule) a zároveň v DNF (je to disjunkce jednotkových elementárních konjunkcí).
- Výrok $(p \lor q) \land (p \lor \neg q) \land \neg p$ je v CNF.
- Výrok $\neg p \lor (p \land q)$ je v DNF.

Reference: Sekce 2.3, strany 28-29【7†lecture-notes (1) (2) (2).pdf】.

## 3. Prenexní normální formy predikátových logických formulí
Formula v predikátové logice je v prenexní normální formě (PNF), pokud jsou všechny kvantifikátory na začátku formule, následované kvantifikátorově volnou částí. Proces převodu formule do PNF zahrnuje posunutí kvantifikátorů do levých pozic.

#### Příklad
Formula $$(\forall x) (\exists y) (\phi)$$ je v prenexní normální formě, kde $\phi$ je kvantifikátorově volná formula.

Reference: Sekce 8.2.1, strana 116【7†lecture-notes (1) (2) (2).pdf】.

## 4. Sémantika a modely teorií
### Sémantika
Sémantika v logice odkazuje na význam formulí, což je definováno jejich pravdivostními hodnotami v různých modelech. Model je struktura, která přiřazuje hodnoty proměnným a interpretuje symboly ve formuli.

### Modely teorií
Model teorie je struktura, ve které jsou všechny axiomy teorie pravdivé. Pravdivostní hodnota formule v modelu je určena interpretací jejích komponent v rámci modelu.

#### Příklad
Modely jazyka uspořádání $L = \langle \leq \rangle$ zahrnují struktury jako $\langle \mathbb{N}, \leq \rangle$, $\langle \mathbb{Q}, > \rangle$, libovolný orientovaný graf $G = \langle V, E \rangle$, a $\langle P(X), \subseteq \rangle$.

Reference: Sekce 6.4, strany 79-81【7†lecture-notes (1) (2) (2).pdf】.

## 5. Extenze teorií
Extenze teorií zahrnují přidávání nových axiomů nebo definic k existující teorii za účelem rozšíření jejího rozsahu. Extenze musí být konzistentní s původní teorií, aby se zabránilo kontradikcím.

#### Příklad
Teorie grafů je teorie v jazyce $L = \langle E \rangle$ s rovností, splňující axiomy ireflixivity a symetrie: $T_{\text{graph}} = \{¬E(x, x), E(x, y) \rightarrow E(y, x)\}$.

Reference: Sekce 6.7, strana 89-90【7†lecture-notes (1) (2) (2).pdf】.

## 6. Důkaznost a formální důkazní systémy
Důkaznost v logice se vztahuje k schopnosti odvodit formuli z množiny axiomů pomocí pravidel inference. Formální důkazní systémy poskytují rámec pro konstrukci důkazů, což jsou sekvence formulí, kde každá formula je buď axiom nebo je odvozena z předchozích formulí pomocí pravidel inference.

#### Příklad
Hilbertův kalkulus je formální důkazní systém pro predikátovou logiku, kde důkaz je sekvence formulí končící formulí, která má být dokázána.

Reference: Sekce na formální důkazní systémy a Hilbertův kalkulus, strana 111【7†lecture-notes (1) (2) (2).pdf】.

## 7. Věty o kompaktnosti a úplnosti
### Věta o kompaktnosti
Věta o kompaktnosti říká, že pokud je každá konečná podmnožina množiny formulí splnitelná, potom je celá množina splnitelná.

#### Důkaz věty o kompaktnosti
Důkaz této věty je nepřímý. Předpokládáme, že teorie nemá model, což znamená, že je sporná. Pokud je teorie sporná, existuje konečný tablo důkaz sporu. Tento důkaz používá pouze konečný počet axiomů, což znamená, že existuje konečná část teorie, která je také sporná.

Reference: Sekce 4.7, strana 54【7†lecture-notes (1) (2) (2).pdf】.

### Věta o úplnosti
Věta o úplnosti tvrdí, že pokud je formula pravdivá ve všech modelech teorie, potom existuje důkaz této formule z axiomů teorie.

#### Důkaz věty o úplnosti
Pokud selže dokazování, tj. pokud dostaneme bezespornou větev v dokončeném tablu z teorie pro položku $F\phi$, potom tato větev poskytuje protipříklad: model teorie, který se shoduje s položkou $F\phi$ v kořeni tabla, tj. neplatí v něm $\phi$. Takových modelů může být více, ale kanonický model se shoduje se všemi položkami na větvi.

Reference: Sekce 4.5.5, strana 53【7†lecture-notes (1) (2) (2).pdf】.

## 8. Rozhodnutelnost
Rozhodnutelnost v logice odkazuje na to, zda existuje algoritmus, který může určit pravdivost nebo nepravdivost libovolné formule v daném logickém systému. Teorie je rozhodnutelná, pokud takový algoritmus existuje; jinak je nerozhodnutelná.

#### Příklad
Rozhodnutí o splnitelnosti formulí ve výrokové logice je rozhodnutelný problém, známý jako SAT (splnitelnost).

Reference: Sekce na rozhodnutelnost, strany 14-15【7†lecture-notes (1) (2) (2).pdf】.

#### Důkaz nerozhodnutelnosti predikátové logiky
Uvažme formuli $\phi$ tvaru $(\exists x_1) \ldots (\exists x_n) p(x_1, \ldots, x_n) = q(x_1, \ldots, x_n)$, kde $p$ a $q$ jsou polynomy s přirozenými koeficienty. Důkaz využívá faktu, že každé přirozené číslo lze vyjádřit jako součet čtyř čtverců celých čísel.

Reference: Sekce 10.3.2, strana 145【7†lecture-notes (1) (2) (2).pdf】.
