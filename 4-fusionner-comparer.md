---
mainfont: Alegreya
title: Fusionner et nettoyer des données tabulaires
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Fusionner et nettoyer des données tabulaires
=====

Plan :

1. [Fusionner des tableaux](#t1)
	1. [Prise en main d'un tableur ](#t1-1)
	2. [Prudence !!! Comparer les en-têtes des tableaux ](#t1-2)
	3. [Fusionner les tableaux ](#t1-3)
2. [Comparer deux tableaux de données](#t2)
	1. [Les fonctions ](#t2-1)
	2. [Comparer des jeux de données ](#t2-2)
	3. [Récupérer les données de l'API POP ](#t2-3)

[comment]: <> (FINET)


<a id='t1'/>

# Fusionner des tableaux
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Prise en main d'un tableur 

### <2>

Quelques trucs et astuces pour manipuler efficacement des données tabulaires

- Ouvrir dans **LibreOffice Calc** votre fichier **inventaire-pays-loire-debut.csv** ([également téléchargeable ici](https://raw.githubusercontent.com/sbiay/td-num-vnp/main/csv/inventaire-pays-loire-debut.csv))
- *Options de séparateur* : **Tabulation** (uniquement)
- *Séparateur de chaînes de caractères* : **`"`**

```
```


### <3>

- La souris ne sert pas à grand chose pour se déplacer dans un tableau : **privilégier les flêches**

	- **Ctrl + flêche** vous renvoie à la dernière case non vide dans la direction de la flêche

- **Pour modifier** le contenu d'une cellule :
	- Se placer sur la cellule
	- Écrire un nouveau contenu
	- Sortir de la cellule (par une touche flêche ou Entrée)
	- **Ctrl + Z** pour annuler une modification malheureuse

- **Pour sélectionner** un groupe de cellule :
	- Se placer sur une première cellule
	- Rester appuyer sur **Maj**
	- Se déplacer avec les flêches jusqu'à la dernière cellule souhaitée


### <4>

- Pour aller tout au début d'une ligne : touche **Début**
- Pour aller tout au bout d'une ligne : touche **Fin**
- Pour aller à la case A1 : **Ctrl + Début**
- Pour aller à la case opposée (dernière ligne et dernière colonne de la partie non vide du tableau) : **Ctrl + Fin**

- **Pour sélectionner** tout le tableau :
	- **Ctrl + Début**
	- Puis maintenir **Ctrl + Maj**
	- Appuyer sur **Fin**


<a id='t1-2'/>

## Prudence !!! Comparer les en-têtes des tableaux 

### <5>

Nous avons exporté les données d'une même API en deux moitiés, mais les données sont-elles faciles fusionner, cela reste à voir !…

- En utilisant les conseils précédents, sélectionner toute la première ligne : **Ctrl + Maj + Flêche de droite**

- La copier : **Ctrl + C**
- Ouvrir un nouveau fichier : **Ctrl + N**
- Coller la ligne dans le nouveau fichier
- Puis coller en dessous la première ligne de l'autre tableau : **inventaire-pays-loire-fin.csv** ([également téléchargeable ici](https://raw.githubusercontent.com/sbiay/td-num-vnp/main/csv/inventaire-pays-loire-fin.csv))

Comparer les deux lignes pour voir si les colonnes des deux tableaux se correspondent…


### <6>

Les données de **datation** et de **chercheur** ne se correspondent pas :

- Les données de "fin" ont jusqu'à trois datations
- Les données de "début" n'ont qu'une seule datation, mais jusqu'à quatre chercheurs

Dans le fichier "fin", commencer par regrouper les colonnes de datation ensemble :

\vskip -0.5em

- A la place de la colonne "commune" (E), **insérer une colonne** (par clic droit)
- Répéter l'opération une autre fois : **Ctrl + Maj + Y**
- A l'aide de **Maj + flêche**, sélectionner tout le contenu des champs "datation/1" et "datation/2"
- Le couper : **Ctrl + X**
- Le coller dans la colonne E (nouvelle colonne vide de gauche)


### <7>

Pour une stricte correpondance des tableaux, il faut à présent créer des colonnes vides dans **inventaire-pays-loire-debut.csv** :

- E : datation/1
- F : datation/2

Dans ce même tableau on veut maintenant regrouper les différents champs "chercheur" :

- Insérer une colonne à la place de la colonne S
- Y déplacer toute la colonne "copyright"
- Supprimer la colonne U


### <8>

Dans le fichier **inventaire-pays-loire-fin.csv**,
il faut aussi : 

- Inverser "chercheur/0" et "copyright"
- Copier les en-têtes :
	- U : chercheur/1
	- V : chercheur/2
	- W : chercheur/3

En principe, tout est OK !

Mais il vaut mieux vérifier en comparant à nouveau les deux lignes d'en-têtes dans un tableau à part.
Se correspondent-elles parfaitement ?

Alors c'est parti pour fusionner les deux tableaux !


<a id='t1-3'/>

## Fusionner les tableaux 

### <9>

On crée un nouveau document (**Ctrl + N**) et on l'enregistre ainsi :

`prenom-nom/`

=> `tableurs/`

=> => `inventaire-pays-loire-complet.ods`\


### <10>

Pour copier l'intégralité du premier fichier CSV :

- **Ctrl + Début**
- Tenir la touche **Maj**
- **Ctrl + Fin**
- Copier et coller dans le nouveau fichier

Attention ! Lorsque l'on copie le second fichier, on ne copie pas à nouveau la ligne d'en-têtes…


### <11>

Félicitations !

Vous avez reconstitué l'inventaire complet de manière parfaitement structurée !

On aboutit à l'[étape 1](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-1.ods)


<a id='t2'/>

# Comparer deux tableaux de données
[comment5]: <11> (TITRE1)


<a id='t2-1'/>

## Les fonctions 

### <12>

Nous avons récupéré des données très incomplètes de la base **Mérimée**.
Cependant, elles nous permettent de confronter les notices de cette base avec celles que nous avons extraites de **Gertrude**.

Pour cela, nous allons rassembler les données dans un même document **.ods** et croiser leurs identifiants, afin de déterminer si les deux bases contiennent les mêmes notices.


### <13>

- Ouvrir le fichier **inventaire-pays-loire-complet.ods**
- Renommer la feuille unique (par un clic droit) et l'appeler, par exemple, "Gertrude"
- En cliquant droit dans la même zone : **Insérer une nouvelle feuille** et la nommer "Mérimée"
- Y coller toutes les données du tableau que l'on vient de construire ([ce fichier](https://github.com/sbiay/td-num-vnp/raw/main/csv/merimee-export-manuel.csv))


### <14>

Pour comparer les deux feuilles, on doit créer une fonction de **Recherche** dans la feuille Gertrude :

- Dans la dernière colonne disponible (normalement X) créer l'en-tête : `Mérimée`
- Nous voulons que cette colonne nous renseigne de la façon suivante :
	
	
	*Est-ce que l'identifiant (colonne A) de cet enregistrement existe dans la table Mérimée, oui ou non ?*
	

C'est une information qu'il faut *calculer*.


### <15>

Les tableurs ne sont pas seulement un mode de présentation des données, ils sont aussi des outils de calcul.

Pour cela, on utilise des **Fonctions**.

La fonction la plus simple qui soit consiste à citer une autre case :

- Se placer dans la case X2
- Saisir : `=C2`

Dans la case X2 s'affiche désormais le contenu de la case C2, qui est l'**appellation** de notre enregistrement.


### <16>

Si je copie une case contenant une fonction, le tableur recalcule automatiquement la formule.

- Copier la case X2 et la coller en X3

La fonction recalculée présente le contenu de la case A3
Je peux ainsi créer une formule dans la première ligne d'une colonne et l'appliquer à toute la colonne par un simple copier-coller.


### <17>

Passons à un calcul un peu plus subtil : une **condition**

Dans la case X2 écrire : `=SI(C2="pont";"pont";"pas pont")`

La formule se décompose ainsi :

- Un type de fonction : **SI**
- Plusieurs clauses (entre parenthèses et séparées par des points-virgules)
	- La condition à tester : `C2="pont"` *la case C2 est égale à la chaîne de caractère `pont`*
	- Si oui, alors le résultat est : "pont"
	- Si non, alors le résultat est : "pas pont"

Appliquer cette formule à toute la colonne (pour sélectionner toutes les cases de la X3 jusqu'en bas : Ctrl + Maj + Fin)


### <18>

**Afficher des valeurs logiques**

Ce résultat ne fait pas très scientifique, mieux vaudrait exprimer les résultats de façon booléenne…

Comment coder VRAI et FAUX en langage booléen ?

Réécrire la fonction et l'appliquer à toutes les lignes de la colonne X


### <19>

La réponse était : `=SI(C2="pont";1;0)`

Mais le résultat n'exprime pas encore des valeurs logiques : il n'affiche que des 0 et des 1

Il faut définir le format de données comme étant des valeurs booléennes :

- Sélectionner toutes les cellules de la colonne
- Cliquer droit > Formater des cellules
- Catégorie : Valeur logique

Désormais, si la colonne C contient strictement le mot "pont", la colonne X dit VRAI, sinon elle dit FAUX


<a id='t2-2'/>

## Comparer des jeux de données 

### <20>

Maintenant que vous connaissez le principe des fonctions et des conditions, revenons à notre objectif : tester si oui ou non l'identifiant (colonne A) de chaque enregistrement de la feuille Gertrude existe dans la feuille Mérimée (colonne A également).

Dans les formules de cette colonne, à la place de `C2="pont"`, il faut écrire une condition bien différente.

Dans la case X2, au lieu d'une simple condition, nous allons écrire une fonction de **recherche**.


### <21>

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


### <22>

`#N/D` signifie *no data* ou "valeur non disponible".
Ce n'est pas une erreur, cela signifie : l'identifiant que vous cherchez n'est pas dans la matrice de recherche --- il n'est pas dans la feuille Mérimée.

- Appliquer la formule à toute la colonne

Certains identifiants sont trouvés ! Combien ?\
En créant un auto-filtre sur la colonne, vous pourrez manipuler les résultats et les compter facilement.


### <23>

La réponse est 20.

On constate donc que sur les 112 résultats de Mérimée, seuls 20 sont dans l'Inventaire du patrimoine tel qu'exposé sur le site Gertrude et tel qu'on a pu le récupérer grâce à l'API.

**NB** Remplacer les résultats de recherche par des valeurs booléennes (si l'identifiant est trouvé, alors 1, sinon 0) est assez compliqué et ce n'est pas utile de l'apprendre

Mais c'est possible : `=SI(SINA(RECHERCHEV(A2;$Mérimée.A:A;1;0);0)=0;0;1)`


<a id='t2-3'/>

## Récupérer les données de l'API POP 

### <24>

Ayant appris qu'il existe peu de recoupements entre les notices des Mérimée et de Gertrude, il devient indispensable à notre corpus d'obtenir des données complètes de Mérimée…

En cherchant bien, on trouve une API qui contient toutes les notices de Mérimée.
En voici un exemple : [https://api.pop.culture.gouv.fr/merimee/PA00109550](https://api.pop.culture.gouv.fr/merimee/PA00109550)


### <25>

Nous avons la liste des identifiants et le modèle des URL des notices dans l'API… Pour récupérer les données de toutes les notices, quatre solutions :

1. Contacter l'administration du site POP pour leur demander une méthode de requêtage de tous les résultats d'un seul coup…

2. Tout faire à la main (prévoir une cafetière, des bonbons schtroumpf, une série en 4 saisons voire plus, etc.)

3. Apprendre le langage python pour écrire un petit programme

4. Demander à un prof qui connaît le langage python et qui a déjà préparé ce cours de vous extraire les données

Voici le résultat directement importé dans un [fichier .odt](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-2.ods)

<!--Pour la suite du cours : ils doivent évaluer les données de Mérimée, comprendre pourquoi il y a peu de recoupements ; reprendre fdr à "Recouper les données entre Mérimée et Gertrude"-->