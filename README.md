# Données socio-économiques et criminelles
L'objectif est de construire un arbre de décision pour prédire le nombre de crimes violents par habitant. A partir d'une combinaison des données socio-économique du CENSUS 1990 des Etats-Unis et des données criminels du FBI UCR en 1995.  

# Réccupérer les données
Il faut aller sur : #lien pour téléchager les deux fichiers des données et d'explication. En essayant d'ouvrir les fichier avec un éditeur de texte, vous remarquerez qu'il faudra les manipuler pour avoir un jeu de données correcte. 

# Environnement de travail
Nous utiliserons Python et les bibliothèques: sklearn, numpy, seaborn & matplotlib, sont à importer.

# Manipulaion des données
Première chose à remarquer est que les attributs des colonnes du fichier communities.data n'y sont pas et qu'il faut réccupérer ces attributs du fichier communities.name, créer un nouveau fichier attributes.csv puis importer ce dernier et communities.data à notre environnement de travail  en créant le lien entre les deux.

# Nettoyage des données
Après avoir affiché le jeu de données correctement, il est clair que les 4 premières variables sont catégoriques, nous les retirons alors. 

(à suivre)
