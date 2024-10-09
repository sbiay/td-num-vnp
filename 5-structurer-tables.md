---
mainfont: Alegreya
title: Structurer les données en plusieurs tables
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Structurer les données en plusieurs tables
=====

Plan :

1. [Relation simple par une clé étrangère](#t1)
	1. [Table des lieux ](#t1-1)
2. [Relation multiple par une table de relation](#t2)

[comment]: <> (FINET)


<a id='t1'/>

# Relation simple par une clé étrangère
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Table des lieux 

### <2>

- Créer une table des **Lieux** où départer les données relatives aux communes et aux départements

- Utiliser le code INSEE comme clé étrangère dans la table **Fusion** que l'on rebasptise **Ponts**


### <3>

1. On copie-colle toutes les données pertinentes dans une feuille brouillon

2. On élimine les doublons

	- Sélectionner toutes les données
	- **Données** > Plus de filtres > Filtre standard
	- Nom de champ : aucun(e)
	- Options : sans doublon

3. On sélectionne le résultat et on le copie colle dans la feuille **Lieux**

	- **Ctrl + Maj + V** : Valeurs seulement


### <4>

La *clé étrangère* de la table **Pont** joue le rôle d'*identifiant* de chaque commune dans la table **Lieux**

- On déplace la colonne contenant le code INSEE à gauche
- On ajoute les en-têtes si besoin
- On contrôle les données

Est-ce satisfaisant ?


### <5>

On a un problème avec :

- Certains enregistrements où le lieu est un département
- Des communes particulières comme L'Île-d'Elle ou Sainte-Radégonde-des-Noyers


### <6>

- Dans la table pont, éliminer les données désormais inutiles

- Créer une fonction de recherche pour afficher la commune et le département :
	
	- Si le code INSEE est bien dans la colonne H, la fonction pour afficher la commune est : `=RECHERCHEV(H2;$Lieux.A:D;2;0)`

Pour copier-coller une formule sans modifier la couleur de fond de la cellule : clic droit > Collage spécial > Formule


<a id='t2'/>

# Relation multiple par une table de relation