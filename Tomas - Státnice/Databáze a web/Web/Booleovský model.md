---
tags:
  - tomas
  - web
  - databaze_a_web
dg-publish: true
---
> [!TODO] Pridat odkaz na prezentaci

> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek z Vyhledávání na webu 

Booleovské a vektorové modely jsou dva základní přístupy používané v informačním vyhledávání k reprezentaci dokumentů a dotazů. Každý z těchto modelů má své výhody a nevýhody a je vhodný pro různé typy úloh.

#### Booleovský model
Booleovský model je jedním z nejstarších a nejjednodušších modelů používaných pro informační vyhledávání. Tento model považuje dokumenty a dotazy za množiny termínů (slov) a vyhledávání se provádí pomocí logických operátorů jako **AND**, **OR** a **NOT**.

##### Základní koncepty:
- **Dokument** je považován za množinu termínů.
- **Termín** je slovo nebo fráze, která se vyskytuje v dokumentu.
- **Dotaz** je booleovský výraz tvořený termíny a logickými operátory.

##### Matematická reprezentace:
Dokument $d_j$ může být reprezentován jako binární vektor:
$$
\mathbf{d_j} = (t_{1,j}, t_{2,j}, \dots, t_{m,j})
$$
kde $t_{i,j} = 1$ znamená, že termín $t_i$ se vyskytuje v dokumentu $d_j$, a $t_{i,j} = 0$, pokud se nevyskytuje.

Dotaz může být reprezentován jako booleovský výraz, např.:
$$
q = t_1 \text{ AND } t_2 \text{ AND NOT } t_3
$$
V tomto modelu se výsledek dotazu získá aplikací logických operací na binární vektory, které reprezentují termíny.

##### Implementace a optimalizace:
Booleovský model je implementován pomocí invertovaného indexu, což je efektivní datová struktura pro rychlé vyhledávání dokumentů obsahujících specifické termíny. Tento index ukládá seznam dokumentů, ve kterých se každý termín vyskytuje.

**Příklad:**
Pokud máme dotaz:
$$
q = \text{Brutus AND Caesar AND NOT Calpurnia}
$$
a termínové vektory:
- **Brutus**: 110100
- **Caesar**: 110111
- **Calpurnia**: 010000

Pak výsledný vektor bude:
$$
q = 110100 \text{ AND } 110111 \text{ AND NOT } 010000 = 100100
$$
Výsledkem jsou dokumenty, které odpovídají pozicím, kde je hodnota 1, tedy dokumenty **Antony and Cleopatra** a **Hamlet**.

#### Vektorový model
Vektorový model, často nazývaný také **model vektorového prostoru**, byl navržen jako rozšíření Booleovského modelu a zohledňuje váhy termínů, což umožňuje částečné shody a výsledky seřazené podle relevance.

##### Základní koncepty:
- **Dokument** je reprezentován jako vektor v $m$-rozměrném prostoru, kde $m$ je velikost slovníku (počet unikátních termínů).
- **Termín** je reprezentován váhou, která udává jeho důležitost v dokumentu.

##### Matematická reprezentace:
Dokument $d_j$ je reprezentován jako vektor vah:
$$
\mathbf{d_j} = (w_{1,j}, w_{2,j}, \dots, w_{m,j})
$$
kde $w_{i,j}$ je váha termínu $t_i$ v dokumentu $d_j$.

Relevance dokumentu $d_j$ vůči dotazu $q$ se vypočítá jako kosinusová podobnost mezi vektory:
$$
\text{relevance}(d_j, q) = \frac{\mathbf{d_j} \cdot \mathbf{q}}{\|\mathbf{d_j}\| \|\mathbf{q}\|}
$$
kde $\mathbf{q}$ je vektor dotazu a $\|\mathbf{d_j}\|$ a $\|\mathbf{q}\|$ jsou délky (normy) vektorů.

