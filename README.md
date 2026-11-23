# DiDE Ankara - GIS Spatial Analysis (GMT 352)

- **Student:** Özge Özdemir (2220674014)
- **Department:** Hacettepe University, Geomatics Engineering
- **Coordinate System:** EPSG:32636 (WGS 84 / UTM Zone 36N)

## About This Project
In this project, I analyzed 668 environmental reports collected across Ankara from `temiz.hacettepe.edu.tr` together with CORINE Land Cover (2018) data in QGIS.

Following the paper by Vergara-Borge et al. (2025) (*Systems*, 13(7), 519 - https://doi.org/10.3390/systems13070519), only counting the number of posts causes duplicate uploads in the same area. Because of that, I created a point-based scoring system using both event types and CORINE land cover classes.

## Scoring System
Formula: `Post Score = (Event Type Weight x CORINE Multiplier) + Diversity Bonus`

Event Type Weights:
- 3.0: Sigara İzmariti, Kontrolsüz Atık Birikimi
- 2.5: Geri Dönüşüm Kutusu, Dolu Çöp/Geri Dönüşüm Kutusu
- 2.0: Ağaç ve Çevre Düzenlemesi
- 1.5: Çöp Kutusu, Sigara İçme Bölgesi, Aydınlatma Arızası
- 1.0: Bank

CORINE Multipliers:
- 2.0: Water bodies and wetlands (Class 4 and 5)
- 1.6: Forest and semi-natural areas (Class 3)
- 1.3: Agricultural areas (Class 2)
- 1.0: Artificial / urban surfaces (Class 1)

Diversity Bonus:
- +5.0 points if a user reported more than one event type or more than one CORINE class.

## Results
- Spatial Join (668 points): 614 points in Class 1 (Urban), 41 points in Class 3 (Forest/Semi-Natural), and 13 points in Class 2 (Agricultural).
- T1 (Dec 2025): 183 posts, covering 2.16 km² around Beytepe Campus.
- T2 (Sep-Oct 2026): 485 posts, covering 1,280.40 km² across Ankara.

Top 10 Student Leaderboard (excluding `supervisor1` pilot account):
1. FakomakO6 - 79.90 pts (51 posts, 3 CORINE classes)
2. Kantegenduziasensio - 70.40 pts (44 posts, 2 CORINE classes)
3. Uckdnz - 39.90 pts (17 posts, 2 CORINE classes)
4. nursenar - 39.00 pts (20 posts, 1 CORINE class)
5. ozi - 34.50 pts (20 posts, 1 CORINE class)
6. Ozeege - 31.40 pts (12 posts, 2 CORINE classes)
7. lttlebdybgheart - 30.00 pts (15 posts, 1 CORINE class)
8. charlescarmichael - 29.50 pts (13 posts, 1 CORINE class)
9. patrickjane - 29.40 pts (12 posts, 2 CORINE classes)
10. goktugnlc - 28.70 pts (11 posts, 2 CORINE classes)

## Maps

1. Spatio-Temporal Diffusion (T1 vs T2)
[maps/map_15.png]

2. Ecological Risk Density (Heatmap)
[maps/map_2.png]

## Notes
- Used EPSG:32636 because Ankara (~32.8°E) is in UTM Zone 36N.
- Fixed geometry errors in the clipped CORINE layer before Spatial Join.
- Saved the QGIS project (`project/project.qgz`) with relative paths to `../Data/`.

## Data License
Contains data from DiDe - Digital Detectives of Environment (contributors), licensed under the DiDe Data Use License v1.0, downloaded on November 13, 2026.
