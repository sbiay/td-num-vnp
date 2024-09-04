---
title: Les expressions régulières
---

Plan :

1. [Les ensembles](#t1)
	1. [Les classes de caractères](#t1-1)
	2. [Les raccourcis de classes de caractères](#t1-2)
	3. [Les métacaractères](#t1-3)
2. [Les opérateurs](#t2)
	1. [L'opérateur d'alternative](#t2-1)
	2. [Les quantificateurs](#t2-2)
3. [La capture](#t3)

[comment]: <> (FINET)


**Une expression régulière est une chaîne de caractères qui décrit les ensembles possibles d'une autre chaîne de caractères.**

On peut les utiliser aussi bien pour rechercher des \"motifs\" dans des fichiers texte,
appliquer des transformations dans des cellules de tableurs, valider la conformité d'une donnée ou encore extraire des informations.


<a id='t1'/>

# Les ensembles

Quand on écrit sur un clavier, on peut utiliser un ensemble défini de caractères.
On y trouve les **lettres** minuscules/majuscules, les **chiffres**, les **espaces** ou « caractères blancs » et des caractères **\"spéciaux\"** (`&\"'…`).


<a id='t1-1'/>

## Les classes de caractères

Dans les expressions régulières, un ensemble se représente entre crochets `[]`:

- Les lettres minuscules `[a-z]` ;
- Les lettres majuscules `[A-Z]` ;
- Les chiffres `[0-9]` ;
- Les caractères blanc `[ \t\n]` :
  - `\t` est la manière textuelle de représenter une tabulation ;
  - `\n` est la manière textuelle de représenter un retour à la ligne ;
- Les caractères spéciaux `[&é »'=]` (à compléter en fonction des besoins) ;
- La négation (trouver ce qui n'est pas compris dans mon ensemble)
  `[^a]` (tout ce qui n'est pas un *a*).


Majuscules et minuscules sont deux classes différentes.
Pour avoir l'ensemble des lettres du texte, on doit écrire deux classes à l'intérieur de notre ensemble: `[a-zA-Z]`.

Pour définir un ensemble de lettres qui ne se suivent pas dans l'alphabet, comme les voyelles : `[aeiouy]`.

**Attention !** Les lettres accentuées sont des caractères spéciaux… `[a-zA-Z]` ne les comprend pas.


<a id='t1-2'/>

## Les raccourcis de classes de caractères

Il existe des classes prédéfinies :

- Les lettres + les chiffres + l'*underscore* (`_`) `\w` ;
- Les chiffres `\d` ;
- Les caractères blancs (espaces, tabulations, retours à la ligne) `\s` ;
- N'importe quel caractère `.`.

Chaque raccourci a également son contraire :

- Ce qui n'est ni une lettre ni un chiffre ni un *underscore* `\W` ;
- Ce qui n'est pas un chiffre `\D` ;
- Ce qui n'est pas un caractère blanc `\S`.


<a id='t1-3'/>

## Les métacaractères

Dans certains cas, on peut vouloir détecter des éléments qu'on ne peut pas écrire au clavier, c'est le cas d'un début de ligne, une fin de ligne, mais également d'un début ou une fin de mot.

Pour les détecter avec une regex, il existe ceci :

- Début de ligne : `^` ;
- Fin de ligne : `$` ;
- Début/fin de mot : `\b`.

Pour comprendre l'utilisation de ces caractères, voici des exemples :

- Si on veut récupérer le premier mot de chaque ligne: `^\w+` ;
- Si on veut récupérer le dernier mot de chaque ligne: `\w+$` ;
- Si on veut récupérer le mot *bon* :
  - en utilisant juste `bon`, on obtiendrait tous les mots de notre fichier comprenant ces trois lettres consécutivement (*bonjour*, *abonder*, etc.) ;
  - en utilisant `\bbon\b` on obtient le mot seul.


<a id='t2'/>

# Les opérateurs

Dans la partie précédente, on a vu comment chercher des éléments d'un ensemble mais cela fonctionnait caractère par caractère.
Nous allons maintenant voir comment faire pour trouver un mot au lieu d'une succession de caractères.


<a id='t2-1'/>

## L'opérateur d'alternative

Il est possible de dire que l'on veut un caractère **OU** un autre.
Pour cela on va simplement écrire `a|b` qui signifie *\"Je veux seulement les a **ou** les b\"* .


<a id='t2-2'/>

## Les quantificateurs

- 0 ou 1 fois `?`
- 0 ou plusieurs fois `*`
- 1 ou plusieurs fois `+`
- Un nombre défini de fois entre `{}` : `{1,3}` signifie *de 1 à 3 fois*


<a id='t3'/>

# La capture


Dans certains cas, on peut vouloir capturer seulement une partie de l'expression régulière que l'on a écrite.
Par exemple, quand on sait comment une phrase est formée, on peut vouloir récupérer une information précise.

> — Bonjour, je m'appelle Aubin et je vis à Angers.
>
> — Bonjour, je m'appelle Radegonde et je vis à Poitiers.
>
> — Et que fais-tu dans la vie ?

On veut récupérer les prénoms.
On sait que dans ce texte le prénom se trouve après *je m'appelle*

On peut faire dans une nouvelle copie du texte :

- Rechercher `^[^\n]+je m'appelle (\w+)[^\n]+$`. Cette expression se compose ainsi :
  - `^` un début de ligne ;
  - `[^\n]+` plusieurs caractères sauf un retour à la ligne ;
  - `je m'appelle`
  - `(\w+)` : **capture** d'un mot (suite de caractères étant soit des lettres, soit des chiffres soit *underscore*, le tout entre parenthèses pour la capture)
  - `[^\n]+` plusieurs caractères sauf un retour à la ligne ;
  - `$` une fin de ligne.

- On copie la sélection dans un nouveau fichier (qui ne contiendra que les phrases intéressant notre recherche)
- On répète la même recherche : `^[^\n]+je m'appelle (\w+)[^\n]+$`
- Remplacer par : `$1` c'est-à-dire le premier motif capturé entre parenthèses

On a ainsi remplacé 

![Groupe capturant](/media/galleries/12002/b7789dcd-0817-4888-b581-8c3f40e063b6.png)

Le match complet est `je m'appelle Toto` mais on a précisé que la capture intéressante était la partie après \"**je m'appelle**\".


