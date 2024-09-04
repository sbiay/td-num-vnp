---
title: Les expressions régulières
---

Plan :

1. [Les ensembles](#t1)
	1. [Les classes de caractères](#t1-1)
	2. [Les raccourcis de classes de caractères](#t1-2)
	3. [Caractères de regex](#t1-3)
	4. [Caractères unicode](#t1-4)
2. [Les opérateurs]](#t2)
	1. [L'opérateur d'alternative](#t2-1)
	2. [Les opérateurs de quantité](#t2-2)
	3. [Quelques exemples](#t2-3)
3. [Les groupes](#t3)
	1. [Les groupes capturant](#t3-1)
	2. [Les groupes non capturant](#t3-2)
	3. [Les groupes nommés](#t3-3)
	4. [Les groupes spéciaux](#t3-4)

[comment]: <> (FINET)


**Un tutoriel pour comprendre les bases des expressions régulières**


**Une expression régulière est une chaîne de caractères qui décrit les ensembles possible d'une autre chaîne de caractères.**

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

Ainsi on comprend bien que `[a-z]` signifie : *\"Je veux les lettres allant de a à z\"*, ce qu'il ne sera pas possible de faire avec les voyelles puisqu'elles ne se suivent pas, il faudra écrire `[aeiou]`.


<a id='t1-2'/>

## Les raccourcis de classes de caractères

Il existe des classes déjà définies :

- Les lettres + les chiffres + l'*underscore* (`_`) `\w` ;
- Les chiffres `\d` ;
- Les caractères blancs (espaces, tabulations, retours à la ligne) `\s` ;
- N'importe quel caractère `.`.

Chaque raccourci a également son contraire :

- Ce qui n'est ni une lettre ni un chiffre ni un *underscore* `\W` ;
- Ce qui n'est pas un chiffre `\D` ;
- Ce qui n'est pas un caractère blanc `\S`.


<a id='t1-3'/>

## Caractères de regex

Dans certains cas, on peut vouloir détecter des éléments qu'on ne peut pas écrire au clavier, c'est le cas d'un début de ligne, une fin de ligne, mais également d'un début ou une fin de mot.

Pour les détecter avec une regex, il existe ceci :

- début de ligne : `^` ;
- fin de ligne : `$` ;
- début/fin de mot : `\b`.

Pour comprendre l'utilisation de ces caractères, voici des exemples :

- Si on veut récupérer le premier mot de chaque ligne: `^\w+` ;
- Si on veut récupérer le dernier mot de chaque ligne: `\w+$` ;
- Si on veut récupérer le mot *bon* :
  - en utilisant juste `bon`, on obtiendrait tous les mots de notre fichier comprenant ces trois lettres consécutivement (*bonjour*, *abonder*, etc.) ;
  - en utilisant `\bbon\b` on obtient le mot seul.


<a id='t1-4'/>

## Caractères unicode

Il est aussi possible d'utiliser des regex pour trouver des caractères
[Unicode] :

- Le caractère ! en unicode: `\x21` ou `\u0021` ;
- un marqueur unicode: `\p{M}` ;
- n'importe quelle lettre de n'importe quel langage: `\p{L}\p{M}*` ;
- n'importe quel graphème unicode: `\X` (équivalent de `\P{M}\p{M}*)`.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Un graphème unicode est un caractère potentiellement enrichi de marqueurs (comme des signes diacritiques) représenté comme une seule unité graphique.
Par exemple a (`\u0061`) et à (qui peut être encodé comme `\u0224` ou bien `\u0061\u0300`) sont des graphèmes.
:::
:::
:::


<a id='t2'/>

# Les opérateurs]

Dans la partie précédente, on a vu comment chercher des éléments d'un ensemble mais cela fonctionnait caractère par caractère.
Nous allons maintenant voir comment faire pour trouver un mot au lieu d'une succession de caractères.


<a id='t2-1'/>

## L'opérateur d'alternative

Il est possible de dire que l'on veut un caractère **OU** un autre.
Pour cela on va simplement écrire `a|b` qui signifie *\"Je veux seulement les a **ou** les b\"* .


<a id='t2-2'/>

## Les opérateurs de quantité

- 0 ou 1 élément `?`
- 0 ou plusieurs éléments `*`
- Au moins 1 élément `+`
- Un nombre défini d'élément ``
  - `{0,}` = `*`
  - `{1,}` = `+`
  - `{,1}` = `?`
  - `\b\w{4,6}\b` (les mots qui font de 4 à 6 lettres)

L'intérêt est par exemple de ne plus chercher un chiffre mais un nombre.
Avec la partie précédente on peut écrire `\d+` qui va allumer tous les nombres (dans une date par exemple).

::: {.custom-block .custom-block-neutral}
::: {.custom-block-heading}
Petite précision :::

::: {.custom-block-body}
Le chiffre est au nombre ce que la lettre est au mot.
:::
:::


<a id='t2-3'/>

## Quelques exemples

Pour les exemples suivants, nous prendrons comme référence le texte ***\"Bonjour 2020\"***.

- L'expression `[a-zA-Z]` doit trouver la liste suivante `['B', 'o', 'n', 'j', 'o', 'u', 'r']` alors que l'expression `[a-zA-Z]+` doit trouver `['Bonjour']`.
- L'expression `\d` doit trouver la liste suivante `['2', '0', '2', '0']` alors que l'expression `\d+` doit trouver `['2020']`.
- L'expression `on|ou` doit trouver la liste suivante `['on', 'ou']`.
- L'expression `\d` doit trouver la liste suivante `['20', '20']`.
:::


<a id='t3'/>

# Les groupes


<a id='t3-1'/>

## Les groupes capturant

Dans certains cas, on peut vouloir capturer seulement une partie de l'expression régulière que l'on a écrite.
Par exemple, quand on sait comment une phrase est formée, on peut vouloir récupérer une information précise.

> Ex. ***\"Bonjour, je m'appelle Toto\"***

Si on veut récupérer le prénom, on ne peut pas écrire `[a-zA-Z]+` car nous aurions tous les mots même ceux qui ne nous intéressent pas.
On sait que le prénom se trouve généralement après avoir dit \"***je m'appelle***\".

On peut alors écrire `je m'appelle ` et on obtient ceci:

![Groupe capturant](/media/galleries/12002/b7789dcd-0817-4888-b581-8c3f40e063b6.png)

Le match complet est `je m'appelle Toto` mais on a précisé que la capture intéressante était la partie après \"**je m'appelle**\".


<a id='t3-2'/>

## Les groupes non capturant

Dans certains cas, il est possible que nous devions repérer une information importante mais dont la capture finale nous importe peu.
Dans ce cas on peut utiliser un groupe qui ne va pas capturer ce qui est entre parenthèses : ``.

Pas d'exemple pour celui là, vous en trouverez sûrement une utilité en pratiquant par vous même ![;)](/static/smileys/svg/clin.svg){.smiley} .


<a id='t3-3'/>

## Les groupes nommés

Quand on veut récupérer des données ordonnées d'une certaine manière comme le format ***jj/dd/yyyy*** d'une date par exemple, ce type de groupe devient très intéressant.
Un groupe nommé s'écrit de cette manière: ``.

Donc si on veut récupérer le jour, le mois et l'année, on peut écrire:\
`(?<day>\d+)\/(?<month>\d+)\/(?<year>\d+)`

![Groupe nommé](/media/galleries/12002/b5c049aa-28a2-48f2-809b-9d6e28326f5a.png)

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Le caractère `/` dans une expression régulière est un caractère spécial.
Pour l'utiliser, il faut \"échapper\" le caractère avec un `\`,
exactement comme pour les tabulations et les retours à la ligne: `\/`.
:::
:::


<a id='t3-4'/>

## Les groupes spéciaux

Ces types de groupes vont être utilisés pour faire des recherches plus avancées dans le texte.

- Positive lookahead : trouver l'élément qui précède

  > Ex. `a` -\> *\"Les a qui précèdent un b\"*.

- Negative lookahead : trouver l'élément qui ne précède pas

  > Ex. `a(?!b)` -\> *\"Les a qui ne précèdent pas un
  > b\"*.

- Positive lookbehind : trouver l'élément qui succède

  > Ex. `(?<=b)a` -\> *\"Les a qui succèdent un b\"*.

- Negative lookbehind : trouver l'élément qui ne succède pas

  > Ex. `(?<!b)a` -\> *\"Les a qui ne succèdent pas un
  > b\"*.

> Ex. *\"Je veux le mot qui se trouve avant **zestedesavoir**\"*\
`\w+(?=\s*zestedesavoir)` -\> doit allumer *\"**site**\"*.

La liste complète des groupes [est accessible ici](https://www.regular-expressions.info/refadv.html) (en anglais).
:::


