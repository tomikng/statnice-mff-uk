---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka

1. **Definice a specifikace**:
   - **Textový formát**: Ukládá tabulková data (čísla a text) v prostém textu.
   - **Kódování**: Výchozí je UTF-8 (dříve US-ASCII).
   - **Oddělovač sloupců**: Čárka (`,`), která odděluje jednotlivá pole.
   - **Escape znak**: Dvojité uvozovky (`"`).

2. **Struktura CSV**:
   - **Řádky**: Každý řádek představuje jeden záznam.
   - **Sloupce**: Jednotlivé hodnoty ve sloupci jsou odděleny čárkami.
   - **Záhlaví**: Volitelné, první řádek může obsahovat názvy sloupců.

3. **Použití**:
   - **Import/Export dat**: CSV se široce používá pro výměnu tabulkových dat mezi různými aplikacemi, např. Excel, databázové systémy.
   - **Zpracování**: CSV soubory lze snadno zpracovávat pomocí skriptů a programů.

### **CSV na Webu (CSVW)**
![[Pasted image 20240822140946.png]]
![[Pasted image 20240822141031.png]]
1. **Co je CSV na Webu?**:
   - **Rozšíření CSV**: CSVW je standard W3C, který rozšiřuje možnosti CSV tím, že umožňuje anotaci tabulek pomocí JSON-LD metadat.
   - **Anotace**: Anotace slouží k validaci dat, transformaci do jiných formátů (např. JSON, RDF) a k zajištění konzistence dat.

2. **Model anotovaných tabulkových dat**:
   - **Tabulková skupina**: Může obsahovat více tabulek.
   - **Tabulka**: Základní jednotka obsahující řádky a sloupce.
   - **Řádky, Sloupce, Buňky**: Každý z těchto prvků může mít různé vlastnosti, např. název, datový typ, schéma.

3. **JSON-LD Popisovač (Metadata)**:
   - **@context**: Obsahuje informace o použitém kontextu, např. základní URL a výchozí jazyk.
   - **Tabulka**: Popisuje jednotlivé tabulky v rámci tabulkové skupiny, např. jejich URL, název, klíčová slova.
   - **Schéma tabulky**: Určuje strukturu dat v tabulce, včetně názvů sloupců, datových typů a klíčů.
   ![[Pasted image 20240822141211.png]]
   ![[Pasted image 20240822141232.png]]
   ![[Pasted image 20240822141521.png]]

4. **Transformace do RDF**:
   - **Výchozí konverze**: CSVW umožňuje automatickou transformaci CSV do RDF, což je formát vhodný pro výměnu dat na webu.
   - **Přizpůsobená konverze**: Umožňuje specifikaci vlastních pravidel pro konverzi, např. použití URI šablon.
   [[Priklad CSVW to RDF]]
   ![[Pasted image 20240822142131.png]]

5. **Použití CSV na Webu**:
   - **Validace a anotace**: Umožňuje kontrolu správnosti dat a jejich anotaci pro další zpracování.
   - **Publikace na webu**: Zajišťuje, že data jsou vhodná pro publikaci na webu a jsou kompatibilní s RDF.

### **Nejlepší praktiky pro CSV**

1. **Datové typy**:
   - **Založené na XML Schema**: Např. `xsd:boolean`, `xsd:integer`, `xsd:date`.
   - **Správné formáty**: Důležité je používat správné datové typy, aby byla zajištěna validita a konzistence dat.

2. **Záhlaví**:
   - **Doporučeno**: Vždy by měl být přítomen první řádek obsahující názvy sloupců.

3. **Null hodnoty**:
   - **Vyhněte se řetězcům "null" nebo "NULL"**: Tyto hodnoty by neměly být použity, protože představují skutečné řetězce, nikoliv absenci hodnoty.

4. **Velikosti, množství, ceny**:
   - **Používejte jednotky**: Vždy specifikujte jednotky, např. `kg`, `tne` (tun), aby nedocházelo k nedorozuměním.