##### Výhody a nevýhody:
Vektorový model umožňuje hodnocení dokumentů podle relevance, což zlepšuje efektivitu vyhledávání. Nicméně, jeho nevýhodou je vyšší výpočetní náročnost ve srovnání s Booleovským modelem, zejména při práci s velkými kolekcemi dokumentů.

### Word2Vec

**Word2Vec** je populární metoda pro vytváření vektorových reprezentací slov v kontinuitním prostoru, což znamená, že slova jsou reprezentována jako vektory v mnohorozměrném prostoru, kde jsou si podobná slova blízko sebe. Tato metoda byla vyvinuta Tomášem Mikolovem a jeho týmem v roce 2013.

#### Základní Principy
Word2Vec používá neuronové sítě k vytvoření distribuovaných reprezentací slov na základě jejich kontextu v textovém korpusu. Existují dva hlavní modely pro trénování Word2Vec: **Continuous Bag of Words (CBOW)** a **Skip-gram**.

1. **Continuous Bag of Words (CBOW)**:
    - Tento model předpovídá cílové slovo na základě kontextu, tedy okolních slov.
    - Například pro větu „Kočka sedí na stromě“ by CBOW model zkoušel předpovědět slovo „sedí“ na základě slov „Kočka“, „na“, a „stromě“.
    - Tento model má vstupní vrstvu, která obsahuje vektory pro kontextová slova, a výstupní vrstvu, která generuje vektor pro cílové slovo.

2. **Skip-gram**:
    - Tento model dělá opak oproti CBOW, předpovídá kontextová slova na základě cílového slova.
    - Pro stejnou větu „Kočka sedí na stromě“ by Skip-gram model zkoušel předpovědět slova „Kočka“, „na“, a „stromě“ na základě slova „sedí“.
    - Skip-gram je obzvlášť vhodný pro trénování na velkých korpusech, protože se zaměřuje na předpověď několika kontextových slov pro každé jednotlivé slovo.

#### Matematická Reprezentace

**CBOW Model:**
- Vstupní vrstva: $x = \{x_1, x_2, \dots, x_c\}$, kde $x_i$ je jednorozměrný vektor pro i-té kontextové slovo.
- Projekční vrstva: $h = W \cdot x$, kde $W$ je váhová matice a $h$ je projekční vektor.
- Výstupní vrstva: $y = softmax(U \cdot h)$, kde $U$ je váhová matice a $y$ je pravděpodobnostní distribuce přes všechna slova ve slovníku.

**Skip-gram Model:**
- Vstupní vrstva: $x = w_t$, kde $w_t$ je vektor pro cílové slovo.
- Projekční vrstva: $h = W \cdot x$, kde $W$ je váhová matice.
- Výstupní vrstva: $y = softmax(U \cdot h)$, kde $U$ je váhová matice a $y$ je sada pravděpodobností pro kontextová slova.

### Aplikace Word2Vec
Word2Vec má široké uplatnění v různých úlohách zpracování přirozeného jazyka (NLP), jako jsou:
- **Vyhledávání informací**: Slova mohou být reprezentována jako vektory, což umožňuje nalezení podobných slov nebo dokumentů na základě vektorových operací.
- **Strojové překládání**: Word2Vec může být použit k mapování slov z jednoho jazyka do druhého na základě jejich vektorových reprezentací.
- **Analýza sentimentu**: Analýza sentimentu textu může být vylepšena díky lepšímu pochopení kontextu pomocí vektorových reprezentací slov.

**Příklad vektorové aritmetiky:**
Jedním ze známých příkladů použití Word2Vec je vektorová aritmetika:
$$ \text{vec("král")} - \text{vec("muž")} + \text{vec("žena")} \approx \text{vec("královna")} $$
Tento příklad ukazuje, jak Word2Vec zachytí vztahy mezi slovy pomocí vektorových operací.

Word2Vec je vysoce efektivní nástroj pro zachycení sémantických informací v textu a nabízí škálovatelné řešení pro mnoho NLP úloh.

Pro více informací a detailní vysvětlení naleznete v prezentaci na slidu 28 přednáška 3.