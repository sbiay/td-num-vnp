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
3. [Evaluation](#t3)
	1. [Consignes ](#t3-1)

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
[comment3]: <6> (TITRE1)


<a id='t2-1'/>

## Table des matériaux 

### <7>

Commencer par isoler les données dans une nouvelle feuille brouillon :

1. Filtrer la colonne **P** materiau_du_gros_oeuvre pourne pas avoir de donnée vide

2. Copier dans une nouvelle feuille brouillon :

- Identifiant
- materiau_du_gros_oeuvre


### <8>

Pour créer la relation multiple entre pont et matériaux, il faut procéder en trois étapes :

1. Transformer les données pour parvenir à des relations unilatérales : un identifiant de pont pour un matériau

2. Prévoir une méthode d'identification de chaque matériau

3. Créer la table des matériaux


<a id='t2-2'/>

## 1. Transformer les données 

### <9>

Pour avoir sur chaque ligne un identifiant et un seul matériau, on fait appel aux expressions régulières

- Copier toutes les données (sans les en-têtes) dans Notepad ++

- On veut remplacer chaque point-virgule par l'identifiant du début de la ligne

- Find : `([IP]A\d+)(\t[^;]+);\s`\

- Replace with : `$1$2\r\n$1\t`


### <10>

- Vérifier la propreté du résultat (nettoyer à la main si besoin)
- Il y a des espaces invisibles en fin de ligne

	- Find `\s\r`
	- Replace `\r`


<a id='t2-3'/>

## 2. Prévoir une méthode d'identification de chaque matériau 

### <11>

La feuille obtenue est une **table de relations**

À présent, on souhaite créer le thésaurus des matériaux, qui ne devra contenir aucun doublon et où chaque matériau aura son identifiant.

On doit donc trouver une méthode pour créer des identifiants


### <12>

- Trier la colonne des matériaux
- Dans une nouvelle colonne **id matériau** inscrire la première valeur pour le premier matériau : `1`

- Pour générer l'identifiant de l'enregistrement suivant j'écris la formule : `=SI(B3=B2;C2;C2+1)`


### <13>

- Renommer la colonne A : `id Pont`
- Insérer une nouvelle colonne en B
- Y copier-coller le contenu de la colonne **id matériau** pour transformer les formules en valeurs
- Supprimer la colonne D


### <14>

- Dans une nouvelle feuille, copier-coller tous les matériaux avec leurs identifiants
- Supprimer les doublons

	- Sélectionner toutes les données
	- **Données** > Plus de filtres > Filtre standard
	- Nom de champ : aucun(e)
	- Options : sans doublon


<a id='t3'/>

# Evaluation
[comment7]: <14> (TITRE1)


### <15>

Félicitations !!!

Vous êtes devenus de véritables ingénieurs de la donnée patrimoniale !

Et avez d'ores-et-déjà obtenu **14 points** pour l'évaluation !


<a id='t3-1'/>

## Consignes 

### <16>

- Créer une copie de la base de données qui ne contienne que le département de la **Sarthe**

- Nettoyer les données du mieux que vous pouvez :
	
	- Supprimer les doublons
	- Récupérer les infos utiles des enregistrements à supprimer
	- Documenter l'existence de l'enregistrement supprimé
		
		- Il existe ailleurs sous le même identifiant
		- Il existe aussi sous un autre identifiant


- Créer une table spécifique pour les **Personnes**\
	(travailler à la main sera plus efficace qu'avec des expressions régulières)

- Pour avoir 22/20 : créer une table pour les **Datations**


### <17>

- **Il est permis** :

	- De me poser toutes les questions que vous voulez
	- De vous entraider
	- De travailler à la maison

- **Il est obligatoire** de me remettre un fichier individuel le 21 octobre à 18h