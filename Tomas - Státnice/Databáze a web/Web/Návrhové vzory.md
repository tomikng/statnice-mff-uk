---
tags:
  - tomas
  - databaze_a_web
  - web
dg-publish: true
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT

Návrhové vzory (design patterns) jsou osvědčené postupy pro řešení opakujících se problémů v softwarovém vývoji. Pomáhají organizovat kód, usnadňují jeho údržbu a rozšiřitelnost a přispívají k lepšímu oddělení odpovědností v aplikaci. V případě návrhových vzorů Front Controller, MVC (Model-View-Controller), MVP (Model-View-Presenter) a MVVM (Model-View-ViewModel) se jedná o architektonické vzory, které se používají především při návrhu uživatelského rozhraní a interakce mezi různými částmi aplikace.

### 1. Front Controller
**Front Controller** je návrhový vzor, který se používá především v kontextu webových aplikací. Cílem tohoto vzoru je <mark style="background: #FFF3A3A6;">centralizovat všechny příchozí požadavky do jedné vstupní brány</mark>, která se nazývá Front Controller. Tento vzor umožňuje lepší řízení toku požadavků a odpovědí, centralizované zpracování autentizace, autorizace, správy session, logování a dalších úkolů.

#### Hlavní charakteristiky:
- **Jedno vstupní místo**: Všechny požadavky jsou směrovány do jednoho kontroleru, který rozhoduje, jaký konkrétní kontroler a akci má požadavek obsloužit.
- **Modularita a rozšiřitelnost**: Nové funkcionality lze přidávat bez nutnosti měnit existující kód.
- **Jednodušší údržba**: Díky centralizaci se všechny požadavky zpracovávají na jednom místě, což usnadňuje údržbu a úpravy.
![[Pasted image 20240816192742.png]]

### 2. MVC (Model-View-Controller)
**MVC (Model-View-Controller)** je velmi rozšířený architektonický vzor, který se používá jak pro webové aplikace, tak pro desktopové aplikace. Tento vzor rozděluje aplikaci na tři hlavní komponenty:

- **Model**: Reprezentuje data a obchodní logiku aplikace. Model je zodpovědný za získávání, ukládání a manipulaci s daty, obvykle v databázi.
- **View**: Zobrazuje data z modelu uživateli. View je zodpovědné za prezentaci dat a je často implementováno jako šablona nebo grafické rozhraní.
- **Controller**: Zpracovává uživatelské vstupy a interaguje s modelem pro provedení potřebných operací. Controller pak rozhodne, která view bude použita pro zobrazení dat.

#### Hlavní charakteristiky:
- **Oddělení odpovědností**: Každá komponenta má jasně definovanou roli, což zjednodušuje vývoj a údržbu.
- **Testovatelnost**: Díky oddělení logiky od prezentace je jednodušší psát jednotkové testy.
- **Flexibilita**: Snadná změna uživatelského rozhraní bez zásahů do obchodní logiky.
![[Pasted image 20240816192823.png]]

### 3. MVP (Model-View-Presenter)
**MVP (Model-View-Presenter)** je varianta vzoru MVC, která se často používá v desktopových aplikacích a některých webových aplikacích. Stejně jako u MVC, MVP rozděluje aplikaci na tři části, ale s několika klíčovými rozdíly:

- **Model**: Stále reprezentuje data a obchodní logiku.
- **View**: Zobrazuje data uživateli, ale v případě MVP je ještě více pasivní než ve vzoru MVC. View je často hloupý (dumb) a zcela závisí na presenteru.
- **Presenter**: Obsahuje logiku aplikace a komunikuje s view a modelem. Presenter zpracovává všechny uživatelské interakce a řídí update zobrazení.

#### Hlavní charakteristiky:
- **Lepší testovatelnost**: Vzhledem k tomu, že presenter obsahuje většinu logiky, lze jej snadno testovat bez potřeby view.
- **Oddělení zodpovědností**: View se stává téměř zcela pasivní a stará se jen o vykreslování.

### 4. MVVM (Model-View-ViewModel)
**MVVM (Model-View-ViewModel)** je další architektonický vzor, který se často používá v kontextu aplikací s bohatým uživatelským rozhraním, jako jsou aplikace v technologii WPF, Silverlight, nebo moderní webové frameworky jako Angular nebo React. Tento vzor je evolucí MVP a přidává novou komponentu: ViewModel.

- **Model**: Stejně jako u ostatních vzorů, Model představuje data a logiku aplikace.
- **View**: Stará se o prezentaci dat uživateli.
- **ViewModel**: Reprezentuje abstrakci View a zprostředkovává data z modelu. ViewModel obsahuje všechny metody, které jsou potřeba pro práci s View a může obsahovat logiku specifickou pro prezentaci, která je však nezávislá na konkrétním uživatelském rozhraní.

#### Hlavní charakteristiky:
- **Data binding**: MVVM využívá datové vazby (data binding) k automatickému propojení mezi View a ViewModel. Jakákoli změna v Modelu je automaticky promítnuta do View.
- **Snadná údržba a rozšiřitelnost**: MVVM podporuje čistý a organizovaný kód, což usnadňuje údržbu a rozšiřování aplikace.
- **Testovatelnost**: ViewModel může být snadno testován nezávisle na uživatelském rozhraní, což usnadňuje psaní testů.
![[Pasted image 20240816195348.png]]