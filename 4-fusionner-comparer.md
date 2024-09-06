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
	1. [Exporter les résultats depuis Mérimée ](#t2-1)
	2. [Extraire les données par des expressions régulières ](#t2-2)
	3. [Les fonctions ](#t2-3)
	4. [Comparer des jeux de données ](#t2-4)
	5. [Récupérer les données de l'API POP ](#t2-5)

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

## Exporter les résultats depuis Mérimée 

### <12>

Les [112 résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D) obtenus de la base Mérimée via le site POP sont toujours un ensemble de PDF…

Vous pouvez les télécharger [ici](https://github.com/sbiay/td-num-vnp/tree/main/pdf)

Il s'agit à présent de convertir tout ou partie du contenu de ces PDF en un unique tableau de données.


<a id='t2-2'/>

## Extraire les données par des expressions régulières 

### <13>

Extraire des données d'un PDF est l'une des opérations les plus délicates en ingénierie des données…

- Ouvrir les PDF dans **Firefox** (d'autres visualiseurs pourraient donner des résultats inégaux)
- Rassembler par copier-coller le contenu des trois PDF dans un seul **éditeur de texte**
- Ouvrir un tableau dans LibreOffice Calc pour recevoir les données
- Y créer les en-têtes sur la première ligne : `identifiant`, `nom`, `localisation`


### <14>

Réfléchissons à la meilleure stratégie pour récupérer les données :

- Dans quelle mesure sont-elles régulières ou irrégulières ?
- Quelles sont les irrégularités qui peuvent poser problème ?
- Sur quelle régularité peut-on s'appuyer pour capturer tout ou partie de l'information ?


### <15>

Irrégularités :

- Les notices n'ont pas toujours le même nombre de lignes !
- Tous les titres ne commencent pas par "pont"


3 régularités à exploiter :

1. Les identifiants des notices sont toujours formés de la même manière : 10 caractères commençant par `IA` ou `PA`

2. La localisation commence toujours par `Pays de la Loire`

3. Le nom de l'édifice est toujours après un numéro d'identifiant ou après des numéros de pages ; mais attention ! c'est l'identifiant de la notice d'avant !

Essayez de composer des expressions régulières pour sélectionner ces éléments.


### <16>

**Récupérer les identifiants**

- Dans l'éditeur de texte, ouvrir la boîte de dialogue de recherche (**Ctrl + F**)
- Vérifier que les expressions régulières sont activées : `.*`
- Chercher : `[I|P]A[\d]{8}`
- Sélectionner tout : **Ctrl + Maj + L** (VS Code)
- Fermer la boîte de dialogue de recherche
- Copier la sélection
- Coller dans la 1^re^ colonne du tableau à partir de la 2^e^ ligne (on mettra en 1^re^ ligne : `identifiant`)


### <17>

**Récupérer le nom**

On sait que les noms se trouvent sur les lignes qui suivent celles des identifiants :

- Tester la recherche suivante : `[P|I]A[\d]{8}\n[^\n]+`

	
	L'expression signifie : *un identifiant, suivi d'un retour à la ligne, puis d'une ligne avec tous ses caractères (de un à une infinité de caractères sauf un retour à la ligne)*
	

Le résultat est-il satisfaisant ?


### <18>

**Récupérer le nom**

On ne capture pas tous les noms correctement.
Il faut procéder à des nettoyages :

- Eliminer les numéros de pages (ils s'interposent entre des identifiants et des noms)

	- Chercher : `\n\d+ / \d+`
	- Remplacer par : *vide*


### <19>

**Récupérer le nom**

Il faut aussi éliminer les titres des documents PDF qui poseront le même problème :

`Panier de notices`\
`50 notices`

- Le faire à la main ou par une expression régulière de votre invention… (le nombre de notices n'est pas de "50" dans la dernière partie du fichier)


### <20>

**Récupérer le nom**

- Ouvrir un second document vide dans l'éditeur de textes

- Chercher : `[P|I]A[\d]{8}\n[^\n]+`

- Coller dans le nouveau document


### <21>

**Récupérer le nom**

- Dans ce nouveau document, on veut éliminer toutes les lignes qui ne sont pas le nom de l'édifice
	- Les identifiants
		- Chercher : `[P|I]A[\d]{8}\n`
		- Remplacer par : *vide*

- Copier toutes les lignes et les coller dans le tableau : **Ctrl + Maj + V**

Le résultat est-il satisfaisant ?


### <22>

**Récupérer le nom**

Le premier nom de la liste n'a pas pu être attrappé par notre méthode !

- Décaler toutes les données de la colonne des noms d'une ligne vers le bas
- Coller à la main le nom du premier enregistrement


### <23>

**Récupérer la localisation**

Ce n'est pas le plus difficile, puisque la localisation commence toujours par "Pays de la Loire".

À vous de composer l'expression régulière pour capturer toute cette ligne et la coller dans le tableau.

L'information "Pays de la Loire" n'étant pas utile pour nous, on peut ensuite l'éliminer de la colonne C du tableau :

- Cliquer sur **C** pour sélectionner toute la colonne
- Ouvrir la boîte de dialogue pour chercher-remplacer : **Ctrl + H**
- Bien cocher : Autres options > Sélection active seulement
- Compléter judicieusement les champs **Rechercher** et **Remplacer**


### <24>

**Félicitations !**

Vous avez extrait les principales données d'un PDF et les avez rendues exploitables en tant que tableau.

Le résultat peut se retrouver dans [ce fichier](https://github.com/sbiay/td-num-vnp/raw/main/csv/merimee-export-manuel.csv)


<a id='t2-3'/>

## Les fonctions 

### <25>

Nous avons récupéré des données très incomplètes de la base **Mérimée**.
Cependant, elles nous permettent de confronter les notices de cette base avec celles que nous avons extraites de **Gertrude**.

Pour cela, nous allons rassembler les données dans un même document **.ods** et croiser leurs identifiants, afin de déterminer si les deux bases contiennent les mêmes notices.


### <26>

- Ouvrir le fichier **inventaire-pays-loire-complet.ods**
- Renommer la feuille unique (par un clic droit) et l'appeler, par exemple, "Gertrude"
- En cliquant droit dans la même zone : **Insérer une nouvelle feuille** et la nommer "Mérimée"
- Y coller toutes les données du tableau que l'on vient de construire ([ce fichier](https://github.com/sbiay/td-num-vnp/raw/main/csv/merimee-export-manuel.csv))


### <27>

Pour comparer les deux feuilles, on doit créer une fonction de **Recherche** dans la feuille Gertrude :

- Dans la dernière colonne disponible (normalement X) créer l'en-tête : `Mérimée`
- Nous voulons que cette colonne nous renseigne de la façon suivante :
	
	
	*Est-ce que l'identifiant (colonne A) de cet enregistrement existe dans la table Mérimée, oui ou non ?*
	

C'est une information qu'il faut *calculer*.


### <28>

Les tableurs ne sont pas seulement un mode de présentation des données, ils sont aussi des outils de calcul.

Pour cela, on utilise des **Fonctions**.

La fonction la plus simple qui soit consiste à citer une autre case :

- Se placer dans la case X2
- Saisir : `=C2`

Dans la case X2 s'affiche désormais le contenu de la case C2, qui est l'**appellation** de notre enregistrement.


### <29>

Si je copie une case contenant une fonction, le tableur recalcule automatiquement la formule.

- Copier la case X2 et la coller en X3

La fonction recalculée présente le contenu de la case A3
Je peux ainsi créer une formule dans la première ligne d'une colonne et l'appliquer à toute la colonne par un simple copier-coller.


### <30>

Passons à un calcul un peu plus subtil : une **condition**

Dans la case X2 écrire : `=SI(C2="pont";"pont";"pas pont")`

La formule se décompose ainsi :

- Un type de fonction : **SI**
- Plusieurs clauses (entre parenthèses et séparées par des points-virgules)
	- La condition à tester : `C2="pont"` *la case C2 est égale à la chaîne de caractère `pont`*
	- Si oui, alors le résultat est : "pont"
	- Si non, alors le résultat est : "pas pont"

Appliquer cette formule à toute la colonne (pour sélectionner toutes les cases de la X3 jusqu'en bas : Ctrl + Maj + Fin)


### <31>

**Afficher des valeurs logiques**

Ce résultat ne fait pas très scientifique, mieux vaudrait exprimer les résultats de façon booléenne…

Comment coder VRAI et FAUX en langage booléen ?

Réécrire la fonction et l'appliquer à toutes les lignes de la colonne X


### <32>

La réponse était : `=SI(C2="pont";1;0)`

Mais le résultat n'exprime pas encore des valeurs logiques : il n'affiche que des 0 et des 1

Il faut définir le format de données comme étant des valeurs booléennes :

- Sélectionner toutes les cellules de la colonne
- Cliquer droit > Formater des cellules
- Catégorie : Valeur logique

Désormais, si la colonne C contient strictement le mot "pont", la colonne X dit VRAI, sinon elle dit FAUX


<a id='t2-4'/>

## Comparer des jeux de données 

### <33>

Maintenant que vous connaissez le principe des fonctions et des conditions, revenons à notre objectif : tester si oui ou non l'identifiant (colonne A) de chaque enregistrement de la feuille Gertrude existe dans la feuille Mérimée (colonne A également).

Dans les formules de cette colonne, à la place de `C2="pont"`, il faut écrire une condition bien différente.

Dans la case X2, au lieu d'une simple condition, nous allons écrire une fonction de **recherche**.


### <34>

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


### <35>

`#N/D` signifie *no data* ou "valeur non disponible".
Ce n'est pas une erreur, cela signifie : l'identifiant que vous cherchez n'est pas dans la matrice de recherche --- il n'est pas dans la feuille Mérimée.

- Appliquer la formule à toute la colonne

Certains identifiants sont trouvés ! Combien ?\
En créant un auto-filtre sur la colonne, vous pourrez manipuler les résultats et les compter facilement.


### <36>

La réponse est 20.

On constate donc que sur les 112 résultats de Mérimée, seuls 20 sont dans l'Inventaire du patrimoine tel qu'exposé sur le site Gertrude et tel qu'on a pu le récupérer grâce à l'API.

**NB** Remplacer les résultats de recherche par des valeurs booléennes (si l'identifiant est trouvé, alors 1, sinon 0) est assez compliqué et ce n'est pas utile de l'apprendre

Mais c'est possible : `=SI(SINA(RECHERCHEV(A2;$Mérimée.A:A;1;0);0)=0;0;1)`


<a id='t2-5'/>

## Récupérer les données de l'API POP 

### <37>

Ayant appris qu'il existe peu de recoupements entre les notices des Mérimée et de Gertrude, il devient indispensable à notre corpus d'obtenir des données complètes de Mérimée…

En cherchant bien, on trouve une API qui contient toutes les notices de Mérimée.
En voici un exemple : [https://api.pop.culture.gouv.fr/merimee/PA00109550](https://api.pop.culture.gouv.fr/merimee/PA00109550)


### <38>

Nous avons la liste des identifiants et le modèle des URL des notices dans l'API… Pour récupérer les données de toutes les notices, quatre solutions :

1. Contacter l'administration du site POP pour leur demander une méthode de requêtage de tous les résultats d'un seul coup…

2. Tout faire à la main (prévoir une cafetière, des bonbons schtroumpf, une série en 4 saisons voire plus, etc.)

3. Apprendre le langage python pour écrire un petit programme

4. Demander à un prof qui connaît le langage python et qui a déjà préparé ce cours de vous extraire les données

Voici le résultat directement importé dans un [fichier .odt](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/inventaire-pays-loire-complet-etape-2.ods)