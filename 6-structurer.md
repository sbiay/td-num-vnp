---
mainfont: Alegreya
title: Structurer les données en plusieurs tables
date: 1^er^ semestre 2025-2026
author: sebastien.biay@univ-nantes.fr
---

Structurer les données en plusieurs tables
=====

Plan :

1. [Qu'est-ce qu'une base de données ?](#t1)
	1. [Définition ](#t1-1)
	2. [Avantages et inconvénients du modèle en table ](#t1-2)
	3. [Modéliser son objet ](#t1-3)
	4. [Le modèle logique et les cardinalités ](#t1-4)
2. [Relation simple par une clé étrangère](#t2)
	1. [Table des lieux ](#t2-1)
3. [Relation multiple par une table de relation](#t3)
	1. [Table des matériaux ](#t3-1)
	2. [1. Transformer les données ](#t3-2)
	3. [2. Identifier chaque matériau ](#t3-3)
	4. [Créer de nouvelles tables ](#t3-4)

<!--FINET-->

<a id='t1'/>

# Qu'est-ce qu'une base de données ?
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Définition 

### <2>

**Base de données** :\
Fichier ou ensemble de fichiers contenant des informations structurées.


De la structuration des données dépendent les possibilités d'exploitation.

<!--
**3 modèles logiques** de structuration des données :

1. Modèles en table
2. Modèle en arbre
3. Modèle en graphe
-->

### <3>

- *Mode de structuration* :

	- **Entité** : prend la forme d'une *table*\
		(*feuille* dans les logiciels de tableur)
	- **Enregistrement** : prend la forme d'une ligne : 
	- **Attribut** ou *champ* : prend la forme d'une colonne

<!--
![](/home/sbiay/illustrations-cours/documents-divers/bdd/table.jpg)


### <4>
-->


- *Formats de fichiers* :

	**CSV** --- *comma separated values*

	- **SQL** --- *Structured query language* (Format professionnel pour la structuration, les requêtes)

<!--


![](/home/sbiay/illustrations-cours/documents-divers/bdd/table.jpg)
-->


<!--

### <5>

- *Mode de structuration* : parent-enfant(s)

- *Format de fichier fréquemment associé* :
	- **XML**
	- **Json**
- *Langage de requête (recherche, modification)* :
	- XML	=> XSLT, Xquery
	- Json	=> Javascript

- Exemple de [fichier XML](https://uncloud.univ-nantes.fr/index.php/s/8aP2QmkLsrYM86b)


### <6>

- *Mode de structuration* : triplet sujet-prédicat-objet
- *Format de fichier fréquemment associé* : **XML-RDF**
- *Langage de requête* : Sparql


![](/home/sbiay/illustrations-cours/documents-divers/bdd/exemple_graphe_1.jpg)


Données en graphe de la BnF


-->


<a id='t1-2'/>

## Avantages et inconvénients du modèle en table 

### <7>

- Simplicité de conception et d'utilisation :skip 

	- Facile à comprendre, structuration de données toujours lisible
		skip
	- Facile à créer, compléter, modifier
		skip
	- Les logiciels de tableur suffisent
		skip
	- Formats de fichiers très partagés
		skip

- Risque majeur : déstructurer ses données

- Pour les projets importants, privilégier le transfert vers un système de type SQL comme [Heurist](https://heurist.huma-num.fr)


<a id='t1-3'/>

## Modéliser son objet 

### <8>


**Modéliser** : opération qui consiste à créer la représentation d'un objet ou d'un système complexe afin de pouvoir l'analyser par des techniques d'ingénierie documentaire.

**Prospective** (ce que je veux pouvoir faire avec ma base) :

- Etablir une cartographie des ponts conservés
- Interroger le corpus par les matériaux
- Interroger le corpus par les personnes (notamment les architectes ou ingénieurs)
- Interroger le corpus par la chronologie
- …


<!--
**Étapes de la modélisation** :

1. *Exploration* : définir l'objet

	- Quel objet ?
	- Quel périmètre d'étude ?
		
		- Quelle chronologie ?
		- Quel espace ?
		- Quelles sources ?


### <9>

2. *Modèle conceptuel* : analyser les éléments constitutifs de l'objet
	
	- Quels éléments ?
	- Quelles relations des éléments entre-eux ?

3. *Prospective* : poser des objectifs
	
	- Conservation
	- Etude : questions que l'on posera à l'objet
	- Valorisation
-->


### <10>

**Image** : [Premier diagramme, *logiciel yEd*](img/bdd-ponts_01-initial.bmp)


Pour aller plus loin sur les diagrammes,
voir [cette page](https://www.lucidchart.com/pages/fr/diagramme-entite-association)


<a id='t1-4'/>

## Le modèle logique et les cardinalités 

### <11>

**Image** : [Diagramme entité-association](img/bdd-ponts_02-cardinalites.bmp)


<!--


<a id='t2'/>

# Relation simple par une clé étrangère
[comment6]: <11> (TITRE1)


<a id='t2-1'/>

## Table des lieux 

### <12>

- Créer une table des **Lieux** où départer les données relatives aux communes et aux départements

- Utiliser le code INSEE comme clé étrangère dans la table **Ponts**


### <13>

1. On copie-colle toutes les données pertinentes dans une feuille brouillon

2. On élimine les doublons

	- Sélectionner toutes les données
	- **Données** > Plus de filtres > Filtre standard
	- Nom de champ : aucun(e)
	- Options : sans doublon

3. On sélectionne le résultat et on le copie colle dans la feuille **Lieux**

	- **Ctrl + Maj + V** : Valeurs seulement


### <14>

La *clé étrangère* de la table **Pont** joue le rôle d'*identifiant* de chaque commune dans la table **Lieux**

- On déplace la colonne contenant le code INSEE à gauche
- On ajoute les en-têtes si besoin
- On contrôle les données

Est-ce satisfaisant ?


### <15>

On a un problème avec :

- Il peut rester des enregistrements où l'INSEE est un numéro département : à corriger
- Des communes particulières comme L'Île-d'Elle ou Sainte-Radégonde-des-Noyers créent des doublons : supprimer les lignes inutiles


### <16>

- Dans la table pont, éliminer les données désormais inutiles

- Créer une fonction de recherche pour afficher la commune et le département :
	
	- Si le code INSEE est bien dans la colonne H, la fonction pour afficher la commune est : `=RECHERCHEV(H2;$Lieux.A:D;2;0)`

Pour copier-coller une formule sans modifier la couleur de fond de la cellule : clic droit > Collage spécial > Formule

-->


<a id='t3'/>

# Relation multiple par une table de relation
[comment8]: <16> (TITRE1)


<a id='t3-1'/>

## Table des matériaux 

### <17>


[comment10]: <17> (**Passons aux matériaux** : ils sont regroupés dans un seul champ --C--, mais on voit que les valeurs sont multiples.)

[comment11]: <17> (Tous les ponts de ces exemples sont constitués de plusieurs matériaux. Est-ce un problème de les organiser ainsi ? Cela permet de trouver l'information, mais si l'on veut porter une attention particulière aux matériaux dans notre corpus, si on a pour objectif de permettre de trier des résultats de notre base par facettes selon les matériaux, alors il faut leur donner une table séparée.)

[comment12]: <17> (Maintenant, comment mettre en relation plusieurs ponts avec plusieurs matériaux ?)

[comment13]: <17> (Il sera nécessaire de créer une **table de relation**.)

Commencer par isoler les données dans une nouvelle feuille brouillon :

1. Filtrer la colonne **materiau_du_gros_oeuvre** pour ne pas avoir de donnée vide

2. Copier dans une nouvelle feuille brouillon :

- identifiant
- materiau_du_gros_oeuvre


### <18>

Pour créer la relation multiple entre pont et matériaux, il faut procéder en trois étapes :

1. Transformer les données pour parvenir à des **relations 1-1** : 1 identifiant de pont pour 1 matériau

2. Créer un **identifiant** pour chaque matériau

3. Créer la **table** des matériaux


<a id='t3-2'/>

## 1. Transformer les données 

### <19>

Pour avoir sur chaque ligne un identifiant et un seul matériau,\
on fait appel aux expressions régulières

- Copier toutes les données (sans les en-têtes) dans Notepad++

- On veut remplacer chaque point-virgule par l'identifiant du début de la ligne

- Find : `([IP]A\d+)(\t[^;\r]+);\s?`\
	**NB** : ne pas copier-coller le signe `^` dans Notepad++ ; il faut le retaper à la main.

- Replace with : `$1$2\r\n$1\t`


### <20>

- Vérifier la propreté du résultat (nettoyer à la main si besoin)
- Il y a des espaces invisibles en fin de ligne

	- Find : `\s\r`
	- Replace All : `\r`


<a id='t3-3'/>

## 2. Identifier chaque matériau 

### <21>

La feuille obtenue est une **table de relations** ; on la renomme : `Relation matérialité`

À présent, on souhaite créer le thésaurus des matériaux, qui ne devra contenir aucun doublon et où chaque matériau aura son identifiant.

On doit donc trouver une méthode pour créer des identifiants


### <22>

- Trier la colonne des matériaux
- Dans une nouvelle colonne **id matériau** inscrire la première valeur pour le premier matériau : `1`

- Pour générer l'identifiant de l'enregistrement suivant j'écris la formule : `=SI(B3=B2;C2;C2+1)`


### <23>

- Renommer la colonne A : `id Pont`
- Insérer une nouvelle colonne en B
- Y copier-coller le contenu de la colonne **id matériau** pour transformer les formules en valeurs (copier-coller avec un **Ctrl + Maj + V** et cliquer sur valeurs seulement)
- Supprimer la colonne D


### <24>

- Dans une nouvelle feuille, copier-coller tous les matériaux avec leurs identifiants
- Supprimer les doublons

	- Sélectionner toutes les données
	- **Données** > Plus de filtres > Filtre standard
	- Nom de champ : aucun(e)
	- Options : sans doublon

- Copier le résultat dans une nouvelle feuille à nommer : `Matériaux`

- Remplacer la colonne C de la feuille **Relation matérialité** par une formule RECHERCHEV permettant d'afficher le matériau selon son identifiant


### <25>


Félicitations !!!

Vous êtes devenus de véritables ingénieurs de la donnée patrimoniale !

Et avez d'ores-et-déjà obtenu **15 points** pour l'évaluation !


<a id='t3-4'/>

## Créer de nouvelles tables 

### <26>

- Filtrer les données pour les limiter au département de la **Sarthe**

- Pour avoir 17/20 : créer une table spécifique pour les **Personnes** :
	
	- *Attention* : la même personne a pu intervenir sur plusieurs ponts, c'est donc une relation multiple, comme les matériaux
	
	- *Conseil* : travailler à la main sera plus efficace qu'avec des expressions régulières

- Pour avoir 20/20 : créer une table pour les **Datations**


### <27>


Vous pouvez me poser des questions à tout moment si vous avez un doute sur la marche à suivre.

Il faut me remettre les fichiers le 3 novembre au plus tard.