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