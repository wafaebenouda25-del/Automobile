# 🚗 Analyse et prédiction des prix des automobiles

## Table des matières

1. [Présentation du projet](#1-présentation-du-projet)
2. [Problématique](#2-problématique)
3. [Objectifs](#3-objectifs)
4. [Jeu de données](#4-jeu-de-données)
5. [Technologies et bibliothèques](#5-technologies-et-bibliothèques)
6. [Méthodologie](#6-méthodologie)
7. [Résultats principaux](#7-résultats-principaux)
8. [Limites et pistes d'amélioration](#8-limites-et-pistes-damélioration)
9. [Structure du projet](#9-structure-du-projet)
10. [Exécution du projet](#10-exécution-du-projet)
11. [Conclusion](#11-conclusion)

---

## 1. Présentation du projet

Ce projet a été réalisé dans le cadre du module **Analyse de données et visualisation par Python**. Il porte sur l'étude d'un jeu de données relatif aux véhicules d'occasion, dans le but d'analyser les caractéristiques des automobiles et d'étudier les facteurs associés à leur prix de vente.

Le travail comprend plusieurs étapes : exploration des données, préparation et nettoyage, analyse statistique, visualisation graphique et application de modèles de Machine Learning pour la prédiction des prix.

## 2. Problématique

Dans quelle mesure les caractéristiques d'un véhicule, notamment son ancienneté, son kilométrage et son type de carburant, permettent-elles d'expliquer et de prédire son prix de vente ?

## 3. Objectifs

- Explorer et comprendre les données automobiles.
- Identifier et traiter les données manquantes, les doublons et les valeurs aberrantes.
- Étudier la distribution des prix et les caractéristiques des véhicules.
- Analyser les relations entre les variables à l'aide de méthodes statistiques.
- Quantifier l'effet du carburant (diesel et essence) sur le prix.
- Construire et évaluer des modèles de régression pour la prédiction des prix.

## 4. Jeu de données

Le projet utilise le fichier `CAR DETAILS FROM CAR DEKHO.csv` (données de la plateforme indienne CarDekho, disponibles notamment sur Kaggle).

Le fichier contient **4 340 observations et 8 colonnes**, dont **cinq sont exploitées** dans cette analyse :

| Variable | Description |
|---|---|
| `name` | Nom du véhicule |
| `year` | Année de fabrication |
| `selling_price` | Prix de vente |
| `km_driven` | Kilométrage parcouru |
| `fuel` | Type de carburant |

Les colonnes `seller_type`, `transmission` et `owner` ne sont pas utilisées. La monnaie n'est pas précisée dans le fichier ; s'agissant d'une plateforme indienne, les prix sont vraisemblablement en roupies indiennes.

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

- Suppression des doublons (767 doublons exacts) et des valeurs manquantes.
- Filtrage des valeurs invalides.
- Détection et traitement des valeurs aberrantes à l'aide de la méthode IQR.

Après cette étape, le jeu de données passe de **4 340 à 3 283 observations**.

### 6.3. Création de variables

De nouvelles variables sont construites afin d'enrichir l'analyse :

- `age` : ancienneté du véhicule (2026 − année de fabrication).
- `km_an` : kilométrage moyen annuel.
- `marque` : marque extraite du nom du véhicule.
- `log_prix` : logarithme du prix, pour réduire l'asymétrie de la distribution.

### 6.4. Analyse statistique et visualisation

- Étude descriptive des prix de vente.
- Analyse de la répartition des véhicules selon le carburant.
- Comparaison des prix médians selon le carburant et les marques.
- Étude des corrélations de Pearson et de Spearman.
- Importance des variables par forêt aléatoire.
- Comparaison diesel / essence par tranche d'âge et par régression OLS.
- Courbe de dépréciation selon le kilométrage (déciles).

### 6.5. Modélisation et prédiction

Deux modèles de régression sont étudiés :

- Linear Regression
- Random Forest Regressor

Les données sont réparties en ensembles d'entraînement et de test selon un rapport de 80 % / 20 %. Les modèles sont entraînés sur le logarithme du prix, puis les prédictions sont ramenées à l'échelle d'origine.

Les performances sont évaluées à l'aide de deux indicateurs :

- **R²** (coefficient de détermination).
- **MAE** (Mean Absolute Error).

## 7. Résultats principaux

- **Distribution du prix** : prix médian de 330 000 ; distribution asymétrique à droite (skewness 0,87), corrigée par une transformation logarithmique (−0,48).
- **Corrélations (Spearman avec le prix)** : âge −0,71 ; kilométrage −0,30 ; kilométrage annuel 0,04. L'âge est le facteur le plus lié au prix.
- **Importance des variables (Random Forest)** : âge 49,7 %, marque 21,0 %, kilométrage 19,2 %, carburant 10,1 %.
- **Effet du carburant** : à âge et kilométrage égaux, une voiture essence se vend en moyenne 36,1 % moins cher qu'un diesel (p < 0,001).
- **Modèles prédictifs (jeu de test)** :

| Modèle | R² | MAE |
|---|---|---|
| Régression linéaire | 0,63 | ≈ 110 227 |
| Random Forest | 0,61 | ≈ 108 873 |

## 8. Limites et pistes d'amélioration

- Variables déterminantes absentes (état du véhicule, puissance, localisation).
- Carburants CNG, LPG et Electric très peu représentés (moins de 2 %) : conclusions peu fiables.
- Le filtrage IQR retire les véhicules les plus chers, ce qui limite la portée du modèle sur le haut de gamme.
- Pistes : exploiter `seller_type`, `transmission` et `owner`, régler les hyperparamètres par validation croisée, tester le Gradient Boosting.

## 9. Structure du projet

```text
Automobile/
│
├── archive/
│   └── CAR DETAILS FROM CAR DEKHO.csv
│
├── car_details.ipynb
├── requirements.txt
├── README.md
└── .gitignore
```

## 10. Exécution du projet

```bash
git clone https://github.com/wafaebenouda25-del/Automobile.git
cd Automobile
pip install -r requirements.txt
jupyter notebook car_details.ipynb
```

Vérifiez que le fichier CSV se trouve dans le dossier `archive/`, puis exécutez les cellules du notebook dans l'ordre.

## 11. Conclusion

Ce projet permet de mettre en pratique les principales étapes d'un processus d'analyse de données, depuis l'exploration et le nettoyage jusqu'à la visualisation et la modélisation prédictive.

L'âge est le principal déterminant du prix des véhicules d'occasion, devant la marque et le kilométrage. Les deux modèles testés expliquent environ 62 % de la variance du prix, avec une erreur absolue moyenne d'environ 110 000.

---

_Projet académique — Analyse de données et visualisation par Python_
