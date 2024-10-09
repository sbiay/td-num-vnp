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
	1. [Les fonctions ](#t1-1)
	2. [Comparer des jeux de données ](#t1-2)
	3. [Récupérer les données de l'API POP ](#t1-3)

[comment]: <> (FINET)


<a id='t1'/>

# Comparer deux tableaux de données
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Les fonctions 

### <2>

On a obtenu via les API plusieurs fichiers de données tabulaires :

1. Données de l'Inventaire extraites de Gertrude
2. Données de Mérimée :

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


### <4>

Les tableurs ne sont pas seulement un mode de présentation des données, ils sont aussi des outils de calcul.

Pour cela, on utilise des **Fonctions**.

La fonction la plus simple qui soit consiste à citer une autre case :

- Se placer dans la case X2
- Saisir : `=C2`

Dans la case X2 s'affiche désormais le contenu de la case C2, qui est l'**appellation** de notre enregistrement.


### <5>

Si je copie une case contenant une fonction, le tableur recalcule automatiquement la formule.

- Copier la case X2 et la coller en X3

La fonction recalculée présente le contenu de la case A3 Je peux ainsi créer une formule dans la première ligne d'une colonne et l'appliquer à toute la colonne par un simple copier-coller.


### <6>

Passons à un calcul un peu plus subtil : une **condition**

Dans la case X2 écrire : `=SI(C2="pont";"pont";"pas pont")`

La formule se décompose ainsi :

- Un type de fonction : **SI**
- Plusieurs clauses (entre parenthèses et séparées par des points-virgules)
	- La condition à tester : `C2="pont"` *la case C2 est égale à la chaîne de caractère `pont`*
	- Si oui, alors le résultat est : "pont"
	- Si non, alors le résultat est : "pas pont"

Appliquer cette formule à toute la colonne (pour sélectionner toutes les cases de la X3 jusqu'en bas : Ctrl + Maj + Fin)


### <7>

**Afficher des valeurs logiques**

Ce résultat ne fait pas très scientifique, mieux vaudrait exprimer les résultats de façon booléenne…

Comment coder VRAI et FAUX en langage booléen ?

Réécrire la fonction et l'appliquer à toutes les lignes de la colonne X


### <8>

La réponse était : `=SI(C2="pont";1;0)`

Mais le résultat n'exprime pas encore des valeurs logiques : il n'affiche que des 0 et des 1

Il faut définir le format de données comme étant des valeurs booléennes :

- Sélectionner toutes les cellules de la colonne
- Cliquer droit > Formater des cellules
- Catégorie : Valeur logique

Désormais, si la colonne C contient strictement le mot "pont", la colonne X dit VRAI, sinon elle dit FAUX


<a id='t1-2'/>

## Comparer des jeux de données 

### <9>

Maintenant que vous connaissez le principe des fonctions et des conditions, revenons à notre objectif : tester si oui ou non l'identifiant (colonne A) de chaque enregistrement de la feuille Gertrude existe dans la feuille Mérimée (colonne A également).

Dans les formules de cette colonne, à la place de `C2="pont"`, il faut écrire une condition bien différente.

Dans la case X2, au lieu d'une simple condition, nous allons écrire une fonction de **recherche**.


### <10>

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


### <11>

`#N/D` signifie *no data* ou "valeur non disponible".
Ce n'est pas une erreur, cela signifie : l'identifiant que vous cherchez n'est pas dans la matrice de recherche --- il n'est pas dans la feuille Mérimée.

- Appliquer la formule à toute la colonne

Certains identifiants sont trouvés ! Combien ?\
En créant un auto-filtre sur la colonne, vous pourrez manipuler les résultats et les compter facilement.


### <12>

La réponse est 20.

On constate donc que sur les 112 résultats de Mérimée, seuls 20 sont dans l'Inventaire du patrimoine tel qu'exposé sur le site Gertrude et tel qu'on a pu le récupérer grâce à l'API.

**NB** Remplacer les résultats de recherche par des valeurs booléennes (si l'identifiant est trouvé, alors 1, sinon 0) est assez compliqué et ce n'est pas utile de l'apprendre

Mais c'est possible : `=SI(SINA(RECHERCHEV(A2;$Mérimée.A:A;1;0);0)=0;0;1)`


<a id='t1-3'/>

## Récupérer les données de l'API POP 

### <13>

Ayant appris qu'il existe peu de recoupements entre les notices des Mérimée et de Gertrude, il devient indispensable à notre corpus d'obtenir des données complètes de Mérimée…

En cherchant bien, on trouve une API qui contient toutes les notices de Mérimée.
En voici un exemple : [https://api.pop.culture.gouv.fr/merimee/PA00109550](https://api.pop.culture.gouv.fr/merimee/PA00109550)


### <14>

Nous avons la liste des identifiants et le modèle des URL des notices dans l'API… Pour récupérer les données de toutes les notices, quatre solutions :

1. Contacter l'administration du site POP pour leur demander une méthode de requêtage de tous les résultats d'un seul coup…

2. Tout faire à la main (prévoir une cafetière, des bonbons schtroumpf, une série en 4 saisons voire plus, etc.)

3. Apprendre le langage python pour écrire un petit programme

4. Demander à un prof qui connaît le langage python et qui a déjà préparé ce cours de vous extraire les données

Voici le résultat directement importé dans un [fichier .odt](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-2.ods)

<!--Pour la suite du cours : ils doivent évaluer les données de Mérimée, comprendre pourquoi il y a peu de recoupements ; reprendre fdr à "Recouper les données entre Mérimée et Gertrude"-->