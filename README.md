# 🚗 Analyse et prédiction des prix des automobiles

## 1. Présentation du projet

Ce projet a été réalisé dans le cadre du module **Analyse de données et visualisation par Python**. Il porte sur l'étude d'un jeu de données relatif aux véhicules d'occasion, dans le but d'analyser les caractéristiques des automobiles et d'étudier les facteurs associés à leur prix de vente.

Le travail comprend plusieurs étapes : exploration des données, préparation et nettoyage, analyse statistique, visualisation graphique et application de modèles de Machine Learning pour la prédiction des prix.

## 2. Problématique

**Dans quelle mesure les caractéristiques d'un véhicule, notamment son ancienneté, son kilométrage et son type de carburant, permettent-elles d'expliquer et de prédire son prix de vente ?**

## 3. Objectifs

- Explorer et comprendre les données automobiles.
- Identifier et traiter les données manquantes, les doublons et les valeurs aberrantes.
- Étudier la distribution des prix et les caractéristiques des véhicules.
- Analyser les relations entre les variables à l'aide de méthodes statistiques.
- Construire et évaluer des modèles de régression pour la prédiction des prix.

## 4. Jeu de données

Le projet utilise le fichier `CAR DETAILS FROM CAR DEKHO.csv`.

Le jeu de données initial contient **4 340 observations** et les cinq variables suivantes :

| Variable | Description |
|---|---|
| `name` | Nom du véhicule |
| `year` | Année de fabrication |
| `selling_price` | Prix de vente |
| `km_driven` | Kilométrage parcouru |
| `fuel` | Type de carburant |

## 5. Technologies et bibliothèques

- **Python** : langage de programmation.
- **Pandas** : manipulation et analyse des données.
- **NumPy** : calcul numérique.
- **Matplotlib** et **Seaborn** : visualisation graphique.
- **Statsmodels** : analyse statistique et régression.
- **Scikit-learn** : construction et évaluation des modèles de Machine Learning.

## 6. Méthodologie

### 6.1. Exploration des données

- Consultation de la structure et des dimensions du jeu de données.
- Identification des types de variables.
- Vérification des valeurs manquantes et des doublons.
- Détection des valeurs potentiellement anormales.

### 6.2. Nettoyage et préparation

- Suppression des doublons et des valeurs manquantes.
- Filtrage des valeurs invalides.
- Détection et traitement des valeurs aberrantes à l'aide de la méthode IQR.

Après cette étape, le jeu de données passe de 4 340 à 3 283 observations.

### 6.3. Création de variables

De nouvelles variables sont construites afin d'enrichir l'analyse :

- `age` : ancienneté du véhicule.
- `km_an` : kilométrage moyen annuel.
- `marque` : marque extraite du nom du véhicule.

### 6.4. Analyse statistique et visualisation

- Étude descriptive des prix de vente.
- Analyse de la répartition des véhicules selon le carburant.
- Comparaison des prix médians selon le carburant et les marques.
- Étude des corrélations de Pearson et de Spearman.
- Visualisation des distributions et des relations entre les variables.

### 6.5. Modélisation et prédiction

Deux modèles de régression sont étudiés :

- **Linear Regression**
- **Random Forest Regressor**

Les données sont réparties en ensembles d'entraînement et de test selon un rapport de 80 % / 20 %.

Les performances des modèles sont évaluées à l'aide de deux indicateurs :

- **R² (coefficient de détermination)**.
- **MAE (Mean Absolute Error)**.

## 7. Structure du projet

```text
Automobile/
│
├── archive/
│   └── CAR DETAILS FROM CAR DEKHO.csv
│
├── car_details.ipynb
├── README.md
└── .gitignore
```

## 8. Exécution du projet

1. Cloner le dépôt GitHub.
2. Installer les bibliothèques nécessaires.
3. Ouvrir le notebook `car_details.ipynb` avec Jupyter Notebook ou JupyterLab.
4. Vérifier que le fichier CSV se trouve dans le dossier `archive/`.
5. Exécuter les cellules du notebook dans l'ordre.

## 9. Conclusion

Ce projet permet de mettre en pratique les principales étapes d'un processus d'analyse de données, depuis l'exploration et le nettoyage jusqu'à la visualisation et la modélisation prédictive.

L'utilisation de méthodes statistiques et de modèles de Machine Learning permet d'étudier les facteurs associés au prix des véhicules d'occasion et d'évaluer la capacité des modèles à estimer ce prix.

---

**Projet académique — Analyse de données et visualisation par Python**
