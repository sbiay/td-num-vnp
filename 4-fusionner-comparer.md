---
mainfont: Alegreya
title: Fusionner et comparer des données tabulaires
date: 1^er^ semestre 2026-2027
author: sebastien.biay@univ-nantes.fr
---

Fusionner et comparer des données tabulaires
=====

Plan :

	1. [Prise en main de Libre Office Calc ](#t0-1)
1. [Comparer deux feuilles de données](#t1)
	1. [Fonction de recherche ](#t1-1)
	2. [Comparer des jeux de données ](#t1-2)
	3. [Evaluer la qualité respective des données ](#t1-3)
2. [Fusionner deux tableaux](#t2)
	1. [Comparer les en-têtes et préparer le tableau Ponts ](#t2-1)
	2. [Chercher les problèmes, comprendre les données ](#t2-2)

<!--FINET-->


<a id='t0-1'/>

## Prise en main de Libre Office Calc 

### <2>


On a obtenu via les jeux de données ouvertes (*open-data*) plusieurs fichiers de données tabulaires :

1. Données de l'Inventaire extraites de Gertrude (en jaune)

2. Données de Mérimée (en bleu) :

	- PA : Palissy / Mérimée
	- IA : Inventaire

Le tout est rassemblé dans un tableau : [étape 1](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-1.ods) :

- Télécharger le fichier
- L'ouvrir dans LO Calc
- Prendre ses repères dans Libre Office Calc grâce au [tutoriel](https://github.com/sbiay/td-num-vnp/blob/main/tuto-lo-calc.md)
- Dans chaque feuille, sélectionner toutes les données (pas avec Ctrl + A, mais avec **Ctrl + Début** puis **Ctrl + Maj + Fin**)
- Poser les filtres : **Ctrl + Maj + L**


<a id='t1'/>

# Comparer deux feuilles de données
[comment2]: <2> (TITRE1)

<a id='t1-1'/>

## Fonction de recherche 

### <3>

Pour comparer les deux feuilles, on doit créer une fonction de **Recherche** :

- Se placer dans la feuille Gertrude
- Dans la dernière colonne disponible (`CR`) créer l'en-tête : `Gertrude`
- Nous voulons que cette colonne nous renseigne de la façon suivante :
	
	
	*Est-ce que l'identifiant (colonne A) de cet enregistrement existe dans la table Gertrude, oui ou non ?*
	

C'est une information qu'il faut *calculer*.


<a id='t1-2'/>

## Comparer des jeux de données 

### <4>


Dans X2, écrire : `=RECHERCHEV(A2;$Gertrude.A:A;1;0)`

La formule se décompose ainsi :

- Un type de fonction : **RECHERCHEV** qui recherche ***V***erticalement dans un groupe de colonnes
- Plusieurs clauses (entre parenthèses et séparées par des ;) :
	- Le critère de recherche : `A2` *car on cherche si l'identifiant de la colonne A sera dans la feuille Gertrude*
	- La matrice (ou groupe de colonnes où chercher) : `$Gertrude.A:A` *qui signifie chercher dans la feuille nommée Gertrude, dans la colonne A*
	- L'indice : `1` *car c'est dans la 1^re^ (et unique) colonne de la matrice que se trouve l'identifiant*
	- Recherche dans une plage triée : `0` *pour FAUX (faites-moi confiance !)*


Votre résultat est sans doute : `#N/D`. 
Est-ce normal ?


### <5>


`#N/D` signifie *no data* ou « valeur non disponible ».
Ce n'est pas une erreur, cela signifie : l'identifiant que vous cherchez n'est pas dans la matrice de recherche --- il n'est pas dans la 1^re^ colonne de la feuille Mérimée.

Appliquer la formule à toute la colonne :

- Se placer en X2 > **Ctrl + C**
- Se placer en X3 > Maintenir sur **Maj**
- Utiliser les flèches haut/bas pour sélectionner toutes les cases jusqu'en bas des données
- **Ctrl + V**

Certains identifiants sont trouvés ! Combien ? En créant un auto-filtre sur la colonne (Ctrl + Maj + L), vous pourrez manipuler les résultats et les compter facilement.


### <6>

La réponse est 20.

On constate donc que, sur les 108 items de Mérimée, seuls 20 sont dans l'Inventaire du patrimoine tel qu'exposé sur le site Gertrude et tel qu'on a pu le récupérer grâce à l'API.

<span info="coupure">

**NB** : remplacer les résultats de recherche par des valeurs booléennes (si l'identifiant est trouvé, alors 1, sinon 0) est assez compliqué et ce n'est pas utile de l'apprendre

Mais c'est possible : `=SI(SINA(RECHERCHEV(A2;$Gertrude.A:A;1;0);0)=0;0;1)`

</span>


<a id='t1-3'/>

## Evaluer la qualité respective des données 

### <7>

Lorsque les deux bases contiennent une notice sous le même identifiant, laquelle est la meilleure ?

<span info="coupure">

Les données de **Mérimée** sont plus complètes pour les *matériaux*, pour la *chronologie*, pour l'*état de la construction*.

On sait que les données de **Gertrude** contiennent un *plus grand nombre de notices*. Elles sont *signées* par un chercheur de l'inventaire (textes identiques non signés dans Mérimée).

</span>

Est-il intéressant pour notre corpus de fusionner ces données ?


<a id='t2'/>

# Fusionner deux tableaux
[comment6]: <7> (TITRE1)


<a id='t2-1'/>

## Comparer les en-têtes et préparer le tableau Ponts 

### <8>

- Dupliquer la feuille Gertrude (clic droit sur l'onglet en bas de l'écran)

- Renommer la nouvelle feuille `Ponts`

- Dupliquer la feuille Mérimée

- Renommer la première feuille en `Mérimée_brut`

### <9>

Il faut transformer la feuille **Mérimée** pour ordonner les informations de la même façon que dans la feuille **Ponts**


- A : identifiant
- B : nom
- C : appellation
- D : datation/0
- E : datation/1
- F : datation/2
- G : commune
- H : departement
- I : insee
- J : code_departement
- K : localisation/lon
- L : localisation/lat
- M : appartient_a
- N : materiau_du_gros_oeuvre
- O : auteur
- P : historique_du_batiment_ou_de_l_oeuvre
- Q : description_du_batiment
- R : type_de_protection
- S : copyright
- T : chercheur/0
- U : chercheur/1
- V : chercheur/2
- W : chercheur/3


### <10>

Creér une nouvelle colonne est simple par un clic droit
	
- **G** : `datation/3`


### <11>

**Déplacer une colonne (ou une ligne)** :

Dans la feuille Ponts, on veut :

- **L** : `localisation/lat`
- **M** : `localisation/lon`

Démarche :

1. Cliquer sur l'en-tête de la colonne **M**
2. Appuyer sur Alt et maintenir
3. Cliquer gaucher sur une cellule de cette colonne et maintenir le clic gauche.
4. Déplacer le curseur vers la destination


### <12>

- 5 en-têtes propres à Mérimée doivent être ajoutés à la fin de Ponts (de **Y** à **AC**)

- On ajoute une colonne **Source** en **AD** ou l'on renseignera soit `Gertrude` soit `Mérimée`

- Coller le contenu de la feuille Mérimée --- **NB** : Il est intéressant de conserver les couleurs pour la comparaison des notices

- Compléter la colonne **source**


### <13>

Félicitations !!!

Vous avez correctement fusionné deux tableaux et atteint l'étape 2 !

<!--

Pour retrouver le résultat : 

https://github.com/sbiay/td-num-vnp/raw/refs/heads/main/tableurs/inventaire-pays-loire-complet-etape-2.ods

-->


<a id='t2-2'/>

## Chercher les problèmes, comprendre les données 

### <14>

Pour analyser les données, il est utile de les trier selon un double critère :

1. La localisation, via le numéro INSEE
2. L'identifiant, pour rapprocher les notices existant sous le même identifiant dans Gertrude et Mérimée


### <15>

La première notice pose problème ! (IA17047185)

Quelle solution proposez-vous ?


### <16>

Copier-coller les coordonnées de géolocalisation du pont dans Google Maps pour visualiser l'environnement du pont.

Un clic droit sur Google Maps permet d'afficher la commune, mais attention ! le code est le code postal, non le code INSEE.

Le pont ferroviaire (IA17047185) est donc localisé ainsi :

- Commune 1 : L'Île-d'Elle, 85111
- Commune 2 : Marans, 17218

Ajouter des colonnes à Ponts :

- `commune/2` en **K**
- `insee/2` en **L**

Corriger aussi les INSEE erronés pour la ville de Mayenne…


### <17>

**Il faut aussi chercher les doublons** : l'objectif d'un corpus est d'avoir un seul enregistrement par pont

Parcourir par communes peut être utile, ou encore trier par géolocalisation :

1. Latitude
2. Longitude

Les enregistrements ayant les mêmes coordonnées seront voisins.

Filtrer pour éliminer les ponts ayant en géolocalisation des valeurs 0.


### <18>

On trouve des ponts ayant les mêmes coordonnées et le même nom, mais pas le même identifiant…

Le pont de Beaulieu à Candé (49)

- IA49001529
- IA49001526

Est-ce deux fois le même pont ?

Ou encore le Pont - D 210, Blandouet :

- IA53002314
- IA53002318

Même question…


### <19>


1. Les deux ponts sont voisins l'un de l'autre

2. Ils sont situés sur la même route départementale de part et d'autre de la commune

