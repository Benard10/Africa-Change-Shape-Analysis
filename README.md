# Correct the Map: Measuring Africa's Distortion in World Map Projections

A reproducible geospatial analysis of how WGS 84, Web Mercator, and Equal Earth change the visual relationship between Africa and other regions. The project combines maps, area measurements, true-scale overlays, and the 2026 UN vote on the **Correct the Map** resolution.

> Africa is not reduced by Mercator. High-latitude regions are enlarged much more strongly, making Africa look too small by comparison.

## Key findings

| Region | Equal-area estimate | Area measured on a Web Mercator map | Mercator enlargement |
|---|---:|---:|---:|
| Africa | 29.95 million km² | 33.57 million km² | 1.12× |
| Greenland | 2.21 million km² | 36.29 million km² | 16.44× |
| United States (all parts) | 9.51 million km² | 21.86 million km² | 2.30× |

- Africa is approximately **13.6 times the area of Greenland**.
- Africa is approximately **3.8 times the area of the contiguous United States** in this generalized dataset.
- When area is measured directly on the Web Mercator map, Africa appears only about **0.9 times as large as Greenland**.
- `EPSG:4326` is a geographic coordinate system, not an equal-area projection; its familiar rectangular GIS display also distorts size and shape.
- Equal Earth (`EPSG:8857`) preserves relative area and is better suited to global comparisons of magnitude.

## Visual results

### One dataset, three world views

![Comparison of WGS 84, Web Mercator, and Equal Earth](figures/01_projection_comparison.png)

### Area-statistics summary

![Table comparing equal-area estimates with areas measured on Web Mercator](figures/02_area_statistics.png)

### Mercator area enlargement by latitude

![Chart showing Mercator area enlargement by latitude](figures/03_mercator_area_distortion.png)

### True-scale outlines over Africa

The outlines are moved over Africa but never resized. Both panels use the same equal-area map projection.

![True-scale Greenland and contiguous United States outlines over Africa](figures/04_true_scale_overlays.png)

### UN General Assembly vote

![UN General Assembly vote on the Correct the Map resolution](figures/05_un_vote.png)

The General Assembly adopted `A/80/L.104` as **resolution `A/RES/80/307`** on 4 September 2026 by **164 votes in favour, 1 against, and 6 abstentions**. The United States cast the only vote against. Estonia, Georgia, Lithuania, the Republic of Moldova, Serbia, and Ukraine abstained.

The screenshot headed “Decade of culture for sustainable development” belongs to a separate vote held during the same meeting:

| Subject | Draft | Resolution | Vote |
|---|---|---|---:|
| Correct the Map | `A/80/L.104` | `A/RES/80/307` | 164–1–6 |
| Decade of Culture for Sustainable Development | `A/80/L.102` | `A/RES/80/308` | 174–1–0 |

## Why it matters

- **African Union:** shows broad international support for the AU's call to represent Africa fairly and update school curricula.
- **Schools and publishers:** encourages equal-area world maps and lessons showing that every flat map has limits.
- **UN and public bodies:** gives them a clear reason to use fairer world maps in reports, statistics, and learning materials.
- **Technology and media:** encourages equal-area options for world views while keeping Mercator for navigation and detailed local maps.
- **Mapmakers and analysts:** reminds them to use an equal-area projection when measuring or comparing land area.

The resolution is a recommendation, not a law. It does not ban Mercator, force anyone to use one map, or change any country's borders.

## Reproduce the analysis

Open [`Africa_map_distortion_analysis.ipynb`](Africa_map_distortion_analysis.ipynb) and run all cells from top to bottom.

```bash
pip install geopandas shapely pyproj matplotlib pandas
```

The first run downloads Natural Earth 1:110m boundaries to `data/`; later runs use the cached file.

## Method and limits

- `EPSG:6933` supplies equal-area measurements.
- `EPSG:3857` supplies the areas measured on the Web Mercator map.
- Overlay geometries are translated without scaling or rotation.
- Natural Earth 1:110m boundaries are generalized, so the results are explanatory estimates rather than official statistics.
- No flat map preserves area, shape, direction, and distance everywhere. Projection choice must follow purpose.

## Sources

- [African Union Assembly Decision 959 (XXXIX)](https://au.int/sites/default/files/decisions/46188-Assembly_Decisions_E.pdf)
- [African Union communiqué, 4 September 2026](https://www.au.int/en/pressreleases/20260904/communique-auc-chairperson-adoption-correct-map-resolution)
- [UN General Assembly meeting coverage and explanations of vote](https://press.un.org/en/2026/ga12779.doc.html)
- [Official agenda for the 114th plenary meeting](https://igov.un.org/ga/plenary/80/meetings?document=A%2F80%2FL.104)
- [UN draft resolution A/80/L.104](https://docs.un.org/A/80/L.104)
- [Natural Earth cultural vectors](https://www.naturalearthdata.com/downloads/110m-cultural-vectors/)
- [Equal Earth, EPSG:8857](https://epsg.io/8857)

## Social version

See [`LINKEDIN.md`](LINKEDIN.md) for a concise, paste-ready post and suggested carousel order.
