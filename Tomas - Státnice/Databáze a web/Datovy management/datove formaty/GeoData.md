---
dg-publish: true
tags:
  - tomas
  - datovy_management
  - databaze_a_web
---
> [!NOTE] ChatGPT
> Vygenerováno pomocí ChatGPT na základě přednášek od Klimka
### Souřadnicový referenční systém (SRS) v kontextu prostorových dat

**Souřadnicový referenční systém (SRS)** je systém, který umožňuje definovat polohu bodů v prostoru pomocí souřadnic. Tento systém zahrnuje referenční elipsoid a datum, což jsou základní komponenty pro přesné určení polohy na povrchu Země.

- **Referenční elipsoid:** matematický model Země, který je používán jako základ pro geodetické výpočty.
- **Datum:** definice pozice elipsoidu vzhledem k Zemskému středu a určení dalších parametrů jako je orientace os.

Nejčastěji používané souřadnicové referenční systémy zahrnují:
- **WGS-84:** Globální systém používaný např. v GPS.
- **S-JTSK:** Systém používaný v České republice.
- **ETRS-89:** Evropský terestrický referenční systém.

Příklad:
Pokud máme bod s následujícími souřadnicemi v systému WGS-84: E 14° 42' 23'', N 49° 52' 12'', tyto souřadnice jednoznačně určí polohu tohoto bodu na Zemi.

### Reprezentace prostorových dat v různých formátech

Prostorová data mohou být reprezentována v různých formátech, které umožňují zpracování, výměnu a vizualizaci těchto dat. Níže jsou uvedeny čtyři základní formáty:

#### 1. **Well-Known Text (WKT)**
WKT je textový formát definovaný konsorciem OGC (Open Geospatial Consortium), který slouží k reprezentaci geometrických objektů jako jsou body, linie a polygony.

**Příklad WKT:**
```wkt
POINT (14.42 49.52)
```
Tento zápis reprezentuje bod se souřadnicemi (14.42, 49.52).

#### 2. **Geography Markup Language (GML)**
GML je XML založený formát pro kódování geografických dat, který je také definován OGC. GML podporuje různé typy geometrie a CRS.

**Příklad GML:**
```xml
<gml:Point srsName="urn:ogc:def:crs:EPSG::5514">
  <gml:pos>14.42 49.52</gml:pos>
</gml:Point>
```
Tento příklad ukazuje bod v CRS s EPSG kódem 5514.

#### 3. **GeoJSON**
GeoJSON je formát založený na JSON, který je určen pro reprezentaci jednoduchých geometrických objektů, jako jsou body, linie a polygony. Podporuje pouze CRS WGS-84.

**Příklad GeoJSON:**
```json
{
  "type": "Point",
  "coordinates": [14.42, 49.52]
}
```
Tento JSON zápis reprezentuje bod se souřadnicemi (14.42, 49.52) ve WGS-84.

#### 4. **GeoSPARQL**
GeoSPARQL je standard pro práci s prostorovými daty v rámci RDF grafů, který podporuje různé operace nad geografickými daty. Reprezentace geometrie může být v GML nebo WKT.

**Příklad GeoSPARQL:**
```sparql
PREFIX geo: <http://www.opengis.net/ont/geosparql#>
INSERT DATA {
  <http://example.org/feature/point1> geo:hasGeometry [
    a geo:Point ;
    geo:asWKT "POINT(14.42 49.52)"^^geo:wktLiteral ;
  ] .
}
```
Tento příklad vkládá bod do RDF grafu jako WKT reprezentaci.