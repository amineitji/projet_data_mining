# projet_data_mining
Amine ITJI &amp; Youssef BOUAMAMA


```markdown
# Projet de Clustering de Joueurs de Football

## Description du Projet

Ce projet applique des techniques de **clustering non supervisé** pour analyser et regrouper des joueurs de football professionnels évoluant dans les cinq grands championnats européens (Premier League, La Liga, Serie A, Bundesliga, Ligue 1). L'objectif est de développer un système permettant d'identifier automatiquement des joueurs aux profils statistiques similaires, facilitant ainsi les décisions de recrutement et de gestion d'effectif.

## Problématique

Dans le football moderne, les clubs font face à plusieurs défis stratégiques :

- **Remplacement de joueurs blessés** : Comment identifier rapidement un remplaçant avec un profil similaire ?
- **Recrutement data-driven** : Comment quantifier la similarité entre joueurs pour optimiser les transferts ?
- **Détection de talents** : Comment identifier des jeunes joueurs (< 23 ans) ayant des caractéristiques de joueurs établis ou élites ?
- **Analyse tactique** : Quels sont les profils complémentaires pour construire un effectif équilibré ?

**Question centrale** : Comment utiliser le clustering pour identifier des joueurs aux profils similaires en tenant compte des spécificités positionnelles et des métriques de performance ?

## Méthodologie

### 1. Analyse Exploratoire
- Inspection de la qualité et de la structure des données
- Analyse des distributions par poste et par âge
- Identification des corrélations entre variables
- Détection des valeurs aberrantes

### 2. Prétraitement des Données
- Traitement des valeurs manquantes
- Normalisation (StandardScaler, RobustScaler)
- Sélection de features pertinentes par poste
- Encodage des variables catégorielles si nécessaire

### 3. Réduction de Dimensionnalité
- **PCA (Principal Component Analysis)** : Compression de l'information et visualisation
- **t-SNE** : Visualisation non-linéaire des relations entre joueurs
- Analyse de la variance expliquée

### 4. Clustering
- **K-Means** : Clustering par partition
- **DBSCAN** : Clustering par densité (détection d'outliers)
- **Clustering Hiérarchique** : Analyse de la structure hiérarchique des groupes
- Comparaison des performances des algorithmes

### 5. Validation et Interprétation
- Métriques de qualité : Silhouette Score, Davies-Bouldin Index, Calinski-Harabasz
- Méthode du coude pour K-Means
- Interprétation métier des clusters

### 6. Applications Pratiques
- Recherche de remplaçants pour un joueur donné
- Identification de jeunes talents similaires à des joueurs élites
- Analyse de la polyvalence positionnelle

## Structure du Projet

```
.
├── cache/                          # Cache pour optimisation des calculs
├── data/
│   └── cleaned_scouting_report.csv # Dataset nettoyé
├── doc/
│   └── dataset.md                  # Documentation détaillée du dataset
├── src/
│   └── __pycache__/                # Cache Python
├── viz/                            # Visualisations générées
├── README.md                       # Ce fichier
├── requirements.txt                # Dépendances Python
├── TODO.md                         # Liste des tâches
└── notebook_clustering.ipynb       # Notebook principal d'analyse
```

## Dataset

Le dataset `cleaned_scouting_report.csv` contient des statistiques détaillées de joueurs normalisées par 90 minutes jouées. Les variables couvrent plusieurs dimensions de la performance :

### Variables d'Identification
- `player_name` : Nom du joueur
- `Position` : Poste principal
- `Team Name` : Club actuel
- `Age` : Âge du joueur

### Variables de Performance

#### Offensive
- `Buts (sans les pénaltys)` : Nombre de buts marqués (hors penalties)
- `npxG: xG sans les pénaltys` : Expected Goals hors penalties
- `Total des tirs` : Nombre total de tirs tentés
- `Passes décisives` : Nombre de passes décisives
- `xAG: Prévu(s) Buts assistés` : Expected Assisted Goals

#### Construction du Jeu
- `Passes tentées` : Nombre total de passes tentées
- `% de passes réussies` : Pourcentage de réussite des passes
- `Passes progressives` : Passes faisant progresser le ballon vers le but adverse
- `Actions menant à un tir` : Nombre d'actions ayant abouti à un tir

#### Technique Individuelle
- `Dribbles réussis` : Nombre de dribbles réussis
- `Possessions progressives` : Contrôles de balle faisant progresser le ballon
- `Touches (SurfRépOff)` : Touches dans la surface de réparation adverse
- `Passes progressives reçues` : Nombre de passes progressives reçues

#### Défensive
- `Tacles` : Nombre de tacles effectués
- `Interceptions` : Nombre d'interceptions
- `Balles contrées` : Nombre de tirs/passes contrés
- `Dégagements` : Nombre de dégagements défensifs
- `Duel aérien gagnés` : Nombre de duels aériens remportés

#### Métrique Composite
- `npxG + xAG` : Somme de l'expected goals et expected assisted goals (contribution offensive totale)

Pour plus de détails, consulter `doc/dataset.md`.

## Installation et Exécution

### Prérequis
- Python 3.8+
- Jupyter Notebook ou JupyterLab

### Installation des dépendances

```bash
# Cloner le repository (si applicable)
git clone [URL_DU_REPO]
cd projet-clustering-football

# Installer les dépendances
pip install -r requirements.txt
```

### Exécution

```bash
# Lancer Jupyter
jupyter notebook

# Ouvrir le notebook principal
# notebook_clustering.ipynb
```

## Dépendances Principales

- `pandas` : Manipulation et analyse de données
- `numpy` : Calculs numériques
- `scikit-learn` : Algorithmes de machine learning (clustering, PCA, normalisation)
- `matplotlib` : Visualisations
- `seaborn` : Visualisations statistiques avancées
- `scipy` : Fonctions scientifiques et statistiques

Voir `requirements.txt` pour la liste complète.

