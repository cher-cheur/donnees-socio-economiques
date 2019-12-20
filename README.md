# Données socio-économiques et criminelles
L'objectif est de construire une forêt aléatoire d'arbres de dé pour prédire le nombre de crimes violents par habitant. A partir d'une combinaison des données socio-économique du CENSUS 1990 des Etats-Unis et des données criminels du FBI UCR en 1995.  

# Réccupérer les données
Il faut aller sur : http://archive.ics.uci.edu/ml/datasets/communities+and+crime pour téléchager les deux fichiers des données et d'explication. En essayant d'ouvrir les fichiers avec un éditeur de texte, vous remarquerez qu'il faudra les manipuler pour avoir un jeu de données correcte. 

# Environnement de travail
Nous utiliserons Python et les bibliothèques: sklearn, numpy, seaborn & matplotlib, sont à importer.

# Manipulaion des données
Première chose à remarquer est que les attributs des colonnes du fichier communities.data n'y sont pas et qu'il faut réccupérer ces attributs du fichier communities.name, créer un nouveau fichier attributes.csv puis importer ce dernier et communities.data à notre environnement de travail en créant le lien entre les deux.

# Nettoyage des données
Après avoir affiché le jeu de données correctement, il est clair que les 4 premières variables sont catégoriques, nous les retirons alors. Nous nous retrouvons avec un jeu de données de 1994 observations et 123 variables quantitatives.

Nous trouvons qu'une variable "OtherPerCop" a une seule valeur manquante, tandis que 21 autres ont majoritairement des valeurs manquantes. Nous retirons ces dernières et remplaçons celle de "OtherPerCop" par la moyenne de ses observations.

Le jeu de données sur lequel nous allons opérer est de 101 variables et 1994 obsevartions.

Nous créons la matrice la corrélation pour apercevoir les niveaux de correlations entre les variables de notre jeu de données.
Nous retirons les variables les moins corrélées avec la variable à prédire, et nous gardons que les variables corrélées à plus de 40% avec la variable à prédire. Nous nous retrouvons alors avec 26 variables explicatives.

# Répartition de l'ensemble d'entraînement et de validation 
Une fois avoir défini l'ensemble des variables explicatives et la variable à prédire, nous répartissons les ensembles d'entraînement et de validation.

# Normaliser les variables explicatives
Nous allons centrer et réduire nos variables explicatives.

# Créer le modèle seuil
Nous allons déployer une forêt aléatoire de 100 estimateurs d'arbres de décision sur l'ensemble d'entrâinement et imprimerons le score de ce modèle. Ainsi que la moyenne absolue d'érreur et la moyenne d'erreurs au carré. On essayera ensuite d'avoir des performances meilleures en le comparant à ce modèle.

# Optimisation des paramètres du train_test_split
Pour cela nous créons une boucle testant les Random_Stae de 0 à 50 et afficher les résultats du modèle ayant eu le meilleur score.

# Conclusion et amélioration
Avec de telle performance, le modèle construit peut être généralisé sur des nouvelles données mais cela n’empêche pas de le faire évoluer en :
    • Trouvant le seuil de corrélation maximisant le score du modèle.
    • S’il y a assez de données par état« state » – sachant que chaque état a ses propres lois -  créer une forêt aléatoire par état et comparer variables explicatives.
