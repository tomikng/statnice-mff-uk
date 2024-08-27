---
dg-publish: true
tags:
  - tomas
  - databaze_a_web
  - web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek

### Základní principy komprese videa

#### Co je komprese videa?

Komprese videa je proces, při kterém jsou video data zmenšována, aby zabírala méně místa při zachování co nejvyšší možné kvality. Komprese je důležitá, protože nekomprimovaná videa mohou být velmi velká, což komplikuje jejich ukládání, sdílení a přehrávání na různých zařízeních. Klíčem ke kompresi je nalezení správné rovnováhy mezi kvalitou a velikostí souboru.

---

### Jak funguje komprese videa?

Komprese videa zahrnuje několik kroků:

1. **Původní data**: Původní video data mohou být například seznamem obrazových souborů (např. BMP) se specifikovanou snímkovou frekvencí (fps) jako 29.97, 30, 60 fps atd.

2. **Coder (Kodér)**: Při kompresi videa se používá kodér, který komprimuje jednotlivé snímky (frames) a ukládá je do menšího formátu.

3. **Decoder (Dekodér)**: Dekodér je používán při přehrávání videa, aby se zkomprimovaná data dekomprimovala zpět do původní podoby nebo co nejblíže původní kvalitě.

Matematicky je možné popsat proces takto:

$\text{frame} \rightarrow \text{Coder} \rightarrow \text{Decoder} \rightarrow \text{frame}'$

Zde se zkoumá, zda výstupní rámec (frame') po dekódování je co nejbližší původnímu rámci.

---

### Populární formáty komprese videa

Existuje několik formátů komprese videa, které se staly standardem v průběhu let:

- **H.262/MPEG-2 (1994)**: Používán pro DVD a DVB-T.
- **H.264/AVC (2003)**: Používán pro HDTV, Blu-ray a YouTube. Je asi o 50% efektivnější než MPEG-2.
- **H.265/HEVC (2013)**: Používán pro 8K video, je o 50-60% efektivnější než AVC.
- **H.266/VVC (2020)**: O 40% efektivnější než HEVC.

Tyto formáty se vyvíjely s cílem poskytovat lepší kvalitu videa při nižší bitové rychlosti.

---

### Co znamená „lepší“ komprese?

„Lepší“ komprese znamená, že pro stejnou kvalitu obrazu (měřeno například pomocí **Mean Opinion Score - MOS**) potřebujeme nižší bitovou rychlost. To znamená, že video zabírá méně místa na disku při zachování stejné kvality. Grafy na obrázku ukazují, že pro různé formáty, jako je **HEVC** a **H.264**, potřebujeme různou bitovou rychlost pro dosažení stejné kvality.

---

### Proč komprese funguje?

Existuje několik důvodů, proč komprese videa funguje efektivně:

1. **Lidské vidění může být „oklamáno“**: Lidské oko není schopno rozlišit všechny detaily v obraze, což umožňuje ztrátovou kompresi. Techniky jako chroma subsampling a kvantizace v doméně frekvencí (přístup podobný JPEG) mohou výrazně snížit velikost dat bez výrazné ztráty kvality.

2. **Prostorová a časová redundance**: Video obsahuje mnoho podobných snímků nebo oblastí v rámci jednoho snímku. Tyto podobnosti mohou být použity k redukci datového objemu. Například, pokud je v několika snímcích stejná obloha, můžeme tuto informaci uložit jednou a následně ji opakovaně použít.

3. **Statistická redundance**: V rámci videa existují i další statistické vzory, které mohou být využity k efektivnějšímu kódování.

---

### Komprese videa pomocí jednotek a bloků

Video je při kompresi rozděleno na menší jednotky, z nichž každá se zpracovává samostatně:

- **Makrobloky**: V H.264 se používají makrobloky o velikosti 16x16 pixelů. 
- **Kódovací jednotky (Coding Units - CU)**: V H.265 se používají kódovací jednotky, které mohou být děleny do menších částí (např. 4x4, 8x8, 16x16, 32x32 pixelů).

Tyto jednotky mají různé predikční módy (intra-frame a inter-frame predikce), které se používají k předpovědi hodnot pro každý blok. Tím se sníží množství informací potřebných pro kódování, což vede k lepší kompresi.

---

### Inter-frame a Intra-frame komprese

- **Intra-frame komprese**: Každý snímek je komprimován nezávisle na ostatních. Tento přístup je podobný JPEG kompresi, kde se každý snímek zpracovává jako samostatný obraz.
  
- **Inter-frame komprese**: Komprese využívá podobnosti mezi snímky, což umožňuje snížit množství dat potřebných k uložení videa. Používá se kódování typu P a B snímků, které obsahují informace o pohybu mezi snímky (motion compensation).

---

### Shrnutí

Komprese videa je komplexní proces, který umožňuje efektivní ukládání a přenos video dat. Hlavním cílem komprese je snížit velikost souboru při zachování kvality obrazu, a to prostřednictvím využití lidského vnímání, prostorové a časové redundance a efektivního kódování. S rozvojem nových standardů, jako je H.266, se efektivita komprese stále zlepšuje, což umožňuje lepší kvalitu obrazu při menších velikostech souborů.

Tímto způsobem bychom měli být schopni plně pochopit základní principy komprese videa a proč je tak důležitá pro moderní digitální média.