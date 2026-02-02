# NASA-Exoplanets-Analysis-PowerBI
Analyse interactive des données astrophysiques de la NASA (Exoplanet Archive). Dashboard Power BI explorant les méthodes de découverte, les caractéristiques physiques (masse, rayon) et la classification des mondes lointains (2013-2025). Inclut des mesures DAX avancées.

# 🌌 Exploration des Exoplanètes : Analyse des Données NASA

## 🎯 Aperçu du Projet
Ce projet Power BI propose une immersion analytique dans le catalogue des mondes situés au-delà de notre système solaire. En exploitant les données du **NASA Exoplanet Archive**, ce rapport permet de visualiser l'évolution des découvertes spatiales et de comprendre les caractéristiques physiques des planètes détectées.

**Axes majeurs d'analyse :**
* 🛰️ **Dynamique des découvertes :** Analyse de l'explosion des détections suite aux missions Kepler et TESS.
* 🔭 **Méthodologies :** Comparaison de l'efficacité des méthodes (Transit vs Vitesse Radiale).
* 🌍 **Habitabilité & Classification :** Identification des types de planètes (Super-Terres, Géantes gazeuses) et leur positionnement spatial.

---

## 🖼️ Aperçu du Rapport
![Tableau de Bord Exoplanètes](
)
> *Note : Ce dashboard interactif synthétise les données de plus de 4 700 mondes découverts à ce jour.*

---

## 🧠 Intelligence Analytique & DAX
Pour ce projet, j'ai développé des mesures spécifiques afin de traduire des données astronomiques complexes en indicateurs compréhensibles.

### 1. Classification par Type de Planète
Cette mesure segmente les planètes en fonction de leur rayon par rapport à celui de la Terre ($R_\oplus$).
```dax
Classification Planète = 
SWITCH(TRUE(),
    AVERAGE('Exoplanets'[pl_rade]) < 1.25, "Terrestre",
    AVERAGE('Exoplanets'[pl_rade]) < 2, "Super-Terre",
    AVERAGE('Exoplanets'[pl_rade]) < 6, "Mini-Neptune",
    "Géante Gazeuse"
)

2. Estimation de la Distance Moyenne (Années-Lumière)
Calcul de la profondeur de champ des découvertes par rapport à notre système solaire.

Extrait de code
Distance Moyenne (AL) = 
AVERAGE('Exoplanets'[sy_dist]) * 3.26156
3. Taux de Croissance des Découvertes
Mesure de l'accélération des découvertes d'une année sur l'autre (Year-over-Year).

Extrait de code
Croissance Découvertes = 
VAR AnneePrecedente = CALCULATE(COUNT('Exoplanets'[pl_name]), PREVIOUSYEAR('Calendrier'[Date]))
RETURN
DIVIDE(COUNT('Exoplanets'[pl_name]) - AnneePrecedente, AnneePrecedente, 0)

📂 Structure des Données
Le modèle de données repose sur les paramètres astrophysiques officiels :

pl_name : Nom unique de l'exoplanète.

discoverymethod : Technique de détection utilisée.

pl_rade : Rayon terrestre (unité de comparaison).

sy_dist : Distance du système par rapport à la Terre (parsecs).

disc_year : Année de confirmation de la découverte.

🛠️ Méthodologie & Visualisation
ETL (Power Query) : Nettoyage des coordonnées célestes et gestion des valeurs manquantes sur les masses planétaires.

DataViz : * Scatter Chart pour corréler la température de l'étoile et le rayon de la planète.

Treemap pour visualiser la domination de la mission Kepler dans les méthodes de transit.

Slicers temporels pour isoler les "âges d'or" de l'astronomie moderne.


👤 Contact
Sébastien Henique 📧 heniquea38@gmail.com

🔗 www.linkedin.com/in/sébastien-henique

