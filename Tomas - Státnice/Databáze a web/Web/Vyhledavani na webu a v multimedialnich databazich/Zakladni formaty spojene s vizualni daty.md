---
dg-publish: true
tags:
  - tomas
  - databaze_a_web
  - web
---
### Jak ukládat a sdílet multimediální data?

#### Co je to multimediální kontejner?

Když mluvíme o multimediálním obsahu, jako jsou videa, zvukové soubory nebo obrázky, je důležité vědět, že tyto typy dat jsou často ukládány v tzv. **kontejneru**. Kontejner je jeden soubor, který obsahuje všechny související datové prvky, jako jsou audio, video, titulky a další. Představte si to jako kufr, kde jsou všechny věci (různé typy dat) uloženy na jednom místě. Tento kufr (kontejner) obsahuje nejen data samotná, ale i informace o jejich struktuře, synchronizaci a fragmentaci, což znamená, jak jsou jednotlivé části uspořádány a synchronizovány dohromady.

#### Proč je důležitá komprese?

Pokud bychom všechna data ukládali v nekomprimované podobě, byla by extrémně velká a obtížně přenositelná. Například 1 sekunda nekomprimovaného videa ve formátu 1920x1080 s 30 snímky za sekundu (fps) by mohla zabírat až 186,6 MB! Abychom mohli efektivně ukládat a sdílet taková data, používáme **kompresi**, která data zmenšuje při zachování co nejvyšší kvality. Komprese je proces, při kterém jsou data zmenšována tak, aby zabírala méně místa, ale zároveň zůstala použitelná.

#### Co jsou standardní formáty?

Při ukládání multimediálních dat je také důležité používat **standardní formáty**. Tyto formáty jsou „čitelné pro každého“, což znamená, že je můžete otevřít na různých zařízeních a platformách bez problémů. Příkladem jsou formáty jako **MP4** pro video, **JPEG** pro obrázky nebo **BMP** pro bitmapové obrázky. 

---

### Základní schéma přehrávání kódovaného souboru

Pro přehrávání kódovaného multimediálního souboru potřebujeme několik věcí:

1. **Mediální kontejner** (např. MP4, MKV, AVI, MOV) – toto je soubor, který obsahuje všechny části multimediálního obsahu, včetně videa, zvuku, titulků a dalších informací.
   
2. **Mediální přehrávač** (např. VLC, Windows Media Player, Google Chrome) – software, který umí přečíst obsah kontejneru a přehrát jej.

3. **Codec nástroj** (Coder + Decoder) – software nebo hardware, který dokáže kódovat nebo dekódovat data uvnitř kontejneru. Příkladem jsou AVC nebo AAC kodeky pro video a zvuk.

4. **Audio/video stream pro přehrávání** – toto je výstupní tok dat, který přehrávač přehrává na vašem zařízení.

##### Co je to "Muxing" a "Demuxing"?

- **Muxing** je proces kombinování různých datových proudů (např. video a audio) do jednoho kontejneru.
- **Demuxing** je naopak proces oddělování těchto proudů zpět do jejich původních formátů.

---

### MP4 kontejner – co to je a proč ho používat?

#### Vlastnosti MP4 kontejneru

MP4 kontejner byl poprvé představen organizací **ISO/IEC** v roce 2001. Je to otevřený a rozšiřitelný formát, což znamená, že může být použit na různých platformách a je široce podporován. Tento kontejner podporuje různé typy datových proudů, jako jsou video, zvuk, titulky a metadata (např. informace o autorovi, délce videa, atd.). Navíc MP4 může obsahovat různé kodeky, jako je **H.264**, **H.265** pro video a **AAC** pro zvuk.

MP4 je také známý jako **„life-cycle format“**, protože je vhodný pro různé fáze práce s videem – od nahrávání, přes editaci až po přehrávání a streamování.

#### Jak MP4 kontejner funguje?

MP4 kontejner je složený z několika částí, které jsou hierarchicky uspořádány do tzv. **boxů** nebo **atomů**. Každý box obsahuje určitou informaci, například:

- **ftyp** – informace o formátu a kompatibilitě.
- **mdat** – box obsahující samotná multimediální data (video, audio).
- **moov** – box obsahující metadata o videu, jako je doba trvání, velikost a časové značky.

Box **moov** může obsahovat další boxy, které obsahují podrobnější informace o jednotlivých stopách videa nebo audia.

##### Jak funguje fragmentace v MP4?

Pro streamování videa, například na internetu, se MP4 soubory často dělí na menší fragmenty. Každý fragment obsahuje tzv. **moof** box (metadata o fragmentu) a **mdat** box (data samotná). Tento proces se nazývá **fragmentované MP4 (fMP4)** a je používán v různých streamovacích protokolech, jako je **MPEG DASH** nebo **HLS**.

---

### Základní formáty spojené s vizuálními daty

#### BMP (Bitmap)

- **BMP** je velmi jednoduchý formát pro ukládání obrázků, který ukládá každý pixel jako nezávislé datové body.
- Typický BMP soubor není komprimovaný, což znamená, že je velmi velký ve srovnání s jinými formáty.
- BMP je používán především ve Windows prostředí a je ideální pro uchování obrázků bez ztráty kvality.

#### JPEG (Joint Photographic Experts Group)

- **JPEG** je široce používaný formát pro ukládání fotografií a obrázků, který využívá ztrátovou kompresi.
- JPEG soubory jsou menší než BMP, ale při kompresi dochází ke ztrátě některých detailů.
- Tento formát je ideální pro sdílení obrázků na internetu, kde je velikost souboru důležitá.

#### MP4 (MPEG-4 Part 14)

- **MP4** je formát, který je často používán pro ukládání video a audio souborů.
- MP4 kombinuje video, audio, titulky a další data do jednoho souboru.
- Tento formát je univerzální a je podporován na většině zařízení a softwarových přehrávačů.

---

Tyto poznámky poskytují základní přehled o tom, jak se multimediální data ukládají, komprimují a přehrávají. Pokud chcete jít hlouběji do tématu, můžete se podívat na detaily jednotlivých formátů a postupy, které jsou specifické pro vaše potřeby nebo projekty.
