---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka
Here is the full markdown-formatted text including **WikiText**, **LaTeX**, and **TeX**:

# Plain Text (prostý text)
- **Formát:** Prostý text bez formátování.
- **Přípona souboru:** .txt.
- **Typ média:** `text/plain`.
- **Ukončení řádků:** Způsob ukončení řádků se liší podle OS (CR+LF pro Windows, LF pro Unix a macOS, CR pro starší verze Mac OS).
- **Kódování:** Dříve US-ASCII, dnes se doporučuje UTF-8.

# Formatted Text (formátovaný text)
- **Richtext (RFC 1341):** Základní formátování pomocí značek jako `<bold>` a `<italic>`, omezené možnosti.
- **Enriched Text (RFC 1896):** Rozšířená verze Richtextu s více možnostmi formátování, zaměřená na e-mailovou komunikaci.
- **Rich Text Format (RTF):** Vytvořeno společností Microsoft, umožňuje pokročilé formátování a podporuje různé znakové sady, vhodné pro WYSIWYG editory.

# HTML (HyperText Markup Language)
- **Formát:** HTML je základní formát pro vytváření webových stránek. Umožňuje strukturování obsahu pomocí značek (tags), jako jsou `<h1>` pro nadpisy, `<p>` pro odstavce, `<a>` pro odkazy atd.
- **Přípona souboru:** .html nebo .htm.
- **Typ média:** `text/html`.
- **Kódování:** Moderní HTML stránky používají UTF-8, ale mohou podporovat i jiná kódování.
- **Vlastnosti:**
  - **Hypertextové odkazy:** Možnost propojení různých částí textu či externích zdrojů.
  - **Strukturování:** Umožňuje hierarchii obsahu (nadpisy, odstavce, seznamy).
  - **Vkládání multimédií:** Podporuje integraci obrázků, videí, a dalšího multimediálního obsahu.
- **Použití:** Je základním stavebním kamenem webových stránek, který se často kombinuje s CSS (pro stylování) a JavaScript (pro interaktivitu).

# Markdown
- **Formát:** Markdown je lehký značkovací jazyk, který umožňuje formátování textu pomocí jednoduchých znaků, jako jsou hvězdičky pro tučné písmo nebo křížky pro nadpisy.
- **Přípona souboru:** .md nebo .markdown.
- **Typ média:** `text/markdown`.
- **Vlastnosti:**
  - **Jednoduché formátování:** Umožňuje rychlé a snadné formátování bez nutnosti použití složitých HTML značek.
  - **Převoditelnost:** Markdown lze snadno převést do HTML a dalších formátů.
- **Použití:** Široce využíván pro psaní dokumentace, blogových příspěvků, a také pro tvorbu obsahu na platformách jako GitHub.

# CommonMark
CommonMark je standardizovaná a jednoznačná specifikace syntaxe pro Markdown, která byla vyvinuta jako reakce na roztříštěnost různých implementací původního Markdownu. Zatímco Markdown byl navržen jako snadno čitelný a jednoduše převoditelný do HTML, různé varianty Markdownu se v průběhu let od sebe odlišily, což vedlo k nekompatibilním rozšířením.

## Základní vlastnosti CommonMark zahrnují:
- **Jednoznačná syntaxe:** CommonMark poskytuje standardizovanou a jednoznačnou sadu pravidel pro zápis Markdownu, což umožňuje, aby dokumenty psané v CommonMarku byly interpretovány konzistentně napříč různými nástroji a platformami.
  
- **Podpora kódu:** CommonMark podporuje zvýrazněné bloky kódu, kde lze určit jazyk kódu prostřednictvím tzv. "info stringu". Například, pro blok kódu v Ruby se používá následující syntaxe:
```ruby
def foo(x)
return 3
end
```
  což se následně převádí do HTML s přidaným atributem `class="language-ruby"`.

- **Podpora HTML bloků:** CommonMark umožňuje vkládání HTML bloků přímo do textu, což je užitečné pro pokročilé uživatele, kteří chtějí začlenit vlastní HTML struktury do svých dokumentů.

- **Tvrdé zalomení řádku:** CommonMark podporuje tvrdé zalomení řádku, což znamená, že řádky ukončené dvěma mezerami nebo zpětným lomítkem jsou vygenerovány jako nové řádky v HTML.

- **Široká podpora:** CommonMark je implementován v různých platformách a službách, včetně Discourse, GitHubu, GitLabu, Redditu a Stack Overflow. To zajišťuje, že dokumenty napsané v CommonMarku jsou kompatibilní s mnoha oblíbenými online nástroji a prostředími.

# WikiText
- **Formát:** Wikitext je značkovací jazyk používaný především v prostředí MediaWiki, což je software, který pohání Wikipedii a mnoho dalších Wiki stránek.
- **Vlastnosti:**
  - **Jednoduché formátování:** Umožňuje vytvářet nadpisy, seznamy, odkazy, tabulky a další prvky pomocí jednoduché syntaxe.
  - **Podpora odkazů:** Podporuje vytváření interních a externích odkazů na jiné stránky či části stránky.
- **Příklady syntaxe:**
  - Nadpisy: `== Heading 2 ==`
  - Odkazy: `[[Main Page]]` pro interní odkazy nebo `[http://example.com Example]` pro externí odkazy.

# TeX
- **Vytvořeno:** Donald Knuth, 1978.
- **Účel:** TeX je programovací jazyk a softwarový systém pro typografii, zaměřený na vytváření vysoce kvalitních knih a vědeckých dokumentů, zejména v technických oborech.
- **Přípona souboru:** .tex.
- **Vlastnosti:**
  - **Přesná typografie:** Zajišťuje, že výstup bude stejný na všech počítačích, bez ohledu na operační systém.
  - **Použití:** Široce používán v matematice, fyzice, počítačové vědě a dalších technických oborech.

# LaTeX
- **Vytvořeno:** Leslie Lamport, 1984.
- **Účel:** LaTeX je sada maker pro TeX, která zjednodušuje psaní dokumentů, umožňuje autorům soustředit se na obsah a ne na formátování.
- **Přípona souboru:** .tex.
- **Vlastnosti:**
  - **Podpora pro komplexní dokumenty:** Umožňuje vytvářet velké dokumenty s částmi, referencemi, tabulkami a obrázky.
  - **Podpora pro matematiku:** Umožňuje psaní složitých matematických vzorců.
  - **Výstup:** Výsledkem je obvykle PDF soubor.
  - **Použití:** Vědecké články, technické zprávy, knihy a prezentace.
  - **Ukázkový kód:**
```latex
\documentclass{article}
\usepackage{amsmath}
\begin{document}
Hello world!
\[
	\binom{n}{k} = \frac{n!}{k!(n-k)!}
\]
\end{document}
```
