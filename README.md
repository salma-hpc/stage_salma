# Downscaling Climatique par Machine Learning dans les Pyrénées

**Auteur :** Salma Bensmail  
**Cadre :** Stage de Master 1 - CEFREM (Université de Perpignan), 2025

## Contexte et Objectif

Ce projet vise à améliorer la résolution spatiale des données climatiques en zone de montagne complexe. Il compare les données de réanalyse standard (SAFRAN, maille de 8km) avec un modèle de downscaling basé sur le Machine Learning (LightGBM), entraîné sur des données de stations in situ et des variables topographiques.

## Résultats de la Modélisation

Le modèle de downscaling (LightGBM) corrige efficacement les biais liés à l'altitude et à la topographie locale. 

**Validation croisée sur 65 stations :**

| Métrique | Modèle LightGBM (Notre approche) | Données SAFRAN Brutes (Référence) | Gain observé |
| :--- | :---: | :---: | :--- |
| **R² (Précision)** | 0.89 | -0.23 | Excellente corrélation locale |
| **MAE (Erreur Moyenne)** | 1.33°C | 4.21°C | Erreur divisée par 3 |
| **RMSE (Erreur Quadratique)** | 1.69°C | 5.55°C | Réduction massive des écarts |

*(Optionnel : Si tu as une image dans ton dossier results, décommente la ligne ci-dessous)*
## Structure du Code et Reproductibilité

L'ensemble des traitements a été développé sous **Python 3.10** (Google Colab).  
*Stack technique : pandas, numpy, scikit-learn, geopandas, rasterio, lightgbm.*

### 1. Préparation des données et modélisation (`scripts/`)
L'exécution doit respecter l'ordre du pipeline suivant :

1. [MNT_Cropping_pyrennees.ipynb](scripts/MNT_Cropping_pyrennees.ipynb) : Découpage du MNT (SRTM) sur la zone d'étude.
2. [Métadonnées_IN_Situ_Stations_pyrénées_final.ipynb](scripts/Métadonnées_IN_Situ_Stations_pyrénées_final.ipynb) : Extraction des métadonnées des stations.
3. [stations_statics_pyrenees.ipynb](scripts/stations_statics_pyrenees.ipynb) : Filtrage spatial des stations StatiC.
4. [Intégration_des_données_Raster_Stations.ipynb](scripts/Intégration_des_données_Raster_Stations.ipynb) : Croisement des données raster (MNT, pente, orientation) avec les stations.
5. [Prétraitement_Filtrage_Fully_Consolidated.ipynb](scripts/Prétraitement_Filtrage_Fully_Consolidated_Stations_Meteo_GIS_Data.ipynb) : Nettoyage et consolidation.
6. [Données_SAFRAN_pyrénées_filtrées.ipynb](scripts/Données_SAFRAN_pyrénées_filtrées.ipynb) : Préparation des données SAFRAN.
7. [Pipeline_préparation_Données_RandomForestFinal.ipynb](scripts/Pipeline_préparation_Données_RandomForestFinal.ipynb) : Modélisation (Random Forest, LightGBM) et évaluation.

### 2. Données et Ressources (`data/` et `results/`)
Seules les données légères (fichiers `.csv` et `.shp`) nécessaires à l'architecture spatiale sont incluses dans ce dépôt.

**Notes sur les données volumineuses :** Les jeux de données bruts (SAFRAN complet, MODIS) sont trop volumineux pour être hébergés sur GitHub. Les scripts fournis permettent de recréer les jeux de données d'entraînement à partir de ces sources officielles :
* SAFRAN : [Météo-France AERIS](https://www.aeris-data.fr/)
* MODIS (COT, CER, CWP) : [NASA EOSDIS Earthdata](https://earthdata.nasa.gov/)

## Documentation

* [Slides de la soutenance (PDF)](presentation/Slides_de_la_soutenance.pdf)

**Salma Bensmail – 2025**  
Université de Perpignan – CEFREM


