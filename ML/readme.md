# Rapport d’analyse et d’interprétation — Qualité du vin blanc

Fait par BOMBOMA Namangue Manuella

## Contexte et objectif

L’étude porte sur un jeu de données relatif à des échantillons de vins blancs "Vinho Verde" du nord du Portugal. Le but est de modéliser la qualité du vin à partir de tests physico-chimiques. La variable cible est la qualité, notée entre 0 et 10, basée sur une évaluation sensorielle.

***

## Description des données

- Nombre d’exemples : 4898 vins blancs
- Nombre de variables : 11 caractéristiques physico-chimiques continues
- Caractéristiques principales : acidité fixe, acidité volatile, acide citrique, sucre résiduel, chlorures, dioxyde de soufre libre et total, densité, pH, sulfates, alcool
- Variable cible : qualité (score entre 0 et 10)
- Données sans valeurs manquantes

***

## Analyse exploratoire

- Distribution des qualités : la majorité des vins ont une qualité autour de 5-6, avec peu d’exemples très mauvais (3) ou très bons (8-9)
- Visualisation par boxplots des variables montre la dispersion et la présence d’éventuelles valeurs extrêmes
- Matrice de corrélation inspectée pour déceler des relations linéaires entre variables (corrélations modérées observées, par exemple entre alcool et qualité)

***

## Préparation des données

- La variable qualité a été binarisée en deux classes : vins de mauvaise qualité (≤5) et vins de bonne qualité (>5) pour simplifier la classification
- Les données ont été divisées en ensembles d’entraînement (~1/3), validation (~1/3) et test (~1/3) en maintenant la stratification selon la variable cible pour respecter la répartition des classes
- Les données d’entrée ont été standardisées (centrées-réduites) pour améliorer les performances des modèles

***

## Modélisation

- Un classifieur K-Nearest Neighbors (KNN) a été entraîné avec différentes valeurs de $k$ (1, 3, 5, ..., 35)
- Pour chaque $k$, l’erreur de classification a été calculée sur les ensembles d’entraînement et validation
- La valeur optimale $k^\star$ correspond au plus petit taux d’erreur sur l’ensemble de validation, trouvée grâce au vecteur des erreurs

***

## Résultats et interprétation

- Les erreurs diminuent généralement avec l’augmentation de $k$ jusqu’à un certain point, puis augmentent à cause du sur-lissage (biais élevé)
- Le choix du $k^\star$ optimal équilibre le compromis biais-variance pour donner un bon pouvoir prédictif
- La qualité de vin étant difficile à prédire parfaitement, la simplification en classification binaire aide à obtenir des performances stables

***

## Perspectives d’amélioration

- Tester d’autres modèles de classification (SVM, arbres de décision, forêts aléatoires)
- Effectuer une sélection de variables pour retirer les moins pertinentes
- Étendre l’analyse aux vins rouges ou à une classification multi-classes pour une modélisation plus fine
- Enrichir les données avec des variables supplémentaires (type de raisin, conditions de fermentation)

***

## Références

- Paulo Cortez et al., "Modeling wine preferences by data mining from physicochemical properties," Decision Support Systems, 2009.
- Jeu de données Wine Quality UCI : https://archive.ics.uci.edu/ml/datasets/Wine+Quality

***

## Conclusion

-L’étude montre que l’algorithme K-Nearest Neighbors est un modèle efficace pour classer la qualité du vin blanc à partir de ses caractéristiques physico-chimiques. Le choix optimal du paramètre kk permet d’équilibrer le compromis entre biais et variance, assurant ainsi des performances maximales sur des données non vues. Bien que KNN offre une précision acceptable, il existe toutefois des limites liées notamment à la nature déséquilibrée des classes et à la complexité croissante pour des ensembles de données volumineux.

-Pour améliorer davantage la prédiction, il est recommandé de comparer KNN avec d’autres algorithmes tels que les forêts aléatoires, les machines à vecteurs de support (SVM), voire les réseaux de neurones artificiels, qui dans des études similaires ont montré des performances supérieures à KNN. De plus, des techniques de sélection de variables et d’ingénierie des caractéristiques pourraient renforcer la modélisation.

-Enfin, cette modélisation contribue à une meilleure compréhension des facteurs influençant la qualité du vin et peut être un outil précieux pour les producteurs visant à optimiser leurs processus en fonction des variables physico-chimiques. La classification binaire reste une simplification utile, mais une approche multi-classes peut être envisagée pour une analyse plus fine et nuancée.


