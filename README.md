# Digital Detectives of Environment (DiDE) — Ankara Spatial Analysis

**Course:** GMT 352: Geographical Information Systems (Hacettepe University, Department of Geomatics Engineering)  
**Student:** Özge Özdemir (`2220674014`)  
**Study Area:** Ankara, Türkiye (`EPSG:32636` — WGS 84 / UTM Zone 36N)  
**Data Sources:** `temiz.hacettepe.edu.tr` (DiDE Open Data, 668 reports) & CORINE Land Cover 2018  

---

## 1. Project Overview & Theoretical Rationale

This project implements a **Spatial Multi-Criteria Ecological Scoring Model** and **Spatio-Temporal Diffusion Analysis** on crowdsourced environmental observations collected across Ankara between December 2025 and October 2026.

The methodology is grounded in:
> Vergara-Borge, F., López-de-Ipiña, D., Emaldi, M., Olivares-Rodríguez, C., Khan, Z., & Soomro, K. (2025). *Gamifying Engagement in Spatial Crowdsourcing: An Exploratory Mixed-Methods Study on Gamification Impact Among University Students*. **Systems**, 13(7), 519. https://doi.org/10.3390/systems13070519

Vergara-Borge et al. (2025) demonstrate that rewarding contributors solely by raw submission volume triggers an **"engagement–quality spiral" (quantity-over-quality)** and **spatial bias**, where participants repeatedly upload duplicate reports in convenient central locations (confirmed in our dataset by repeated uploads at Beytepe Campus). To counter this, our scoring scheme weights each post by **ecological impact / circularity potential** and **CORINE Land Cover sensitivity**, supplemented by a **diversity bonus**.

---

## 2. Point-Based Ecological Scoring Scheme

Each report ($P_i$) is graded using the following formula:

$$\text{Post Score}_i = \left( w_{\text{type}} \times w_{\text{Corine}} \right) + \text{Bonus}_{\text{diversity}}$$

### A. Event Type Weight ($w_{\text{type}}$)
| Category | Weight ($w_{\text{type}}$) | Rationale |
| :--- | :---: | :--- |
| `Sigara İzmariti`, `Kontrolsüz Atık Birikimi` | **3.0** | High ecotoxicity (microplastics, heavy metals) & acute environmental hazard |
| `Dolu Çöp/Geri Dönüşüm Kutusu`, `Geri Dönüşüm Kutusu` | **2.5** | Circular economy support (SDG 12) & overflow prevention |
| `Ağaç ve Çevre Düzenlemesi` | **2.0** | Urban green infrastructure & ecological maintenance |
| `Çöp Kutusu`, `Sigara İçme Bölgesi`, `Aydınlatma Arızası` | **1.5** | General urban environmental infrastructure |
| `Bank` | **1.0** | Baseline urban furniture |

### B. CORINE LU/LC Sensitivity Multiplier ($w_{\text{Corine}}$)
| CORINE Level-1 Class | Multiplier ($w_{\text{Corine}}$) | Rationale |
| :--- | :---: | :--- |
| **Class 4 & 5** (Wetlands & Water Bodies) | **2.0** | Direct threat to aquatic ecosystems and water basins |
| **Class 3** (Forest & Semi-Natural Areas) | **1.6** | Biodiversity sensitivity and fire/habitat risk |
| **Class 2** (Agricultural Areas) | **1.3** | Soil contamination and food-chain risk |
| **Class 1** (Artificial / Urban Surfaces) | **1.0** | Baseline urban areas with regular municipal service |

### C. Diversity Bonus ($\text{Bonus}_{\text{diversity}}$)
Contributors who report across **more than one event type** or **more than one CORINE class** receive a **+5.0** detective bonus to reward spatial and thematic exploration.

---

## 3. Key Analytical Findings

### CORINE LU/LC Spatial Join (`n = 668`, 0 NULLs)
* **Class 1 (Artificial Surfaces):** 614 posts (91.9%)
* **Class 3 (Forest & Semi-Natural Areas):** 41 posts (6.1%)
* **Class 2 (Agricultural Areas):** 13 posts (1.9%)
* **Post Score Distribution:** Min = `1.00`, Mean = `1.88`, Max = `4.80`

