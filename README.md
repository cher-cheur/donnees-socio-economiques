# Projet : Prédiction du Nombre de Crimes Violents par Habitant

## Vue d'Ensemble du Projet

Ce projet de Machine Learning vise à prédire le nombre de crimes violents par habitant dans les communautés des États-Unis. En combinant des données socio-économiques du recensement américain de 1990 (CENSUS) avec des données criminelles issues du rapport FBI UCR de 1995, nous avons développé un modèle de régression robuste.

L'objectif est de fournir un outil analytique capable d'estimer les niveaux de criminalité violente, ce qui pourrait aider à l'allocation des ressources ou à la compréhension des facteurs influents. Ce projet est un exemple complet d'un pipeline de Machine Learning, de la préparation des données à la modélisation avancée et au déploiement potentiel.

## Fonctionnalités Clés & Méthodologie

  * [cite\_start]**Sources de Données Riches :** Utilisation de données publiques et reconnues (US Census, FBI UCR, US LEMAS survey [cite: 4]).
  * **Nettoyage et Préparation Avancée des Données :**
      * [cite\_start]**Gestion des Valeurs Manquantes :** Imputation ciblée (moyenne pour `OtherPerCap`) et suppression des colonnes avec un trop grand nombre de valeurs manquantes (\>50%, notamment les données LEMAS [cite: 46]).
      * **Sélection de Caractéristiques par Corrélation :** Identification des prédicteurs les plus pertinents en retenant uniquement les variables ayant une corrélation absolue supérieure à 0.40 avec la variable cible (`ViolentCrimesPerPop`). Ce seuil a été choisi pour réduire la dimensionalité du modèle, améliorer son interprétabilité en se concentrant sur les facteurs les plus influents, et diminuer le bruit dans les données.
  * **Modélisation Comparative :**
      * Comparaison de plusieurs algorithmes de régression (Régression Linéaire, Ridge, SVR, Arbre de Décision, Random Forest) via la validation croisée (R² moyen sur 5 folds) pour identifier le plus performant.
      * Le **Random Forest Regressor** a été sélectionné comme modèle de base en raison de ses performances initiales prometteuses.
  * **Optimisation des Hyperparamètres :** Utilisation de `GridSearchCV` pour trouver la meilleure combinaison d'hyperparamètres pour le Random Forest, améliorant ainsi sa précision et sa généralisabilité.
  * **Évaluation Rigoureuse :** Mesure de la performance du modèle optimisé sur un ensemble de test indépendant à l'aide de métriques telles que le R², l'Erreur Absolue Moyenne (MAE) et l'Erreur Quadratique Moyenne (MSE).
  * **Exportation du Modèle :** Le modèle entraîné et optimisé, ainsi que le `StandardScaler` (pour la normalisation future des données d'entrée), sont sauvegardés pour une utilisation facile dans des applications tierces.

## Structure du Projet

Le projet est organisé pour une clarté maximale et une réutilisation aisée :

```
.
├── README.md                 # Description détaillée du projet
├── notebook/
│   └── crime_prediction.ipynb           # Notebook Jupyter détaillant l'analyse et la modélisation
├── data/
│   ├── communities.data      # Jeu de données principal
│   └── communities.names     # Fichier de métadonnées et noms d'attributs
├── models/                   # Répertoire pour les modèles sauvegardés
│   ├── best_random_forest_model.joblib
│   ├── scaler.joblib
│   └── selected_features.joblib
├── app.py                    # (À venir) Fichier pour l'application Streamlit
├── requirements.txt          # Liste des dépendances Python
└── LICENSE             # Informations sur la licence du projet
```

## Technologies & Dépendances

Ce projet est développé en Python et utilise les bibliothèques suivantes :

  * `pandas` : Manipulation et analyse de données.
  * `numpy` : Opérations numériques.
  * `matplotlib` & `seaborn` : Visualisation de données.
  * `scikit-learn` : Modélisation Machine Learning (régression, prétraitement, sélection de modèles).
  * `joblib` : Sauvegarde et chargement de modèles Python.
  * `streamlit` : (À venir) Pour la création de l'application web interactive.

Pour installer toutes les dépendances, vous pouvez utiliser le fichier `requirements.txt` (à créer ou mettre à jour avec les versions exactes) :

```bash
pip install -r requirements.txt
```

## Comment Exécuter le Projet

### 1\. Cloner le Dépôt

```bash
git clone https://github.com/cher-cheur/donnees-socio-economiques.git
cd donnees-socio-economiques
```

### 2\. Configurer l'Environnement

Il est recommandé d'utiliser un environnement virtuel :

```bash
python -m venv venv
source venv/bin/activate  # Sous Linux/macOS
# ou `venv\Scripts\activate` sous Windows
pip install -r requirements.txt
```

### 3\. Préparer les Données

Assurez-vous que les fichiers `communities.data` et `communities.names` sont bien placés dans le dossier `data/`.

### 4\. Exécuter le Notebook d'Analyse

Le notebook `crime_prediction.ipynb` contient toutes les étapes d'analyse, de nettoyage des données, de modélisation et d'évaluation.

```bash
jupyter notebook notebook/crime_prediction.ipynb
```

Suivez les cellules du notebook séquentiellement. La dernière cellule exportera le modèle entraîné et le `StandardScaler` dans le dossier `models/`.

### 5\. Lancer l'Application Streamlit (À venir)

Une fois le fichier `app.py` créé (à l'étape future de notre processus), vous pourrez lancer l'application Streamlit ainsi :

```bash
streamlit run app.py
```

## Résultats & Conclusions

Le modèle Random Forest optimisé a démontré des performances robustes sur l'ensemble de test, avec un score R² significativement amélioré par rapport au modèle de référence. L'analyse des caractéristiques a permis d'identifier un sous-ensemble pertinent de variables socio-économiques et démographiques qui sont des prédicteurs clés du nombre de crimes violents par habitant.

Ce projet met en lumière l'importance d'un pipeline de données rigoureux, de la sélection des caractéristiques pertinentes à l'optimisation des modèles, pour obtenir des prédictions fiables et exploitables.

## Améliorations Futures

  * **Hyperparamétrage Avancé :** Explorer des techniques d'optimisation plus sophistiquées comme `RandomizedSearchCV` ou les optimisations bayésiennes pour affiner davantage les hyperparamètres.
  * **Ingénierie de Caractéristiques Avancée :** Créer de nouvelles caractéristiques à partir des données existantes (par exemple, ratios, interactions entre variables) qui pourraient capturer des relations plus complexes.
  * **Autres Modèles :** Tester des modèles plus avancés comme XGBoost ou LightGBM.
  * **Analyse par État :** Si les données le permettent, développer des modèles spécifiques à chaque état pour tenir compte des variations régionales.
  * **Déploiement Complet :** Finaliser l'application Streamlit pour permettre aux utilisateurs d'interagir facilement avec le modèle et d'obtenir des prédictions en temps réel.

## Licence

Ce projet est sous la licence [GNU GENERAL PUBLIC LICENSE Version 3, 29 Juin 2007](https://www.google.com/search?q=license/LICENSE).
