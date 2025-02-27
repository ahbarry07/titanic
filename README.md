# Titanic - Machine Learning from Disaster  

## Introduction  
Ce projet Kaggle consiste à prédire la survie des passagers du Titanic lors de son naufrage tragique en 1912. L'objectif est de développer un modèle prédictif qui détermine quels types de personnes étaient plus susceptibles de survivre, en utilisant des données sur les passagers telles que leur nom, âge, sexe, et classe socio-économique.


## Description du projet  
Ce projet est structuré autour de deux fichiers Jupyter Notebook qui contiennent les étapes de l'analyse de données (notebook/EDA.ipynb), l'ingénierie des fonctionnalités, l'entraînement du modèle, et les prédictions (scripts/model.ipynb).  

Les principales étapes suivies dans ce projet incluent :  
1. Exploration des données (EDA) pour comprendre les relations et tendances.
2. Ingénierie des fonctionnalités pour extraire des informations pertinentes et améliorer les performances du modèle.
3. Entraînement et évaluation de plusieurs modèles de machine learning.
4. Soumission des prédictions pour évaluer les performances sur les données de test.

## Ingénierie des fonctionnalités  
L'ingénierie des fonctionnalités a joué un rôle crucial pour améliorer les performances du modèle prédictif. Voici les caractéristiques utilisées et les transformations effectuées :  

### 1. **Pclass**  
   - **Description :** La classe socio-économique des passagers (1ère, 2ème ou 3ème classe).  
   - **Raison :** Les passagers des classes supérieures avaient un taux de survie plus élevé. Cette variable a été utilisée directement sans transformation.  

### 2. **Sex**  
   - **Description :** Le sexe du passager (homme ou femme).  
   - **Transformation :** Converti en valeur numérique binaire (0 pour les hommes, 1 pour les femmes).  
   - **Raison :** Les femmes avaient une probabilité de survie plus élevée, ce qui rend cette variable très prédictive.  

### 3. **Age**  
   - **Description :** L’âge des passagers, avec des valeurs manquantes imputées par la moyenne ou des valeurs estimées en fonction de la classe socio-économique et du Name_Title(ex: Mr ou Miss).  
   - **Transformation :** L’âge a été utilisé à la fois comme une variable continue.
   - **Raison :** L’âge influence significativement la survie, notamment pour les enfants qui avaient une plus grande chance de survie.  

### 4. **Family_Size**  
   - **Description :** Taille de la famille calculée comme :  
     \[
     \text{Family\_Size} = \text{SibSp} + \text{Parch} + 1
     \]  
     où `SibSp` représente le nombre de frères/sœurs et conjoints à bord, et `Parch` le nombre de parents/enfants à bord.  
   - **Raison :** Les passagers avec des familles petites ou moyennes avaient de meilleures chances de survie par rapport aux passagers seuls ou avec des familles très grandes.  

### 5. **Embarked**  
   - **Description :** Port d’embarquement du passager (C = Cherbourg, Q = Queenstown, S = Southampton).  
   - **Transformation :** Encodé en variables indicatrices pour permettre au modèle de traiter cette variable catégorique.  
   - **Raison :** Le port d’embarquement peut indiquer une différence socio-économique ou des préférences d’attribution de places sur le navire, ce qui peut influencer la survie.  

### 6. **Fare**  
   - **Description :** Tarif payé par le passager pour son billet.
    - **Transformation :**Les valeurs manquantes ont été remplacés par la moyenne des 'Fare' groupé par la classe(Pclasse).
   - **Raison :** Le tarif peut refléter indirectement la classe socio-économique et, par conséquent, la probabilité de survie.  


Ces transformations et créations de variables ont permis de mieux capturer les relations dans les données et d’améliorer la capacité du modèle à prédire la survie des passagers.  

## Modèle utilisé    
Le modèle qui a obtenu le meilleur score (0.79425) sur le leaderboard est basé sur :  
- Un algorithme de **RandomForestClassifier**.  
- Une recherche de grille (GridSearchCV) a été réalisée pour optimiser les hyperparamètres du modèle.  

## Installation de l'environement
```bash
conda env create -f environment.yml
conda activate titanic
```