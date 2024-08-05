---
tags:
  - nail062log
---
## Výroková logika
**Teorie** $T$
- libovolná podmnožina $T \subseteq VF_\mathbb{P}$ výroků v jazyce P
- axiomy - jednotlivé výroky teorie
- konečnou teorii lze nahradit konjunkcí všech axiomů $\varphi_{1} \wedge \varphi_{2} \dots \wedge \varphi_{n}$

### Vlastnosti teorie
**Vlastnosti teorie**
- **sporná** - platí v ní spor, $T \models \bot$ = nemá model = platí všechny výroky (i opačného vyhodnocení)
	- výrok platí v T, když platí v každém modelu T, ty ale nejsou, proto ve sporné T platí každý výrok
	- pokud má alespoň jeden model, nemůže platít $\bot=p \wedge \neg p$, v žádném ohodnocení nedává výstup 1
- bezesporná (**splnitelná**) = má nějaký model
- **kompletní** = nemá nezávislé výroky, jen pravdivé a lživé = má právě jeden model
	- kdyby měla dva různé modely $v \neq v'$, pak dokážeme zkonstruovat z prvního modelu výrok $\bigwedge_{p\in \mathbb{P}}p^{v(p)}$ a ten neplatí v druhém, je nezávislý
	- je-li model pouze jeden, pak každý výrok buď v něm platí nebo ne
- **ekvivalentní** teorie = mají stejné modely, $M_{\mathbb{P}}(T)=M_{\mathbb{P}}(T')$

Důsledek teorie
- každý výrok platný v T, $T \models \varphi$, $$Csq_{\mathbb{P}}(T)=\{\varphi\in VF_\mathbb{P} | T \models \varphi\}$$v jazyce $\mathbb{P}$ lze psát: $$Csq_{\mathbb{P}}(T)=\{\varphi\in VF_\mathbb{P} | M_{\mathbb{P}}(T) \subseteq M_{\mathbb{P}}(\varphi)\}$$
- $T \subseteq Csq_{\mathbb{P}}(T)$ - množina axiomů je podmnožinou důsledků teorie
	- vyplývá z toho, že modely platných výroků jsou nadmnožiny modelů teorie
- $Csq_{\mathbb{P}}(T)=Csq_{\mathbb{P}}(Csq_{\mathbb{P}}(T))$ - důsledky důsledků
	- $M(Csq(T))=M(T)$ - modely důsledků teorie jsou shodné s modely teorie
- $T \subseteq T' \Rightarrow Csq_{\mathbb{P}}(T) \subseteq Csq_{\mathbb{P}}(T')$
	- $T \subseteq T' \Rightarrow M(T) \supseteq M(T')$ - $T'$ má více axiomů, proto má méně modelů
	- $Csq_{\mathbb{P}}(T')=\{\varphi\in VF_\mathbb{P} | M_{\mathbb{P}}(T') \subseteq M_{\mathbb{P}}(T) \subseteq M_{\mathbb{P}}(\varphi)\}$
- $\varphi\in Csq_{\mathbb{P}}(\{\varphi_{1},\dots,\varphi_{n}\}) \Leftrightarrow (\varphi_{1} \wedge \dots \wedge \varphi_{n})\to \varphi \text{ je tautologie}$
	- $\psi \to \varphi$ je tautologie právě když $M(\psi) \subseteq M(\varphi)$ - nemůžeme najít takové ohodnocení, kde platí $\psi$, ale neplatí $\varphi$
	- Modely konjunkce výroků odpovídají modelům výrokům zvlášť $M(\dots \wedge \dots) = M(\dots,\dots)$
	- výrok je důsledkem teorie právě když konjunkce axiomů ho vždy implikuje

## Predikátová logika
**Teorie** $T$
- Množina $L$-formulí, prvky jsou axiomy
- **Model teorie** je L-struktura (model jazyka), ve které platí všechny axiomy, $$M_{L}(T) = \{\mathcal{A}\in M_{L} | \mathcal{A} \models T\}$$
- $\mathcal{A}\models T$ - je modelem teorie $T$ <=> $\mathcal{A} \models \varphi$ - je modelem všech axiomů $\varphi\in T$
- **Otevřená teorie** - všechny axiomy jsou otevřené formule


**[[Elementární ekvivalence]]** $\mathcal{A} \equiv \mathcal{B}$
- Struktury jsou EE, pokud platí tytéž sentence

Platnost v teorii
- $T$ je teorie v jazyce $L$, $\varphi$ je $L$-formule
- $T \models \varphi$ - **pravdivá** v T <=> $\mathcal{A}\models \varphi$ pro všechna $\mathcal{A}\in M(T)$ <=> $M(T) \subseteq M(\varphi)$
- $T \models \neg \varphi$ - **lživá** v T <=> lživá v každém modelu T, $M(T)\cap M(\varphi)=\emptyset$
- **nezávislá** - ani pravdivá, ani lživá
- **kompletní** - bezesporná a každá sentence je pravdivá nebo lživá
	- má právě 1 model až na elementární ekvivalence
- Prokazuje se pomocí nesplnitelnosti:
	- Je-li T teorie a $\varphi$ sentence, pak platí:
	- $T \cup \{\neg \varphi\}$ nemá model <=> $T \models \varphi$
		- $\neg \varphi$ neplatí v žádném modelu T <=> $\varphi$platí v každém modelu T (protože $\varphi$ je sentence)

Důsledky v PL
- všechny pravdivé sentence v T $$Csq_{L}(T) = \{\varphi| \varphi \text{ je sentence a } T \models \varphi\}$$
- $\{\varphi | M(T)\subseteq M(\varphi)\}$ pro sentence $\varphi$
