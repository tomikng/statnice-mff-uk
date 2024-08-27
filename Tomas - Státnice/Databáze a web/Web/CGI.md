---
dg-publish: true
tags:
  - tomas
  - web
  - databaze_a_web
---
### Fungování CGI a CGI-like aplikací

**CGI (Common Gateway Interface)** je standardní protokol, který umožňuje webovému serveru spouštět externí programy (skripty) a generovat dynamický obsah. Když webový server obdrží požadavek na CGI skript, spustí tento skript jako proces na straně serveru a předá mu vstupní data (např. parametry požadavku). Skript zpracuje data a vrátí výstup (např. HTML stránku), který je poté odeslán zpět klientovi.

#### Jak CGI funguje:
1. **Požadavek od klienta**: Klient (např. webový prohlížeč) odešle HTTP požadavek na webový server.
2. **Spuštění CGI skriptu**: Webový server identifikuje požadavek jako CGI a spustí příslušný skript (např. v jazyce Perl, Python, C, nebo PHP).
3. **Zpracování**: Skript zpracuje vstupní data, která mohou zahrnovat environmentální proměnné, data z formulářů, nebo soubory.
4. **Generování výstupu**: Skript vygeneruje výstup (obvykle HTML, ale může to být jakýkoliv jiný obsah) a vrátí ho zpět serveru.
5. **Odeslání odpovědi**: Server vrátí výstup CGI skriptu jako odpověď na původní požadavek klienta.

**CGI-like aplikace** jsou aplikace, které fungují podobně jako CGI, ale používají modernější přístupy k dynamickému generování obsahu. Příkladem jsou FastCGI, SCGI, nebo aplikace postavené na serverových frameworcích (např. PHP, Ruby on Rails, Node.js). Tyto technologie jsou obvykle efektivnější než klasické CGI, protože například umožňují dlouhodobé udržování procesů na serveru (tzv. process pooling), což snižuje režii při spouštění nových procesů.

### Možnosti udržování stavu pro webové aplikace a využití uživatelských relací

Udržování stavu a správa uživatelských relací jsou zásadní pro interaktivní a personalizované webové aplikace. Zde jsou některé z hlavních metod:

1. **Cookies**:
   - Cookies jsou malé datové soubory ukládané v prohlížeči uživatele. Mohou obsahovat informace o relacích, uživatelských preferencích, a další data.
   - **Výhody**: Přetrvávají mezi jednotlivými požadavky a mohou být nastaveny s dobou platnosti.
   - **Nevýhody**: Mohou být omezeny na velikost a jsou citlivé na bezpečnostní rizika, pokud nejsou šifrovány.

2. **Session (Relace)**:
   - Relace umožňují ukládat stav na straně serveru mezi různými požadavky od stejného uživatele. Session ID se obvykle ukládá do cookies nebo URL.
   - **Výhody**: Bezpečnější než uložení stavu v cookies, protože data jsou uložena na serveru.
   - **Nevýhody**: Vyžaduje úložiště na straně serveru (např. soubory, databáze), což může mít vliv na škálovatelnost.

3. **Hidden Fields**:
   - Skryté pole v HTML formuláři může být použito k uložení stavu mezi požadavky.
   - **Výhody**: Jednoduché na implementaci a nevyžaduje cookies.
   - **Nevýhody**: Omezeno na formuláře a viditelné v kódu HTML, což může být riziko z pohledu bezpečnosti.

4. **Local Storage a Session Storage**:
   - Uložení dat na straně klienta v prohlížeči pomocí Web Storage API.
   - **Výhody**: Může být použito k uložení většího množství dat než cookies.
   - **Nevýhody**: Omezeno na moderní prohlížeče a není vhodné pro citlivá data.

