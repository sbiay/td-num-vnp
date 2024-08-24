---
mainfont: Alegreya
title: Modéliser et récolter
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Modéliser et récolter
=====

Plan :

1. [Modéliser un objet d'étude](#t1)
	1. [Qu'est-ce que modéliser ? ](#t1-1)
	2. [Exploration ](#t1-2)
	3. [Modèle conceptuel : vocabulaire ](#t1-3)
	4. [Prospective ](#t1-4)
2. [Récolter les données](#t2)
	1. [Consulter les sites web ](#t2-1)
	2. [Mérimée : à vous de jouer ! ](#t2-2)

[comment]: <> (FINET)


<a id='t1'/>

# Modéliser un objet d'étude
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Qu'est-ce que modéliser ? 

### <2>

**Modéliser** : opération qui consiste à créer la représentation d'un objet ou d'un système complexe afin de pouvoir l'analyser par des techniques d'ingénierie documentaire.

*Étapes de la modélisation* :

1. **Exploration** : définir l'objet

	- Quel objet ?
	- Quel périmètre d'étude ?
		
		- Quelle chronologie ?
		- Quel espace ?
		- Quelles sources ?


### <3>

2. **Modèle conceptuel** : analyser les éléments constitutifs de l'objet
	
	- Quels éléments ?
	- Quelles relations des éléments entre eux ?

3. **Prospective** : poser des objectifs
	
	- Conservation
	- Etude : questions que l'on posera à l'objet
	- Valorisation


<a id='t1-2'/>

## Exploration 

### <4>

Le pont le plus anciennement attesté en Pays de la Loire :\
le Grand Pont d'Angers (Grégoire de Tours, 590).


**Image** : [Angiers fait della main du capite Ercules conte de Senfront, v. 1590, Archives de l'État de Turin<a date='sans'/>](img/img_0e1c4490-d6ab-4c9b-bd2a-a5929150ce1c.jpg)


### <5>

Un des ponts les plus anciens conservés en Pays de la Loire :

[comment4]: <5> (Il n'est pas du tout certain que la voie romaine Chartres-Le Mans traversait l'Huisne à cet emplacement ; c'est au Moyen Âge que cet axe devient important pour relier Le Mans et Paris.)

**Image** : [Le pont dit Romain de Montfort-le-Gesnois, 1^re^ moitié XV^e^ s.](img/img_10e0aa33-b8e9-4731-995e-83897f815155.jpg)


### <6>

**Image** : [Vieux Pont de Laval, XV^e^ s.](img/img_laval.jpg)


### <7>

Et en Loire-Atlantique…

**Image** : [Pont de la Chalandière dit aussi de l'Arche, Thouaré-sur-Loire, Moyen Âge ?](img/img_5528c7dc-9f45-4974-b5c0-bbc262a1f347.jpg)


### <8>


Jusqu'aux **ouvrages d'art** les plus récents…


**Image** : [Construction du pont de Cheviré, Nantes, achevé en 1990](img/img_985b86c3-fa3a-4538-a4da-2adc8c33c00b.jpeg)

**Image** : [Vu depuis le terminal à bois vers les quais de la Roche-Maurice](img/img_ef409199-d761-464b-ac02-eb7a7b37e80b.jpeg)


### <9>

1. Site de l'Inventaire général des Pays de la Loire

	- [Notice 1](https://gertrude.paysdelaloire.fr/dossier/IA49000842)
	- [Notice 2](https://gertrude.paysdelaloire.fr/dossier/IA85001933)

2. Base Mérimée

	- [Notice 3](https://pop.culture.gouv.fr/notice/merimee/IA49000843)

**Questions :**

- Quelles sont les informations essentielles qui permettront de caractériser un pont ?
- Quels sont les concepts principaux qui vont graviter autour ? Quelles informations vont les caractériser à leur tour ?

[comment5]: <9> (Remarque : un pont est-il une architecture ou un point --immatériel-- de franchissement ?)
[comment6]: <9> (- architecture : base orientée objet ; comme il n'y aura jamais qu'une seule architecture conservée en place --sauf à faire du phasage archéologique complexe--, chaque point de franchissement correspondra à une architecture)
[comment7]: <9> (- point de franchissement : on peut en avoir sans architecture, avec par exemple une mention textuelle)

[comment8]: <9> (Il faut donc se demander ce qui est le plus important pour nous.)

[comment9]: <9> (Revenons à l'idée du phasage : le cas du Grand Pont d'Angers est intéressant. On peut rattacher à chaque entité *pont* des entités *phases*, qui se distinguent par la date, les matériaux, les sources qui s'y rattachent --icono par exemple--. On voit que le site de l'inventaire comme la base POP --uniquement l'API-- font plus simple : rassembler toutes les données de phase et d'histoire dans une seule notice : l'utilisateur interprétera lui-même l'information « Haut Moyen Âge » en lisant l'ensemble de la notice.)


<a id='t1-3'/>

## Modèle conceptuel : vocabulaire 

### <10>

- **Entité** : type d'objet pouvant être décrits par une même liste fermée d'attribut
	- Egalement dénommé : classe, *record type*
	- Exemples : pont, personne, localité, source iconographique, source bibliographique, source archivistique, etc.

- **Attribut** : caractéristique d'une entité permettant de distinguer des enregistrements
	
	- Egalement dénommé : champ, *field*
	- Exemples : 
		- Pour une entité *personne* : nom, prénom, date de naissance, etc.

- **Enregistrement** : élément singulier appartenant à une entité

	- Egalement dénommé : *record*


<a id='t1-4'/>

## Prospective 

### <11>

- Etablir une cartographie des ponts conservés
- Réunir de la documentation iconographique sur les ponts disparus
- Interroger le corpus par les intervenants
- Interroger le corpus par la chronologie


<a id='t2'/>

# Récolter les données
[comment12]: <11> (TITRE1)

[comment13]: <11> (L'un des enjeux majeurs de ce TD est de vous apprendre à récolter le plus de données possibles de manière automatisée, plutôt que de faire 10 000 copier-coller.)


<a id='t2-1'/>

## Consulter les sites web 

### <12>

- Quels sont les sites me permettant d'accéder à de l'information sur le sujet ?
- Quelles informations me donnent-ils ?
	- Couverture du sujet
	- Quantité de données
	- Qualité des données
- Comment récolter leurs données pour les exploiter ?


### <13>

Un article [Liste des ponts de France](https://fr.wikipedia.org/wiki/Liste_de_ponts_de_France)

- Vieux Pont de Laval ? *absent*
- Pont sur l'Huisne à Montfort-le-Gesnois ? *absent*
- Pont de Cheviré ? *absent*

Des données beaucoup trop lacunaires pour être utiles !


### <14>

[https://pop.culture.gouv.fr/](https://pop.culture.gouv.fr/)

\vskip 3em

- Collections des musées de France : la base Joconde

- Patrimoine mobilier : la base Palissy

- Photographies : la base Mémoire

- Patrimoine architectural : la base [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)

- Etc.


<a id='t2-2'/>

## Mérimée : à vous de jouer ! 

### <15>

1. Avant de commencer, lire le [bref descriptif](https://www.culture.gouv.fr/espace-documentation/Bases-de-donnees/Fiches-bases-de-donnees/Merimee-une-base-de-donnees-du-patrimoine-monumental-francais-de-la-Prehistoire-a-nos-jours) de la base et de ce qu'elle contient

	- Le domaine **Monuments historiques** (national) : notices PA
	- Le domaine **Inventaire général** des services régionaux : notices IA

2. Chercher tous les ponts de la région Pays de la Loire sur [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)

	- Il faut aboutir à une liste de [112 résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D)


### <16>

**Méthode à suivre** :

- Par une recherche simple, trouver n'importe quelle notice de pont

- Identifier les champs pertinents pour croiser le type de monument cherché et la localisation

- Examiner le menu déroulant des champs interrogeables en recheche avancée : les premiers sont multiples, puis ce sont des champs simples classés par ordre alpahbétique de leurs abréviations

- La recherche la plus pertinente pour le type : **dénomination --DENO--** *contient* « pont »

- La recherche la plus pertinente pour la localisation : **région --REG--** *égal à* « Pays de la Loire »


