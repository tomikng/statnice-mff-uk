---
tags:
  - nail062log
aliases:
  - LI-rezoluce
---
**Lineární důkaz**
- Konečná posloupnost centralních a bočních klauzulí
- $C_{0}\in S$, $C_{i+1}$ je rezolventou $C_{i}$ a $B_{i}$
- $B_{0}\in S$, $B_{i}=C_{j}$ pro nějaké $j<i$
- Lineární zamítnutí je důkaz sporu z S
- $C$ má lineární důkaz z S <=> $S \vdash_{R} C$ - lze z něj vyrobit rezoluční strom indukcí v délce důkazu
	- místo $B_{i}$ napojíme rezoluční strom pro důkaz $C_{j}$ z S, proto je korektní

**LI-důkaz** (linear-input rezoluce)
- lineární důkaz s požadávkem, aby všechny boční klauzule byly z $S$ (axiom z S)
- $S \vdash_{LI}C$
- Přímo dává rezoluční strom (listy jsou axiomy) ve tvaru chlupaté cesty
- LI není úplná! (pouze pro Hornovy formule)

**(T7) Věta o úplnosti LI-rezoluce pro výrokové Hornovy formule.**
- Je-li Hornova formule $T$ splnitelná a $T \cup \{G\}$ nesplnitelná pro cíl $G$, pak $T \cup \{G\} \vdash_{LI} \square$ LI-zamítnutím s cílem $G$