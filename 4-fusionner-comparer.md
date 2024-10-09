---
mainfont: Alegreya
title: Fusionner et comparer des données tabulaires
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Fusionner et comparer des données tabulaires
=====

Plan :

1. [Comparer deux tableaux de données](#t1)
	1. [Fonction de recherche ](#t1-1)
	2. [Comparer des jeux de données ](#t1-2)
	3. [Evaluer la qualité respective des données ](#t1-3)
2. [Fusionner deux tableaux](#t2)
	1. [Comparer les en-têtes et adapter le tableau Fusion ](#t2-1)
3. [Analyser les données](#t3)
	1. [Chercher les problèmes, comprendre les données ](#t3-1)

[comment]: <> (FINET)


<a id='t1'/>

# Comparer deux tableaux de données
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Fonction de recherche 

### <2>

On a obtenu via les API plusieurs fichiers de données tabulaires :

1. Données de l'Inventaire extraites de Gertrude
2. Données de Mérimée\
	(API complète [https://api.pop.culture.gouv.fr/merimee/](https://api.pop.culture.gouv.fr/merimee/PA00109550)) :

	- PA : protection au titre des MH
	- IA : Inventaire (compétence nationale jusqu'en 2004)

Le tout est rassemblée dans un tableau : [étape 1](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-1.ods)

On va évaluer la complémentarité des deux tableaux.


### <3>

Pour comparer les deux feuilles, on doit créer une fonction de **Recherche** :

- Dans la dernière colonne disponible (normalement X) créer l'en-tête : `Mérimée`
- Nous voulons que cette colonne nous renseigne de la façon suivante :
	
	
	*Est-ce que l'identifiant (colonne A) de cet enregistrement existe dans la table Mérimée, oui ou non ?*
	

C'est une information qu'il faut *calculer*.


<a id='t1-2'/>

## Comparer des jeux de données 

### <4>

Dans X2, écrire : `=RECHERCHEV(A2;$Mérimée.A:C;1;0)`

La formule se décompose ainsi :

- Un type de fonction : **RECHERCHEV** qui recherche ***v***erticalement dans un groupe de colonnes
- Plusieurs clauses (entre parenthèses et séparées par des ;) :
	- Le critère de recherche : `A2` *car on cherche si l'identifiant de la colonne A sera dans la feuille Mérimée*
	- La matrice (ou groupe de colonne où chercher) : `$Mérimée.A:C` *qui signifie chercher dans la feuille nommée Mérimée, dans les colonnes de A à C*
	- L'indice : `1` *car c'est dans la 1^re^ colonne de la matrice que se trouve l'identifiant*
	- Recherche dans une plage triée : `0` *pour FAUX (faites-moi confiance !)*

\vskip -0,5em

Votre résultat est sans doute : `#N/D` et c'est normal !


### <5>

`#N/D` signifie *no data* ou "valeur non disponible".
Ce n'est pas une erreur, cela signifie : l'identifiant que vous cherchez n'est pas dans la matrice de recherche --- il n'est pas dans la feuille Mérimée.

- Appliquer la formule à toute la colonne

Certains identifiants sont trouvés ! Combien ?\
En créant un auto-filtre sur la colonne, vous pourrez manipuler les résultats et les compter facilement.


### <6>

La réponse est 20.

On constate donc que sur les 112 résultats de Mérimée, seuls 20 sont dans l'Inventaire du patrimoine tel qu'exposé sur le site Gertrude et tel qu'on a pu le récupérer grâce à l'API.

**NB** Remplacer les résultats de recherche par des valeurs booléennes (si l'identifiant est trouvé, alors 1, sinon 0) est assez compliqué et ce n'est pas utile de l'apprendre

Mais c'est possible : `=SI(SINA(RECHERCHEV(A2;$Mérimée.A:A;1;0);0)=0;0;1)`


<a id='t1-3'/>

## Evaluer la qualité respective des données 

### <7>

Lorsque les deux bases contiennent une notice sous le même identifiant, laquelle est la meilleure ?

Il faut parcourir les données en procédant à des sondages :

- Ouvrir un nouveau tableau pour comparer deux enregistrements
- Choisir un identifiant
- Copier l'ensemble de la ligne dans le nouveau tableau :
	
	- Clic droit
	- **Collage spécial** : transposer


### <8>

On en déduit que les données de Mérimée sont plus complètes pour les matériaux et pour la chronologie.

On sait que les données de Gertrude contiennent un plus grand nombre de notices.

Il est donc intéressant pour notre corpus de chercher à fusionner ces données.


<a id='t2'/>

# Fusionner deux tableaux
[comment5]: <8> (TITRE1)


<a id='t2-1'/>

## Comparer les en-têtes et adapter le tableau Fusion 

### <9>

- Créer une nouvelle feuille que l'on peut appeler "Fusion"

- Y coller tout le contenu de la feuille Gertrude

- Dans un nouveau tableau servant de brouillon comparer les en-têtes de la feuille Gertrude et de la feuille Mérimée

- Quelles différences ? Que faut-il faire ?


### <10>

Creér une nouvelle colonne est simple par un clic droit
	
- **G** : `datation/3`


### <11>

**Déplacer une colonne (ou une ligne)** :

Dans la feuille Fusion On veut :

- **K** : `localisation/lat`
- **L** : `localisation/lon`

Démarche :

1. Cliquer sur l'en-tête de la colonne (B par exemple).
2. Appuyer sur Alt et maintenir
3. Cliquer gaucher sur une cellule de cette colonne et maintenir le clic gauche.
4. Déplacer vers la destination le curseur (colonne H par exemple)


### <12>

On ajoute une colonne **Source** ou l'on renseignera soit `Gertrude` soit `Mérimée`

Il est intéressant de conserver les couleurs pour la comparaison des notices.


### <13>

Félicitations !!!

Vous avez correctement fusionné deux tableaux !

Pour retrouver le résultat : [étape 2](https://github.com/sbiay/td-num-vnp/raw/refs/heads/main/tableurs/inventaire-pays-loire-complet-etape-2.ods)


<a id='t3'/>

# Analyser les données
[comment7]: <13> (TITRE1)


<a id='t3-1'/>

## Chercher les problèmes, comprendre les données 

### <14>

Pour analyser les données, il est utile de les trier selon un double critère :

1. La localisation, via le numéro INSEE
2. L'identifiant, pour rapprocher les notices existant sous le même identifiant dans Gertrude et Mérimée


### <15>

La première notice pose problème ! (IA17047185)

Quelle solution proposez-vous ?


### <16>

Un clic droit sur Google Maps permet d'afficher la commune, mais attention le code est le code postal, non le code INSEE

Le pont ferroviaire (IA17047185) est donc localisé ainsi :

- Commune 1 : L'Île-d'Elle, 85111
- Commune 2 : Marans, 17218


### <17>

Il faut aussi chercher les doublons : l'objectif d'un corpus est d'avoir un seul enregistrement par pont

Parcourir par communes peut être utile, ou encore trier par géolocalisation :

1. Latitude
2. Longitude

Les enregistrements ayant les mêmes coordonnées seront voisins.

Filtrer pour éliminer les ponts ayant en géolocalisation des valeurs 0.


### <18>

Tout naturellement la géolocalisation rapproche les ponts ayant le même identifiant : par exemple IA49000842

On trouve que la notice Mérimée (jaune) est plus riche

On peut créer une nouvelle colonne **Existe avec le même identifiant dans** et insérer la valeur `Gertrude`

Trouvez-vous d'autres doublons qui n'ont pas le même identifiant ?


### <19>

Le pont de Beaulieu à Candé (49)

- IA49001529
- IA49001526

Est-ce le même pont ?

Ou encore le Pont - D 210, Blandouet :

- IA53002314
- IA53002318

Même question…


### <20>

Dans le premier cas les deux ponts existent toujours.

Dans le second l'un a remplacé l'autre.

Il nous appartient de décider si notre corpus conserve ce type de doublon ou les élimine.