### Spatio-Temporal Diffusion ($T_1$ vs. $T_2$)
* **$T_1$ (Dec 2025):** 183 posts — Convex Hull Area = **2.16 km²** (`2,157,841 m²`), concentrated around Beytepe Campus.
* **$T_2$ (Sep–Oct 2026):** 485 posts — Convex Hull Area = **1,280.40 km²** (`1,280,399,886 m²`), expanding across Çankaya, Etimesgut, Sincan, and Polatlı (**~593× spatial expansion**).

---

## 4. Sustainability Leaderboard (Top 10 Contributors)

*(Note: Pilot/admin account `supervisor1` [ID 55, 219 posts] is excluded from the student competition ranking; only the Top 10 contributors are listed for privacy.)*

| Rank | Detective | Posts | Event Types | CORINE Classes | Base Score | Diversity Bonus | Total Score |
| :---: | :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| 🥇 1 | `FakomakO6` | 51 | 2 | 3 | 74.90 | +5.0 | **79.90** |
| 🥈 2 | `Kantegenduziasensio` | 44 | 5 | 2 | 65.40 | +5.0 | **70.40** |
| 🥉 3 | `Uckdnz` | 17 | 2 | 2 | 34.90 | +5.0 | **39.90** |
| 4 | `nursenar` | 20 | 5 | 1 | 34.00 | +5.0 | **39.00** |
| 5 | `ozi` | 20 | 2 | 1 | 29.50 | +5.0 | **34.50** |
| 6 | `Ozeege` | 12 | 5 | 2 | 26.40 | +5.0 | **31.40** |
| 7 | `lttlebdybgheart` | 15 | 5 | 1 | 25.00 | +5.0 | **30.00** |
| 8 | `charlescarmichael` | 13 | 5 | 1 | 24.50 | +5.0 | **29.50** |
| 9 | `patrickjane` | 12 | 7 | 2 | 24.40 | +5.0 | **29.40** |
| 10 | `goktugnlc` | 11 | 5 | 2 | 23.70 | +5.0 | **28.70** |

*Notice how the eco-weighted model rewards spatial diversity: `Uckdnz` (17 posts across 2 CORINE classes) outranks 20-post contributors who stayed within a single urban class.*

---

## 5. Maps & Visual Outputs

1. **Map 1 — Spatio-Temporal Diffusion (`maps/Harita_1_Yayilim.png`):** Compares $T_1$ and $T_2$ Convex Hull footprints over CORINE 2018 land cover classes.
2. **Map 2 — Ecological Risk Density (`maps/Harita_2_Risk_Heatmap.png`):** Kernel Density Estimation (`Quartic`, radius = 2,000 m, weighted by `post_score`, clamped `0–80` to reveal secondary urban hotspots beyond Beytepe Campus).

---

## 6. Technical & Methodological Notes

* **CRS Selection (`EPSG:32636`):** Ankara (~32.8°E) falls in UTM Zone 36N (central meridian 33°E), rather than Zone 37N (36°E–42°E). All metric area and KDE calculations were performed in `EPSG:32636` to avoid angular distortion.
* **Topology Repair:** The raw `corine2018.shp` layer contained minor self-intersections (`TopologyException`) after extent clipping; `Fix geometries` in QGIS was applied prior to Spatial Join to ensure 100% point matching (668/668).
* **Scale Consideration:** CORINE vector data uses a 25 ha Minimum Mapping Unit (MMU); future work can cross-validate micro-scale urban green patches against the 10 m `CLCplus` raster.
* **Portability:** The QGIS project (`project/project.qgz`) is configured with **Relative Paths** pointing to `../Data/`.

---

## 7. Repository Structure

```text
D-DE_GIS_GMT327/
├── project/
│   └── project.qgz                  # Portable QGIS project (Relative Paths)
├── Data/                            # Clipped & projected GeoPackages + KDE Raster
├── maps/                            # 300 DPI Cartographic Outputs (Map 1 & Map 2)
├── index.html                       # Interactive Detective Card & Top 10 Dashboard
└── README.md
