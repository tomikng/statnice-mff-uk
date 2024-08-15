---
tags:
  - databaze
  - databaze_a_web
  - tomas
dg-publish: true
---
## Transakční zpracování
[[Transakce.pdf]]

### ACID
1. **Popis ACID vlastností:**
   - **Atomicity (Atomicita):** Transakce je buď zcela provedena, nebo vůbec neprovedena.
	   - Buď všechno, nebo nic
	   - Pomocí nějakého logovacího systému, dokáže systém číst historii
   - **Consistency (Konzistence):** Transakce převádí databázi z jednoho <mark style="background: #FFF3A3A6;">konzistentního</mark> <mark style="background: #FFF3A3A6;">stavu</mark> do jiného konzistentního stavu.
	   - Dodržuje pravidla
	   - Například, pro bankovní databázi nedovolíme záporný zůstatek
   - **Isolation (Izolace):** Transakce probíhají <mark style="background: #FFF3A3A6;">nezávisle</mark> na sobě.
	   - Stará se o to rozvrh, více v [[#Vlastnosti rozvrhů]]
   - **Durability (Trvalost):** Jakmile je transakce potvrzena, její výsledek je trvalý i při <mark style="background: #FFF3A3A6;">výpadku</mark> systému.
	   - Řešení je například duplikovat na jinou databázi

### Vlastnosti rozvrhů
Stav databáze se mění během vícevlákonové exekuce, <mark style="background: #ADCCFFA6;">kde vlákno dává přístup k datům pro jiné vlákno?
</mark> -> porušuje <mark style="background: #FF5582A6;">Izolaci a konzistenci</mark>

Rozvrh poskytuje :
#### Uspořádatelnost (Serializability):
<mark style="background: #BBFABBA6;">Definice</mark>: Rozvrh je **uspořádatelný**, pokud jeho výsledky odpovídají nějakému serialnímu rozvrhu, tj. transakce lze uspořádat tak, že dávají stejný výsledek jako při jejich sekvenčním vykonávání.
![[Pasted image 20240813094400.png]]
Problém je, jak poznat že jsou dva rozvrhy uspořádané.

**Konflikty**
   - read-read - v pořádku - <mark style="background: #FF5582A6;">nekonfliktní operace</mark>
   - write-read (<mark style="background: #BBFABBA6;">WR</mark>): T1 write, T2 Read - čtení necommitnutých dat
   - read-write (<mark style="background: #BBFABBA6;">RW</mark>): T1 read, T2 write - neopakované čtení
   - write-write (<mark style="background: #BBFABBA6;">WW</mark>): přepsání necommitnutých dat
![[Pasted image 20240813113136.png]]
<mark style="background: #FFB86CA6;">Pozorování</mark>: Nekonfliktní operace nám nemění konečný stav rozvrhu

<mark style="background: #BBFABBA6;">Definice:</mark> Rozvrhy jsou **konfliktně ekvivalentní** pokud sdílí konfliktní pár

<mark style="background: #BBFABBA6;">Definice:</mark> Rozvrh je **konfliktně uspořádaný** pokud je <mark style="background: #FFF3A3A6;">konfliktně ekvivalentní</mark> pro nějaký uspořádaný rozvrh (pro tu stejnou transakci) ^2c2c4a

<mark style="background: #FFB86CA6;">Pozorování:</mark> Pokud rozvrh je **konfliktně uspořádaný**, pak je **uspořádaný**
![[Pasted image 20240813114833.png]] ^11b71c

Potřebujeme ale stále nějak rozpoznat jestli je rozvrh [[#^2c2c4a |konfliktně uspořádané]]

<mark style="background: #BBFABBA6;">Definice</mark>: Precedenční graf, kde
	- vrcholy jsou commitnuté transakce
	- hrany reprezentují RW, WR, WW konflikt na rozvrhu
Platí: <mark style="background: #FFB8EBA6;">Rozvrh je konfliktně uspořádaný, pokud je graf acyklický</mark> 
![[Pasted image 20240813122349.png]]
![[Pasted image 20240813122356.png]]
Teď víme kdy je rozvrh [[#^2c2c4a |konfliktně uspořádané]] a kdy ne. Nyní si zavedeme ještě přísnější pravidlo pro uspořádaní  ^4d4acb

<mark style="background: #BBFABBA6;">Definice:</mark> Rozvrhy jsou **pohledově ekvivalentní** pokud:
	- Transakce $T_i$ čte iniciální hodnotu $X$ v jednom rozvrhu, právě tehdy když, čte původní hodnotu v druhém rozvrhu (<mark style="background: #FFF3A3A6;">Stejné původní čtení</mark>)
	- Operace $O_{i}$ v transakci $T_{i}$ čte hodnotu $X$, vyprodukovanou operací $O_{j}$ v transakci $T_{j}$ právě tehdy když čte stejnou hodnotu v druhém rozvhru (<mark style="background: #FFF3A3A6;">Stejná závislost při psaní</mark>)
	- Transakce $T_i$ píše finální hodnotu $X$ do jednoho rozvrhu právě tehdy když píše původní hodnotu v druhém rozvrhu (<mark style="background: #FFF3A3A6;">Stejné konečné write</mark>)
<mark style="background: #BBFABBA6;">Definice</mark> Rozvrh je **pohledově uspořádaný**, pokud je pohledově ekvivalentní s nějakým uspořádaným rozvrhem
![[Pasted image 20240813133611.png]]
[Návod na pohledově uspořádaný](https://www.youtube.com/watch?v=Vb3G17vaug8)

##### Shrnutí
Nejdřív graf, pak pokud je cyklický, tak pak pohledově uspořádání.

<mark style="background: #FF5582A6;">POZOR</mark>: Při určování  **pohledově uspořádaný**, tak initial read znamená, že nebylo před ní, žádný write. Pokud v tabulce nebudeme mít transakci, to znamená, že u téhle transakce nezáleží na pořadí, tzn. že může mít jaké pořadí chce.

#### Zotavitelnost (Recoverability):
Rozšířili jsme transakční model o operaci, ABORT. Přináší to ale svoje rizika:
![[Pasted image 20240813141014.png]]
Dostáváme zde **nezotavitelný rozvrh**. Tohle nám ničí v [[#ACID]] **<mark style="background: #FF5582A6;">durability</mark>**.

<mark style="background: #BBFABBA6;">Definice:</mark> V **zotavitelném rozvrhu** transakce T je commitnutá po tom, co všechny ostatní transakce, ovlivňující T jsou commitnuté
[Video s příkladem](https://www.youtube.com/watch?v=jEqnfpaEO6M)

Jak zjistit jestli je rozvrh zotavitelný? Pokud je v [[#Strict 2PL]]. Také funguje na převod z nezotavitelného na zotavitelný
### Uzamykací protokoly
Zamykání databázových entit se používá ke kontrole pořadí čtení a zápisů, a také k zabezpečení **konfliktového uspořádání**.

<mark style="background: #BBFABBA6;">Definice:</mark> **Exkluzivní zámek**: ^770127
- $X(A)$, zamyká A, tak, že čtení a zápis je povolen pouze autorovi/vlastníkovi
- Může být povolen pouze jedné transakci
<mark style="background: #BBFABBA6;">Definice</mark>: **Sdílený zámek** ^8e8fb3
- $S(A)$, pouze čte povolené A. 
	- Vlastník zámku může číst a je si jistý, že se A nemůže změnit
- Může být sdíleno napříč transakcemi
<mark style="background: #BBFABBA6;">Definice</mark>: Odemknutí zámku $U(A)$ ^odemknuti-zamku

?? Nejsem si jistý ale $S \subseteq X$
#### Dobře formátované transakce
Transakce je dobře formátovaná, právě tehdy když
- Před čtením z A transakce si požádala a získala aspoň o [[#^8e8fb3 |sdílený zámek]].
- Před zápisem do A transakce si požádala a získala aspoň o [[#^770127|exkluzivní zámek]].
- Nakonci transakce jsou všechny zámky [[#^odemknuti-zamku|odemčené]]. 
<mark style="background: #FFF3A3A6;">Zámky mohou být požádny explicitně, nebo doplněny implicitně rozvrhem.</mark>
![[Pasted image 20240813150245.png]]
#### Dvoufázový uzamykací protokol (2PL)
2PL přidává navíc jedno pravidlo k [[#Dobře formátované transakce|dobře formátovaným transakcím]].
- Transakce si nemůže požádat o zamykání, pokud už **odemknul jeden**.

Dvě fáze: Zamykání a odemykání
![[Pasted image 20240813153251.png]]
##### Vlastnosti 2PL
- Zajistí, že [[#^4d4acb|precedenční graf]] je acyklický $\implies$ [[#^11b71c|konfliktně uspořádaná]] transkace
- Nezajišťuje [[#Zotavitelnost (Recoverability)]]
#### Strict 2PL
Přidává následující pravidla
- Pokud transakce chce číst (zapisovat) na entitě A, tak musí nejdříve získat [[#^8e8fb3|sdílený]] ([[#^770127|exkluzivní]]) zámek.
- Všechny zámky se odemknou na konci transakce
![[Pasted image 20240813154024.png]]
##### Vlastnosti Strict 2PL
Podobně jako v [[#Vlastnosti 2PL]] navíc s
- zajištění [[#Zotavitelnost (Recoverability)]]
![[Pasted image 20240813154618.png]]
### Blokování
1. **Popis:**
   - **Blokování (Deadlock):** Situace, kdy dvě nebo více transakcí čekají na uvolnění zdrojů držených jinými transakcemi, což vede k nekonečnému čekání.
   - **Řešení:** Použití detekce blokování a rollbacku jedné z transakcí.
![[Pasted image 20240813162508.png]]
![[Pasted image 20240813162519.png]]