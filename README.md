# DiDE Ankara — GIS Spatial Analysis Project

**Course:** GMT 352: Geographical Information Systems (Hacettepe University, Geomatics Engineering)  
**Student:** Özge Özdemir (`2220674014`)  
**Coordinate System:** `EPSG:32636` (WGS 84 / UTM Zone 36N)  

---

## About the Project
This project analyzes crowdsourced environmental reports collected in Ankara via `temiz.hacettepe.edu.tr` (668 points) together with **CORINE Land Cover (2018)** data.  

Based on **Vergara-Borge et al. (2025)** (*Systems*, 13(7), 519, https://doi.org/10.3390/systems13070519), counting only the number of uploads creates duplicate posts in central areas. To reward quality and ecological impact, each post is scored using both its event type and the CORINE land cover class it falls into.

---

## Scoring Formula

`Post Score = (Event Type Weight × CORINE Multiplier) + Diversity Bonus`

* **Event Type Weights:**
  * `3.0`: Cigarette butts (`Sigara İzmariti`), Uncontrolled waste (`Kontrolsüz Atık Birikimi`)
  * `2.5`: Recycling bins & full bins (`Geri Dönüşüm Kutusu`, `Dolu Çöp/Geri Dönüşüm Kutusu`)
  * `2.0`: Tree & landscaping (`Ağaç ve Çevre Düzenlemesi`)
  * `1.5`: Trash bins, smoking areas, lighting issues
  * `1.0`: Benches (`Bank`)
* **CORINE Multipliers:**
  * `2.0`: Water bodies & wetlands (Class 4–5)
  * `1.6`: Forest & semi-natural areas (Class 3)
  * `1.3`: Agricultural areas (Class 2)
  * `1.0`: Artificial / urban surfaces (Class 1)
* **Diversity Bonus:** `+5.0` points for contributors who report more than one event type or CORINE class.

---

## Key Results

* **Spatial Join (668 points, 0 NULL):** 614 points in Class 1 (Urban), 41 in Class 3 (Forest/Semi-Natural), and 13 in Class 2 (Agricultural).
* **Spatio-Temporal Expansion (T1 vs T2):**
  * **T1 (Dec 2025):** 183 posts — `2.16 km²` (Beytepe Campus)
  * **T2 (Sep–Oct 2026):** 485 posts — `1,280.40 km²` (Ankara-wide, ~593× expansion)

### Top 10 Leaderboard (Student Contributors)
*(Pilot account `supervisor1` is excluded from student rankings.)*

| Rank | Detective | Posts | CORINE Classes | Total Score |
| :---: | :--- | :---: | :---: | :---: |
| 1 | `FakomakO6` | 51 | 3 | **79.90** |
| 2 | `Kantegenduziasensio` | 44 | 2 | **70.40** |
| 3 | `Uckdnz` | 17 | 2 | **39.90** |
| 4 | `nursenar` | 20 | 1 | **39.00** |
| 5 | `ozi` | 20 | 1 | **34.50** |
| 6 | `Ozeege` | 12 | 2 | **31.40** |
| 7 | `lttlebdybgheart` | 15 | 1 | **30.00** |
| 8 | `charlescarmichael` | 13 | 1 | **29.50** |
| 9 | `patrickjane` | 12
