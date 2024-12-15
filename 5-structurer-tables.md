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
	1. [Table des matériaux ](#t2-1)
	2. [1. Transformer les données ](#t2-2)
	3. [2. Prévoir une méthode d'identification de chaque matériau ](#t2-3)
	4. [Créer de nouvelles tables ](#t2-4)

[comment]: <> (FINET)

<!--


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

- Il peut rester des enregistrements où l'INSEE est un numéro département : à corriger
- Des communes particulières comme L'Île-d'Elle ou Sainte-Radégonde-des-Noyers créent des doublons : supprimer les lignes inutiles


### <6>

- Dans la table pont, éliminer les données désormais inutiles

- Créer une fonction de recherche pour afficher la commune et le département :
	
	- Si le code INSEE est bien dans la colonne H, la fonction pour afficher la commune est : `=RECHERCHEV(H2;$Lieux.A:D;2;0)`

Pour copier-coller une formule sans modifier la couleur de fond de la cellule : clic droit > Collage spécial > Formule

-->


<a id='t2'/>

# Relation multiple par une table de relation
[comment3]: <6> (TITRE1)


<a id='t2-1'/>

## Table des matériaux 

### <7>

Commencer par isoler les données dans une nouvelle feuille brouillon :

1. Filtrer la colonne **materiau_du_gros_oeuvre** pour ne pas avoir de donnée vide

2. Copier dans une nouvelle feuille brouillon :

- identifiant
- materiau_du_gros_oeuvre


### <8>

Pour créer la relation multiple entre pont et matériaux, il faut procéder en trois étapes :

1. Transformer les données pour parvenir à des **relations 1-1** : 1 identifiant de pont pour 1 matériau

2. Créer un **identifiant** pour chaque matériau

3. Créer la **table** des matériaux


<a id='t2-2'/>

## 1. Transformer les données 

### <9>

Pour avoir sur chaque ligne un identifiant et un seul matériau,\
on fait appel aux expressions régulières

- Copier toutes les données (sans les en-têtes) dans Notepad++

- On veut remplacer chaque point-virgule par l'identifiant du début de la ligne

- Find : `([IP]A\d+)(\t[^;\r]+);\s?`\

- Replace with : `$1$2\r\n$1\t`


### <10>

- Vérifier la propreté du résultat (nettoyer à la main si besoin)
- Il y a des espaces invisibles en fin de ligne

	- Find : `\s\r`
	- Replace All : `\r`


<a id='t2-3'/>

## 2. Prévoir une méthode d'identification de chaque matériau 

### <11>

La feuille obtenue est une **table de relations** ; on la renomme : `Relation matérialité`

À présent, on souhaite créer le thésaurus des matériaux, qui ne devra contenir aucun doublon et où chaque matériau aura son identifiant.

On doit donc trouver une méthode pour créer des identifiants


### <12>

- Trier la colonne des matériaux
- Dans une nouvelle colonne **id matériau** inscrire la première valeur pour le premier matériau : `1`

- Pour générer l'identifiant de l'enregistrement suivant j'écris la formule : `=SI(B3=B2;C2;C2+1)`


### <13>

- Renommer la colonne A : `id Pont`
- Insérer une nouvelle colonne en B
- Y copier-coller le contenu de la colonne **id matériau** pour transformer les formules en valeurs (copier-coller avec un **Ctrl + Maj + V** et cliquer sur valeurs seulement)
- Supprimer la colonne D


### <14>

- Dans une nouvelle feuille, copier-coller tous les matériaux avec leurs identifiants
- Supprimer les doublons

	- Sélectionner toutes les données
	- **Données** > Plus de filtres > Filtre standard
	- Nom de champ : aucun(e)
	- Options : sans doublon

- Copier le résultat dans une nouvelle feuille à nommer : `Matériaux`

- Remplacer la colonne C de la feuille **Relation matérialité** par une formule RECHERCHEV permettant d'afficher le matériau selon son identifiant


### <15>


Félicitations !!!

Vous êtes devenus de véritables ingénieurs de la donnée patrimoniale !

Et avez d'ores-et-déjà obtenu **18 points** pour l'évaluation !


<a id='t2-4'/>

## Créer de nouvelles tables 

### <16>

- Créer une copie de la base de données qui ne contienne que le département de la **Sarthe**

<<<<<<< HEAD
- Pour avoir 18/20 : créer une table spécifique pour les **Personnes** :
	
	- Attention : la même personne a pu intervenir sur plusieurs ponts, c'est donc une relation multiple, comme les matériaux
	- Conseil : travailler à la main sera plus efficace qu'avec des expressions régulières

- Pour avoir 20/20 : créer une table pour les **Datations**


### <17>

Vous pouvez me poser des questions à tout moment si vous avez un doute sur la marche à suivre.

Il faut me remettre les fichiers le 16 décembre au plus tard.
=======
- Pour avoir 20/20 : créer une table spécifique pour les **Personnes** :
	
	- Attention : la même personne a pu intervenir sur plusieurs ponts, c'est donc une relation multiple, comme les matériaux
	- Conseil : travailler à la main sera plus efficace qu'avec des expressions régulières

- Pour avoir 22/20 : créer une table pour les **Datations**


### <17>

Vous pouvez me poser des questions à tout moment si vous avez un doute sur la marche à suivre.

Il faut me remettre les fichiers le 12 novembre au plus tard.
>>>>>>> cc5ef84536d3d7675324bf64537ebd98732b4a36
