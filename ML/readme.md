# Rapport d'Analyse et Modélisation de la Qualité du Vin Blanc
Fait par BOMBOMA Namangue Manuella

## Description du jeu de données

Le jeu de données utilisé provient de la base UCI Wine Quality et contient 4898 échantillons de vin blanc du nord du Portugal. Chaque échantillon est caractérisé par 11 variables physico-chimiques mesurées (comme acidité fixe, acidité volatile, pH, alcool, ...), et une variable cible `quality` représentant la qualité du vin sur une échelle de 0 à 10. Les données sont multivariées et ne contiennent pas de valeurs manquantes. La distribution des qualités montre un déséquilibre, avec une majorité de vins autour de la qualité 6-5, et peu d'exemples de qualité très faible ou très élevée.

## Préparation des données

- La colonne `quality` est séparée comme variable cible $Y$.
- Les variables explicatives sont stockées dans $X$.
- Une analyse descriptive basique est faite par affichage des premières lignes et résumé des colonnes.
- Le dataset est divisé en trois sous-ensembles :
    - Entraînement initial (1/3 du total)
    - Puis entraînement final et validation par split à 50% sur le sous-ensemble d'entraînement initial
- La variable cible est parfois binarisée en qualité "mauvais" (qualité ≤ 5) et "bon" (qualité > 5) pour simplifier la classification.


## Analyse exploratoire

- Boîtes à moustaches (boxplots) illustrent la distribution des variables physico-chimiques.
- Une matrice de corrélation montre les relations entre variables, aidant à remarquer celles qui sont fortement liées.


## Modélisation par k-plus proches voisins (KNN)

- Un modèle KNN est entraîné sur les données normalisées (avec standardisation des variables par moyenne et écart type sur l'ensemble d'entraînement).
- Une gamme de valeurs impaires de $k$ (de 1 à 35 par pas de 2) est testée pour trouver la meilleure complexité du modèle.
- Pour chaque $k$, l'erreur de classification est évaluée sur le train set et sur le validation set.
- La valeur optimale $k^*$ minimise l'erreur de validation.


## Résultats

- L'erreur de classification diminue initialement quand $k$ augmente de 1 vers un optimum, puis remonte, illustrant un compromis biais-variance classique.
- La valeur optimale $k^*$ est retenue pour obtenir la meilleure généralisation.
- Les prédictions finales sont obtenues avec ce $k^*$, et l'erreur mesurée permet d'estimer la performance du modèle.


## Conclusion

Cette étude montre une méthode efficace pour modéliser la qualité du vin blanc à partir de variables physico-chimiques, avec une classification supervisée par KNN. La normalisation des données et la validation croisée sur plusieurs valeurs de $k$ permettent d'optimiser la performance. Le modèle pourrait être amélioré par d'autres techniques de sélection de variables ou modèles plus complexes.


