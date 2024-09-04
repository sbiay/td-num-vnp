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

[comment]: <> (FINET)

```
```


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

Extraire des données d'un PDF est l'une des opérations les plus délicates en ingénierie des données…


<a id='t2-2'/>

## Extraire les données par des expressions régulières 

### <13>

- Ouvrir les PDF dans **Firefox** (d'autres visualiseurs pourraient donner des résultats inégaux)
- Rassembler le contenu des trois PDF dans un seul **éditeur de texte**
- Ouvrir un tableau dans LibreOffice Calc pour recevoir les données
- Examiner les données :
	- Dans quelle mesure sont-elles régulières ou irrégulières ?
	- Quelles sont les irrégularités qui peuvent poser problème ?
	- Sur quelle régularité peut-on s'appuyer pour capturer tout ou partie de l'information ?


### <14>

Irrégularités :

- Les notices n'ont pas toujours le même nombre de lignes !
- Tous les titres ne commencent pas par "pont"


3 régularités à exploiter :

- Les identifiants des notices sont toujours formés de la même manière : 10 caractères commençant par `IA` ou `PA`

- La localisation commence toujours par `Pays de la Loire`

- Le nom de l'édifice est toujours après un numéro d'identifiant ou après des numéros de pages ; mais attention ! c'est l'identifiant de la notice d'avant !

Essayez de composer des expressions pour capturer ces éléments.


### <15>

**Récupérer l'identifiant**

- Ouvrir la boîte de dialogue de recherche (**Ctrl + F**)
- Vérifier que les expressions régulières sont activées : `.*`
- Chercher : `[I|P]A[\d]{8}`
- Sélectionner tout : **Ctrl + Maj + L** (VS Code)
- Fermer la boîte de dialogue de recherche
- Copier la sélection
- Coller dans la première colonne du tableau (on mettra dans la première ligne : `identifiant`)


### <16>

**Récupérer le nom**

- Tester la recherche suivante : `[P|I]A[\d]{8}\n[^\n]+`

	\small
	L'expression signifie : *un identifiant, suivi d'un retour à la ligne, puis d'une ligne avec tous ses caractères (de un à une infinité de caractères sauf un retour à la ligne)*
	

Le résultat est-il satisfaisant ?


### <17>

**Récupérer le nom**

On ne capture pas tous les noms correctement.
Il faut procéder à des nettoyages :

- Eliminer les numéros de pages (ils s'interposent entre des identifiants et des noms)

	- Chercher : `\n\d+ / \d+`
	- Remplacer par : *vide*

- Il faut aussi éliminer les titres des documents PDF qui poseront le même problème :

	`Panier de notices`\
	`50 notices`

- Le faire à la main ou par une expression régulière de votre invention…


### <18>

**Récupérer le nom**

- Ouvrir un second document vide dans l'éditeur de textes

- Chercher : `[P|I]A[\d]{8}\n[^\n]+`

- Coller dans le nouveau document


### <19>

**Récupérer le nom**

- Dans ce nouveau document, on veut éliminer toutes les lignes qui ne sont pas le nom de l'édifice
	- Les identifiants
		- Chercher : `[P|I]A[\d]{8}\n`
		- Remplacer par : *vide*

- Copier toutes les lignes et les coller dans le tableau : **Ctrl + Maj + V**

Le résultat est-il satisfaisant ?


### <20>

**Récupérer le nom**

Le premier nom de la liste n'a pas pu être attrappé par notre méthode !

- Décaler toutes les données de la colonne des noms d'une ligne vers le bas
- Coller à la main le nom du premier enregistrement

[comment8]: <20> (Maintenant il faut récupérer la Localisation)
