
# Stage M1 – Downscaling climatique dans les Pyrénées

Ce dépôt contient les scripts, résultats et documents associés à mon stage de Master 1 réalisé au CEFREM (Université de Perpignan).  
Le projet porte sur le **downscaling climatique dans les Pyrénées**, avec un focus sur les données SAFRAN, les stations in situ et les méthodes d’interpolation/machine learning.

---

##  Organisation du dépôt

- `rapport/`  
  Rapport de stage (PDF).

- `presentation/`  
  Slides de la soutenance (Beamer PDF).

- `scripts/`  
  Notebooks principaux (pipeline de traitement et modélisation) :  
  1. `MNT_Cropping_pyrennees.ipynb` → découpage du MNT (SRTM) sur la zone d’étude  
  2. `Métadonnées_IN_Situ_Stations_pyrénées_final.ipynb` → extraction et préparation des métadonnées des stations in situ  
  3. `stations_statics_pyrenees.ipynb` → filtrage et sélection des stations StatIC dans le polygone des Pyrénées  
  4. `Intégration_des_données_Raster_Stations.ipynb` → croisement des données raster (MNT, pente, orientation) avec les stations  
  5. `Prétraitement_Filtrage_Fully_Consolidated_Stations_Meteo_GIS_Data.ipynb` → nettoyage, consolidation et filtrage des données météo + GIS  
  6. `Données_SAFRAN_pyrénées_filtrées.ipynb` → préparation des données SAFRAN sur la zone d’étude  
  7. `Pipeline_préparation_Données_RandomForestFinal.ipynb` → modélisation (Random Forest, LightGBM) et évaluation des performances  

- `data/`  
  Données légères incluses pour la reproduction :  
  - `polygon_PYRENEES.shp` → polygone de la zone d’étude  
  - `stations_catalogne_pyrenees.csv` → stations disponibles côté Catalogne  
  - `stations_statics_pyrenees.csv` → stations filtrées dans le périmètre pyrénéen  

- `results/`  
  Figures et cartes finales (PNG, PDF).

---

##  Données non incluses

Les données brutes (SAFRAN complet, MODIS, gros CSV/NetCDF) ne sont pas déposées car trop volumineuses.  

  Elles peuvent être téléchargées depuis les serveurs originaux :  
- SAFRAN : [Météo-France AERIS](https://www.aeris-data.fr/)  
- MODIS (COT, CER, CWP) : [NASA EOSDIS Earthdata](https://earthdata.nasa.gov/)  

Les scripts fournis permettent de **recréer les jeux de données** nécessaires à partir de ces sources.

---

##  Reproduction

Environnement utilisé : **Python 3.10**  

Bibliothèques principales :  
- pandas, numpy, scikit-learn  
- geopandas, rasterio, cartopy  
- lightgbm, matplotlib  

---

## Exécution
Tous les notebooks ont été développés et testés sous **Google Colab** (Python 3.10).

---

##  Auteur

**Salma Bensmail – 2025**  
Université de Perpignan – CEFREM
