---
title: Les expressions régulières
---

[comment]: <> (FINET)

# Les expressions régulières

**Un tutoriel pour comprendre les bases des expressions régulières**


**Une expression régulière est une chaîne de caractères qui décrit les ensembles possible d'une autre chaîne de caractères.**

En suivant ce tutoriel, vous serez capable d'écrire vous-même vos
expressions régulières en fonction de vos besoins.
On peut les utiliser
aussi bien pour rechercher des \"motifs\" dans des fichiers texte,
appliquer des transformations dans des cellules de tableurs, valider la
conformité d'une donnée ou encore extraire des informations.

Nous commencerons avec les bases des expressions régulières en
s'exerçant sur des exemples simples, puis nous verrons ensuite quelques
cas d'utilisations dans un milieu professionnel (en programmation et
avec des outils en ligne de commande).

Le cours sera séparé en cinq parties:

-  [Les différents ensembles](#1-les-differents-ensembles)
-  [Les opérateurs](#2-les-operateurs)
-  [Les groupes](#3-les-groupes)
-  [Utilisation en milieu
  professionnel](#4-utilisation-en-milieu-professionnel)
-  [Entrainement](#5-entrainement)


## [Les différents ensembles](#1-les-differents-ensembles) {#1-les-differents-ensembles}

::: {.extract-wrapper}
Quand on écrit sur un clavier, on peut utiliser un ensemble défini de
caractères.
On y trouve les **lettres** minuscules/majuscules, les
**chiffres**, les **espaces** ou **caractères \"blancs\"** et des
caractères **\"spéciaux\"** (&\"'…).

Chacun de ces types de caractères appartient à un ensemble et nous
allons tout de suite commencer à jouer avec.

Pour commencer à explorer le monde des *regex*, ouvrez le site
[Rubular](https://rubular.com/) et dans la partie ***Your test
string***, collez ceci:

::: {.hljs-code-div .hljs-code-text}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}[]{count="6"}[]{count="7"}
:::

  Bonjour et bienvenue dans le tutoriel sur les expressions régulières du site zestedesavoir.com
  anti antidote

  &é"'(è_çà)=
  #{[|`\^@]}

  Date: 06/08/2020
:::

Si dans la partie ***Your regular expression*** on écrit juste `a`, on
voit dans la partie ***Match result*** que tous les a présents
dans le texte se sont allumés (sauf le à qui est un caractère
spécial).

::: {.align-center}
![Regex
a](/media/galleries/12002/86d37170-4c0c-4913-9dc5-866bc5c85d0c.png)
:::

Faire une recherche sur une seule lettre n'a pas vraiment d'intérêt.
On
pourrait alors vouloir chercher d'un seul coup l'ensemble des lettres de
l'alphabet, ou bien l'ensemble des voyelles dans le texte… Et c'est là
qu'interviennent les ensembles !
![;)](/static/smileys/svg/clin.svg){.smiley}


### Les ensembles[](#les-ensembles)

Dans les expressions régulières, un ensemble se représente entre
crochets `[]`:

-  les lettres `[a-z]` ;
-  les chiffres `[0-9]` ;
-  les caractères blanc `[ \t\n]` :
  -  `\t` est la manière textuelle de représenter une tabulation ;
  -  `\n` est la manière textuelle de représenter un retour à la
  ligne.
-  les caractères spéciaux `[&é"'(è_çà)=]` (à compléter en fonction des
  besoins) ;
-  la négation (trouver ce qui n'est pas compris dans mon ensemble)
  `[^a]` (tout ce qui n'est pas un a).

Maintenant écrivons dans la partie ***Your regular expression***
l'ensemble des lettres (`[a-z]`), nous devrions obtenir ceci:

::: {.align-center}
![Resultat](/media/galleries/12002/28466200-6db1-4262-9f0d-97fd09279cfc.png)
:::

On peut observer que toutes les **lettres minuscules** se sont allumées
mais pas les **lettres majuscules**.
C'est pour la simple et bonne
raison que ce sont 2 ensembles différents.
Pour avoir l'ensemble des
lettres du texte, on va pouvoir écrire 2 ensembles à l'intérieur de
notre ensemble: `[a-zA-Z]`.

Ainsi on comprend bien que `[a-z]` signifie : *\"Je veux les lettres
allant de a à z\"*, ce qu'il ne sera pas possible de
faire avec les voyelles puisqu'elles ne se suivent pas, il faudra écrire
`[aeiou]`.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Si vous utilisez - en dehors d'un ensemble (`[]`) il sera
interprété comme le caractère -, ce qui sera également le cas
dans un ensemble **si** et seulement **si** il n'est pas entouré.\
Ex. `[-aeiou]` trouve les voyelles et le tiret.\
`[aei-ou]` trouve les a, e, ce qui se trouve entre
i et o dans la table ascii, et le u.
:::
:::


### Les raccourcis d'ensembles[](#les-raccourcis-densembles)

Il peut vite être fastidieux d'écrire un grand ensemble et de réécrire
toujours la même chose.
Il existe des ensembles déjà définis pour ceux
présentés plus haut :

-  les lettres + les chiffres + l'underscore `\w` ;
-  les chiffres `\d` ;
-  les caractères blancs `\s` ;
-  les caractères spéciaux : désolé je n'irai pas plus loin pour celui
  ci ;
-  n'importe quel caractère `.`.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Si on veut détecter le caractère \"point\" ., il va falloir
écrire `.`, sinon, l'expression régulière pensera que l'on cherche
n'importe quel caractère.
:::
:::

Très pratique, chaque raccourci a également son contraire :

-  ce qui n'est pas une lettre ou un chiffre ou un underscore `\W` ;
-  ce qui n'est pas un chiffre `\D` ;
-  ce qui n'est pas un caractère blanc `\S`.

L'ensemble en majuscule indique l'inverse de l'ensemble minuscule.
Dans
ce cas il n'est pas utile d'utiliser les `[]` sauf si on veut combiner
différents ensembles.


### Caractères de regex[](#caractères-de-regex)

Dans certains cas, on peut vouloir détecter des éléments qu'on ne peut
pas écrire au clavier, c'est le cas d'un début de ligne, une fin de
ligne, mais également d'un début ou une fin de mot.

Pour les détecter avec une regex, il existe ceci :

-  début de ligne : `^` ;
-  fin de ligne : `$` ;
-  début/fin de mot : `\b`.

Pour comprendre l'utilisation de ces caractères, voici des exemples :

-  si on veut récupérer le premier mot de chaque ligne: `^\w+` ;
-  si on veut récupérer le dernier mot de chaque ligne: `\w+$` ;
-  si on veut récupérer le mot anti :
  -  en utilisant juste `anti`, on en obtiendrait 2 (celui de
  **anti** et de **antidote**) ;
  -  en utilisant `\banti\b` on obtient bien le mot seul **anti**
  mais pas celui de **antidote**.


### Caractères unicode[](#caractères-unicode)

Il est aussi possible d'utiliser des regex pour trouver des caractères
[Unicode](https://fr.wikipedia.org/wiki/Unicode) :

-  le caractère ! en unicode: `\x21` ou `\u0021` ;
-  un marqueur unicode: `\p{M}` ;
-  n'importe quelle lettre de n'importe quel langage: `\p{L}\p{M}*` ;
-  n'importe quel graphème unicode: `\X` (équivalent de `\P{M}\p{M}*)`.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Un graphème unicode est un caractère potentiellement enrichi de
marqueurs (comme des signes diacritiques) représenté comme une seule
unité graphique.
Par exemple a (`\u0061`) et à (qui peut
être encodé comme `\u0224` ou bien `\u0061\u0300`) sont des graphèmes.
:::
:::
:::


## [Les opérateurs](#2-les-operateurs) {#2-les-operateurs}

::: {.extract-wrapper}
Dans la partie précédente, on a vu comment chercher des éléments d'un
ensemble mais cela fonctionnait caractère par caractère.
Nous allons
maintenant voir comment faire pour trouver un mot au lieu d'une
succession de caractères.


### L'opérateur d'alternative[](#lopérateur-dalternative)

Il est possible de dire que l'on veut un caractère **OU** un autre.
Pour
cela on va simplement écrire `a|b` qui signifie *\"Je veux seulement les
a **ou** les b\"* (aussi équivalent à l'ensemble
`[ab]`).


### Les opérateurs de quantité[](#les-opérateurs-de-quantité)

-  0 ou 1 élément `?`
-  0 ou plusieurs éléments `*`
-  Au moins 1 élément `+`
-  Un nombre défini d'élément `{n,m}`
  -  `{0,}` = `*`
  -  `{1,}` = `+`
  -  `{,1}` = `?`
  -  `\b\w{4,6}\b` (les mots qui font de 4 à 6 lettres)

L'intérêt est par exemple de ne plus chercher un chiffre mais un nombre.
Avec la partie précédente on peut écrire `\d+` qui va allumer tous les
nombres (dans une date par exemple).

::: {.custom-block .custom-block-neutral}
::: {.custom-block-heading}
Petite précision
:::

::: {.custom-block-body}
Le chiffre est au nombre ce que la lettre est au mot.
:::
:::


### Quelques exemples[](#quelques-exemples)

Pour les exemples suivants, nous prendrons comme référence le texte
***\"Bonjour 2020\"***.

-  L'expression `[a-zA-Z]` doit trouver la liste suivante
  `['B', 'o', 'n', 'j', 'o', 'u', 'r']` alors que l'expression
  `[a-zA-Z]+` doit trouver `['Bonjour']`.
-  L'expression `\d` doit trouver la liste suivante
  `['2', '0', '2', '0']` alors que l'expression `\d+` doit trouver
  `['2020']`.
-  L'expression `on|ou` doit trouver la liste suivante `['on', 'ou']`.
-  L'expression `\d{2}` doit trouver la liste suivante `['20', '20']`.
:::


## [Les groupes](#3-les-groupes) {#3-les-groupes}

::: {.extract-wrapper}


### Les groupes capturant[](#les-groupes-capturant)

Dans certains cas, on peut vouloir capturer seulement une partie de
l'expression régulière que l'on a écrite.
Par exemple, quand on sait
comment une phrase est formée, on peut vouloir récupérer une information
précise.

> Ex. ***\"Bonjour, je m'appelle Toto\"***

Si on veut récupérer le prénom, on ne peut pas écrire `[a-zA-Z]+` car
nous aurions tous les mots même ceux qui ne nous intéressent pas.
On
sait que le prénom se trouve généralement après avoir dit \"***je
m'appelle***\".

On peut alors écrire `je m'appelle ([a-zA-Z]+)` et on obtient ceci:

![Groupe
capturant](/media/galleries/12002/b7789dcd-0817-4888-b581-8c3f40e063b6.png)

Le match complet est `je m'appelle Toto` mais on a précisé que la
capture intéressante était la partie après \"**je m'appelle**\".


### Les groupes non capturant[](#les-groupes-non-capturant)

Dans certains cas, il est possible que nous devions repérer une
information importante mais dont la capture finale nous importe peu.
Dans ce cas on peut utiliser un groupe qui ne va pas capturer ce qui est
entre parenthèses : `(?:noncapturant)`.

Pas d'exemple pour celui là, vous en trouverez sûrement une utilité en
pratiquant par vous même ![;)](/static/smileys/svg/clin.svg){.smiley} .


### Les groupes nommés[](#les-groupes-nommés)

Quand on veut récupérer des données ordonnées d'une certaine manière
comme le format ***jj/dd/yyyy*** d'une date par exemple, ce type de
groupe devient très intéressant.
Un groupe nommé s'écrit de cette
manière: `(?<name>selection)`.

Donc si on veut récupérer le jour, le mois et l'année, on peut écrire:\
`(?<day>\d+)\/(?<month>\d+)\/(?<year>\d+)`

![Groupe
nommé](/media/galleries/12002/b5c049aa-28a2-48f2-809b-9d6e28326f5a.png)

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Le caractère `/` dans une expression régulière est un caractère spécial.
Pour l'utiliser, il faut \"échapper\" le caractère avec un `\`,
exactement comme pour les tabulations et les retours à la ligne: `\/`.
:::
:::


### Les groupes spéciaux[](#les-groupes-spéciaux)

Ces types de groupes vont être utilisés pour faire des recherches plus
avancées dans le texte.

-  Positive lookahead : trouver l'élément qui précède

  > Ex. `a(?=b)` -\> *\"Les a qui précèdent un b\"*.

-  Negative lookahead : trouver l'élément qui ne précède pas

  > Ex. `a(?!b)` -\> *\"Les a qui ne précèdent pas un
  > b\"*.

-  Positive lookbehind : trouver l'élément qui succède

  > Ex. `(?<=b)a` -\> *\"Les a qui succèdent un b\"*.

-  Negative lookbehind : trouver l'élément qui ne succède pas

  > Ex. `(?<!b)a` -\> *\"Les a qui ne succèdent pas un
  > b\"*.

> Ex. *\"Je veux le mot qui se trouve avant **zestedesavoir**\"*\ `\w+(?=\s*zestedesavoir)` -\> doit allumer *\"**site**\"*.

La liste complète des groupes [est accessible
ici](https://www.regular-expressions.info/refadv.html) (en anglais).
:::


## [Utilisation en milieu professionnel](#4-utilisation-en-milieu-professionnel) {#4-utilisation-en-milieu-professionnel}

::: {.extract-wrapper}
Depuis le début du tutoriel, vous faites vos tests sur le site
**Rubular** qui interprète des expressions régulières basées sur le
langage Ruby.
Si je vous précise ça, c'est que ce détail a son
importance.

En effet, en fonction des langages ou des outils utilisés, le moteur de
regex ne sera pas forcément le même et vous pouvez vous trouver dans un
cas ou une expression régulière fonctionne dans un langage/outil et pas
dans un autre.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
En dehors des langages et des outils, il existe également d'autres sites
que Rubular pour tester des expressions régulières.\
Ex. [Regex101](https://regex101.com/), [RegExr](https://regexr.com/),
[RegexTester](https://www.regextester.com/)…
:::
:::

::: {.custom-block .custom-block-warning}
::: {.custom-block-body}
Ce n'est pas parce que l'on maîtrise l'utilisation des regex qu'il faut
en abuser.
Même si dans certains cas cela peut sembler très pratique, il
faut garder à l'esprit que les utiliser abusivement peut parfois mener à
des problèmes de performances et de maintenabilité.
:::
:::


### Où utiliser les regex ?[](#où-utiliser-les-regex)

On peut les utiliser dans les différents langages de programmation,
notamment en C++, Java, Python, Ruby, Perl, Php, SQL (en fonction du
SGBD), Javascript, etc.
Ce qui changera en fonction du langage, c'est le
moteur qui interprète la regex.

Il est également possible de les utiliser dans des outils pour
développeurs (éditeur de code, IDE…) comme Notepad++, Visual studio
code, Eclipse… La liste pouvant être assez longue contentons nous de
ces exemples ![;)](/static/smileys/svg/clin.svg){.smiley} .

Et il est aussi possible de s'en servir dans des outils en ligne de
commande comme
[grep](https://man7.org/linux/man-pages/man1/grep.1.html),
[sed](https://man7.org/linux/man-pages/man1/sed.1.html) ou encore
[awk](https://man7.org/linux/man-pages/man1/awk.1p.html).

::: {.custom-block .custom-block-question}
::: {.custom-block-body}
Puisque tu nous a dis qu'il ne fallait pas abuser des regex, existe-t-il
un exemple où l'utilisation des expressions régulières est idéale ?
:::
:::

Oui, les regex peuvent être exactement ce qu'il nous faut pour par
exemple donner le format précis d'une carte de crédit en fonction du
type de carte :

-  la Visa : `^40-9(?:0-9)?$` ;
-  la MasterCard :
  `^(?:5[1-5]0-9|222[1-9]|22[3-9][0-9]|2[3-6]0-9|27[01][0-9]|2720)0-9$` ;
-  l'American Express : `^3[47]0-9$`.

C'est d'ailleurs grâce à ça que quand vous entrez le numéro de votre
carte sur un site en ligne, il est capable de vous afficher le type de
carte que vous utilisez.


### Exemples en programmation[](#exemples-en-programmation)

Prenons un exemple simple, on veut savoir si une chaîne de caractères
est une [couleur
hexadecimal](https://fr.wikipedia.org/wiki/Couleur_du_Web#Codage_informatique_des_couleurs)
ou non.


#### JavaScript[](#javascript)

::: {.hljs-code-div .hljs-code-js}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}
:::

  let re = /^#0-9a-fA-F$/

  re.test('#80e0f5') // true
  re.test('#F39580') // true
  re.test('#8cj380') // false
:::


#### Python[](#python)

::: {.hljs-code-div .hljs-code-py}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}[]{count="6"}
:::

  import re
  p = re.compile('^#0-9a-fA-F$')

  bool(p.match('#80e0f5')) # True
  bool(p.match('#F39580')) # True
  bool(p.match('#8cj380')) # False
:::


#### C++[](#c)

::: {.hljs-code-div .hljs-code-cpp}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}[]{count="6"}[]{count="7"}[]{count="8"}[]{count="9"}[]{count="10"}[]{count="11"}[]{count="12"}
:::

  #include <iostream>
  #include <regex>

  int main()
  {
  std::regex re("^#0-9a-fA-F$");
  std::cmatch m;
   
  std::cout << std::regex_match("#80e0f5", m, re) << std::endl; // 1
  std::cout << std::regex_match("#F39580", m, re) << std::endl; // 1
  std::cout << std::regex_match("#8cj380", m, re) << std::endl; // 0
  }
:::


### Exemples en ligne de commande[](#exemples-en-ligne-de-commande)

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
grep, sed et awk ont été portés sur Windows, vous pouvez les trouver
[ici](http://gnuwin32.sourceforge.net/). Ces outils en ligne de commande
sont également accessible sur Windows grâce à
[WSL](https://ubuntu.com/wsl), je considère donc que ce qui suit est
valable aussi bien pour Windows que Linux.
:::
:::

Pour nos tests, on va créer un fichier de log fictif, copier/coller le
texte suivant et l'enregistrer dans un fichier :

::: {.hljs-code-div .hljs-code-text}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}[]{count="6"}[]{count="7"}
:::

  192.168.0.11 [01 Feb 2019] - GET data
  192.168.0.12 [02 Feb 2019] - POST data
  192.168.0.12 [02 Apr 2019] - DELETE data
  192.168.0.12 [24 Jun 2020] - POST data
  192.168.0.14 [12 Jul 2020] - GET data
  192.168.0.14 [14 Jul 2020] - POST data
  192.168.0.14 [17 Aug 2020] - DELETE data
:::

Imaginons que pour X raisons, on vous demande de trouver tout ce qui
s'est passé à des dates précises sur un système ou une machine.
Vous
n'allez évidemment pas lire ligne par ligne et extraire à la main les
lignes souhaitées.


#### Avec grep[](#avec-grep)

Ex 1.
*\"**Je veux savoir tout ce qui s'est passé en avril 2019 et
juillet 2020**\"*.

::: {.hljs-code-div .hljs-code-bash}
::: {.hljs-line-numbers}
[]{count="1"}
:::

  grep -P "\[\d{2} (Apr 2019|Jul 2020)\]" log_file.txt
:::

La commande précédente devrait vous retourner ceci :

> 192.168.0.12 **\[02 Apr 2019\]** - DELETE data\ 192.168.0.14 **\[12 Jul 2020\]** - GET data\ 192.168.0.14 **\[14 Jul 2020\]** - POST data


#### Avec sed[](#avec-sed)

Ex 2.
*\"**Je veux connaitre seulement les IP de ceux qui ont fait
quelque chose en avril 2019 et juillet 2020**\"*.

::: {.hljs-code-div .hljs-code-bash}
::: {.hljs-line-numbers}
[]{count="1"}
:::

  sed -nE 's/^(.*) \[0-9 (Apr 2019|Jul 2020)\].*/\1/p' log_file.txt | uniq
:::

La commande précédente devrait vous retourner ceci :

> 192.168.0.12\ 192.168.0.14


#### Avec awk[](#avec-awk)

Même exemple qu'avec `sed` :

::: {.hljs-code-div .hljs-code-bash}
::: {.hljs-line-numbers}
[]{count="1"}
:::

  awk -e '/(.*) \[0-9 (Apr 2019|Jul 2020)\]/ {print $1}' log_file.txt | uniq
:::


### Exemple de différences[](#exemple-de-différences)

En fonction du langage ou de l'outil utilisé, il peut y avoir des
différences, le but ici n'est pas de toutes les détailler mais de savoir
que ça peut arriver pour que vous sachiez que dans certains cas, il faut
faire une recherche dans les documentations pour voir comment contourner
le problème.


#### Les groupes nommés[](#les-groupes-nommés) {#les-groupes-nommés}

L'utilisation des groupes nommés fait partie des choses qui peuvent
changer.

En Python par exemple, en utilisant le module `re`, si on souhaite
utiliser un groupe nommé, on ne va pas écrire `(?<group>blabla)` mais
`(?P<group>blabla)`.

En javascript, il se peut qu'en fonction du navigateur, il ne soit pas
assez récent pour les gérer (de plus en plus rare).

On peut également trouver cette syntaxe: `(?'group'blabla)`, bref vous
avez compris, ce sont des choses qui peuvent arriver.


#### L'utilisation des ensembles[](#lutilisation-des-ensembles)

Il se peut que dans certains cas, l'utilisation des ensembles se fasse
autrement que présenté précédemment.

On peut trouver `[:digit:]` qui équivaut à `\d`, `[:alpha:]` équivalent
de `[a-zA-Z]`…

Encore une fois, vous l'aurez compris, le but ici est uniquement de vous
informer qu'il peut y avoir des différences en fonction de ce que l'on
utilise.


### La substitution[](#la-substitution)

Une des fonctionnalités très intéressante et puissante des regex, c'est
la substitution.
Imaginez un fichier texte qui contient des dates au
format ***jj/mm/aaaa*** et que vous devez toutes les passer au format
***aaaa-mm-jj***. Si votre fichier fait quelques lignes, le faire à la
main sera assez rapide, mais dans un fichier de plusieurs centaines de
lignes, les regex peuvent nous faire gagner un temps fou.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Dans mon cas j'utilise Visual Studio Code pour l'exemple qui suit, mais
vous pouvez utiliser l'éditeur que vous préférez.
:::
:::

::: {.hljs-code-div .hljs-code-text}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}
:::

  01/01/2000
  07/08/2019
  13/09/2020
  21/12/2012
  07/11/2022
:::

La première étape consiste à écrire le format actuel de nos dates sans
oublier les groupes capturant :

-  le jour : `(\d{2})` (groupe 1) ;
-  le mois : `(\d{2})` (groupe 2) ;
-  l'année : `(\d{4})` (groupe 3).

Au complet nous avons donc : `(\d{2})\/(\d{2})\/(\d{4})`.
Il suffit
maintenant de faire un Ctrl+h pour écrire cette regex dans la
partie haute et d'écrire `$3-$2-$1` dans la partie basse pour faire
référence au groupe 3, 2 et 1.

::: {.align-center}
![Substitution](/media/galleries/12002/1ed0b988-a203-489b-9679-a172c093d467.png)
:::

Et là, magie ! Vous avez bien changé le format de toutes les dates de
votre fichier.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Il se peut que dans certains éditeurs, la référence à un groupe se fasse
avec `\1` au lieu de `$1`.
:::
:::

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Cet exemple est un travail taillé pour sed.

::: {.hljs-code-div .hljs-code-bash}
::: {.hljs-line-numbers}
[]{count="1"}
:::

  sed -E 's/(0-9)\/(0-9)\/(0-9)/\3-\2-\1/' date_file.txt
:::

Vous pouvez également directement modifier le fichier et ne pas
\"échaper\" le / avec la commande suivante :

::: {.hljs-code-div .hljs-code-bash}
::: {.hljs-line-numbers}
[]{count="1"}
:::

  sed -Ei 's!(0-9)/(0-9)/(0-9)!\3-\2-\1!' date_file.txt
:::
:::
:::
:::


## [Entrainement](#5-entrainement) {#5-entrainement}

::: {.extract-wrapper}
Pour nous entrainer, nous allons utiliser une fable de **La Fontaine** :
*Le Corbeau et le Renard*.

Pour chaque question, essayez de faire une version sans Unicode et une
avec.

::: {.hljs-code-div .hljs-code-text}
::: {.hljs-line-numbers}
[]{count="1"}[]{count="2"}[]{count="3"}[]{count="4"}[]{count="5"}[]{count="6"}[]{count="7"}[]{count="8"}[]{count="9"}[]{count="10"}[]{count="11"}[]{count="12"}[]{count="13"}[]{count="14"}[]{count="15"}[]{count="16"}[]{count="17"}[]{count="18"}
:::

  Maître Corbeau, sur un arbre perché,
  Tenait en son bec un fromage.
  Maître Renard, par l'odeur alléché,
  Lui tint à peu près ce langage :
  Et bonjour, Monsieur du Corbeau,
  Que vous êtes joli ! que vous me semblez beau !
  Sans mentir, si votre ramage
  Se rapporte à votre plumage,
  Vous êtes le Phénix des hôtes de ces bois.
  À ces mots le Corbeau ne se sent pas de joie,
  Et pour montrer sa belle voix,
  Il ouvre un large bec, laisse tomber sa proie.
  Le Renard s'en saisit, et dit : Mon bon Monsieur,
  Apprenez que tout flatteur
  Vit aux dépens de celui qui l'écoute.
  Cette leçon vaut bien un fromage sans doute.
  Le Corbeau honteux et confus
  Jura, mais un peu tard, qu'on ne l'y prendrait plus.
:::

**Exercices**

1. Le premier mot de chaque ligne.
2. Les mots qui commencent par une majuscule mais qui ne sont pas en
  début de ligne.
3. Les mots de plus de 8 lettres.
4. Les mots qui ont au moins 3 voyelles d'affilées.
5. Les mots qui n'ont pas d'accent.

::: {.custom-block .custom-block-information}
::: {.custom-block-body}
Pour chaque cas, il existe plusieurs manières de faire.
Je ne donnerai
donc qu'une solution pour chaque point.
:::
:::

::: {.custom-block .custom-block-spoiler}
::: {.custom-block-body}
1. `^[a-zA-ZÀéèàîï]+`, Unicode : `^\p{L}+`.
2. `(?:.)([A-Z][a-zA-ZÀéèàîï]+)`, Unicode : `(?:.)(\p{Lu}\p{L}+)`.
3. `a-zA-ZÀéèàîï`, Unicode : `\p{L}{8,}`.
4. `[a-zA-ZÀéèàîï]*aeiou[a-zA-ZÀéèàîï]*`, Unicode :
  `\p{L}*aeiou\p{L}*`.
5. `\b[a-zA-Zç]+\b`.
:::
:::
:::

------------------------------------------------------------------------

Maîtriser les expressions régulières permet de faire des tâches de tri
ou de filtre plus efficacement et de manière plus complexe.

Maintenant que vous avez les bases, l'important est d'être curieux et
d'essayer vous même de modifier certains exemples, voir ce qu'il s. passe et vraiment bien comprendre le fonctionnement.


##### Remerciements[](#remerciements)

Merci à @[kayou](/membres/voir/kayou/){.ping
.ping-link}, @[Yarflam](/membres/voir/Yarflam/){.ping
.ping-link},
@[SpaceFox](/membres/voir/SpaceFox/){.ping
.ping-link},
@[QuentinC](/membres/voir/QuentinC/){.ping .ping-link}
et @[adri1](/membres/voir/adri1/){.ping .ping-link}
pour leurs remarques ![:)](/static/smileys/svg/smile.svg){.smiley}
:::


### 102 commentaires {#comments .comments-title}

-  1
-  [2](/tutoriels/3651/les-expressions-regulieres-1/?page=2#comments)
-  [3](/tutoriels/3651/les-expressions-regulieres-1/?page=3#comments)
-  [4](/tutoriels/3651/les-expressions-regulieres-1/?page=4#comments)
-  [5](/tutoriels/3651/les-expressions-regulieres-1/?page=5#comments)
-  [ Suivante
  ](/tutoriels/3651/les-expressions-regulieres-1/?page=2#comments){.ico-after
  .arrow-right .blue}

::: {.user}
[![](https://secure.gravatar.com/avatar/8b999b01bae94d35ff4552ec39ee4eec?d=identicon&s=80){.avatar}](/@cyr1l){.avatar-link}
:::

::: {.message}
-  [cyr1l](/@cyr1l){.username},
  [dimanche 23 août 2020 à
  17h2223/08/20 à 17h22](#p225201 "Il y a 4 années"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
Sympa l'article ![:)](/static/smileys/svg/smile.svg){.smiley} Sinon un
testeur d'expressions régulières avec un mode graphique:
<https://extendsclass.com/regex-tester.html>
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [23/08/20 à 17h22](#p225201){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/225201/karma/"}
 +1 -0 
:::
:::
:::

::: {.msg-are-hidden .hidden aria-hidden="true"}
[Un ou plusieurs messages ont été masqués](#show){.link}
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/21faf9b2a377acb3d08abedc778f6275?d=identicon&s=80){.avatar}](/@bonbon242019){.avatar-link}
 Banni 
:::

::: {.message}
-  [bonbon242019](/@bonbon242019){.username},
  [lundi 05 octobre 2020 à
  06h3505/10/20 à 06h35](#p226713 "Il y a 3 années, 10 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Arius  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [05/10/20 à 06h35](#p226713){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/2ced794e6de39910cd05e87fe12e6f79?d=identicon&s=80){.avatar}](/@romdhan){.avatar-link}
:::

::: {.message}
-  [romdhan](/@romdhan){.username},
  [mardi 16 mars 2021 à
  22h3616/03/21 à 22h36](#p232372 "Il y a 3 années, 5 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
Merci ça va énormement m'aider.
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [16/03/21 à 22h36](#p232372){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/232372/karma/"}
 +1 -0 
:::
:::
:::

::: {.msg-are-hidden .hidden aria-hidden="true"}
[Un ou plusieurs messages ont été masqués](#show){.link}
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/18be4d1113e2a8df5b973725cf6df076?d=identicon&s=80){.avatar}](/@amyjeffords12){.avatar-link}
 Banni 
:::

::: {.message}
-  [amyjeffords12](/@amyjeffords12){.username},
  [mardi 03 janvier 2023 à
  08h5903/01/23 à 08h59](#p248093 "Il y a 1 année, 8 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [03/01/23 à 08h59](#p248093){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/f27e355cbd06a929a001a0364467189c?d=identicon&s=80){.avatar}](/@AnthonyAnsonn){.avatar-link}
 Banni 
:::

::: {.message}
-  [AnthonyAnsonn](/@AnthonyAnsonn){.username},
  [vendredi 24 février 2023 à
  13h3724/02/23 à 13h37](#p249327 "Il y a 1 année, 6 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [24/02/23 à 13h37](#p249327){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/ec1f254e79145b99e91d04f2ec751983?d=identicon&s=80){.avatar}](/@oli45641){.avatar-link}
 Banni 
:::

::: {.message}
-  [oli45641](/@oli45641){.username},
  [mercredi 01 mars 2023 à
  11h3401/03/23 à 11h34](#p249406 "Il y a 1 année, 6 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [01/03/23 à 11h34](#p249406){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/9e34d71286eb7f1e92237d2e929d4ca6?d=identicon&s=80){.avatar}](/@alexaandr884){.avatar-link}
 Banni 
:::

::: {.message}
-  [alexaandr884](/@alexaandr884){.username},
  [vendredi 03 mars 2023 à
  12h2903/03/23 à 12h29](#p249446 "Il y a 1 année, 6 mois"){.date}
-  Modifié par Moté

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [03/03/23 à 12h29](#p249446){.mobile-permalink}
-  Modifié
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/9e34d71286eb7f1e92237d2e929d4ca6?d=identicon&s=80){.avatar}](/@alexaandr884){.avatar-link}
 Banni 
:::

::: {.message}
-  [alexaandr884](/@alexaandr884){.username},
  [samedi 04 mars 2023 à
  12h5004/03/23 à 12h50](#p249460 "Il y a 1 année, 5 mois"){.date}
-  Modifié par Moté

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [04/03/23 à 12h50](#p249460){.mobile-permalink}
-  Modifié
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/d4c844a2963b0d1c9201893a14395170?d=identicon&s=80){.avatar}](/@blackdesgin){.avatar-link}
 Banni 
:::

::: {.message}
-  [blackdesgin](/@blackdesgin){.username},
  [vendredi 10 mars 2023 à
  08h2010/03/23 à 08h20](#p249508 "Il y a 1 année, 5 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Moté
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [10/03/23 à 08h20](#p249508){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/19929ffbaf7acaef95729d5d11dafd04?d=identicon&s=80){.avatar}](/@emilyjevica){.avatar-link}
 Banni 
:::

::: {.message}
-  [emilyjevica](/@emilyjevica){.username},
  [samedi 11 mars 2023 à
  12h4411/03/23 à 12h44](#p249521 "Il y a 1 année, 5 mois"){.date}

::: {.message-content}
Cette réponse a été utile

Masqué par Moté  --- spam
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [11/03/23 à 12h44](#p249521){.mobile-permalink}
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/cb2808f4b513731326a177a8b8260cbf?d=identicon&s=80){.avatar}](/@VincentPuiss){.avatar-link}
 Banni 
:::

::: {.message}
-  [VincentPuiss](/@VincentPuiss){.username},
  [jeudi 16 mars 2023 à
  10h3716/03/23 à 10h37](#p249585 "Il y a 1 année, 5 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
Merci pour ce tutoriel ! J'ai quand même une question : est-ce qu'on
utilise toujours la même syntaxe pour d'autres langages ?
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [16/03/23 à 10h37](#p249585){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/249585/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/13ece61480048a0592abf9a59530c079?d=identicon&s=80){.avatar}](/@annettestout){.avatar-link}
 Banni 
:::

::: {.message}
-  [annettestout](/@annettestout){.username},
  [vendredi 17 mars 2023 à
  02h3317/03/23 à 02h33](#p249600 "Il y a 1 année, 5 mois"){.date}
-  Modifié

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
![[cyr1l](/tutoriels/3651/les-expressions-regulieres-1/?page=1#p225201)](/static/smileys/svg/smile.svg){.smiley}

Merci ![:ange:](/static/smileys/svg/ange.svg){.smiley}
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [17/03/23 à 02h33](#p249600){.mobile-permalink}
-  Modifié
:::

::: {.message-karma karma-uri="/api/contenus/reactions/249600/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/829518c430e1f7b03d9fcf60bf78bc81?d=identicon&s=80){.avatar}](/@thibsc){.avatar-link}
:::

::: {.message}
-  [thibsc](/@thibsc){.username},
  [jeudi 23 mars 2023 à
  15h3123/03/23 à 15h31](#p249675 "Il y a 1 année, 5 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
> Merci pour ce tutoriel ! J'ai quand même une question : est-ce qu'on utilise toujours la même syntaxe pour d'autres langages ?

[VincentPuiss](/tutoriels/3651/les-expressions-regulieres-1/?page=1#p249585)

Pas exactement, en fonction du moteur de regex utilisé et du langage de
programmation, tu peux avoir de légères différences
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [23/03/23 à 15h31](#p249675){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/249675/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/ec81174b3619c10b365b7fb2acf7f6d6?d=identicon&s=80){.avatar}](/@stef.heisel){.avatar-link}
 Banni 
:::

::: {.message}
-  [stef.heisel](/@stef.heisel){.username},
  [lundi 03 avril 2023 à
  09h5303/04/23 à 09h53](#p249804 "Il y a 1 année, 5 mois"){.date}
-  Modifié

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
thanks
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [03/04/23 à 09h53](#p249804){.mobile-permalink}
-  Modifié
:::

::: {.message-karma karma-uri="/api/contenus/reactions/249804/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/f95e6aa9fc624fbb0eb721996a671fff?d=identicon&s=80){.avatar}](/@nacyliz){.avatar-link}
:::

::: {.message}
-  [nacyliz](/@nacyliz){.username},
  [mardi 30 mai 2023 à
  11h3830/05/23 à 11h38](#p250622 "Il y a 1 année, 3 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
![[cyr1l](/tutoriels/3651/les-expressions-regulieres-1/?page=1#p225201)](/static/smileys/svg/smile.svg){.smiley}

De cette façon, je peux écrire mes propres expressions et appliquer des
transformations dans la cellule de la feuille de calcul.
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [30/05/23 à 11h38](#p250622){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/250622/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/0cf252679bdc9522f8cf789c6b0e387d?d=identicon&s=80){.avatar}](/@folah7){.avatar-link}
 Banni 
:::

::: {.message}
-  [folah7](/@folah7){.username},
  [jeudi 08 juin 2023 à
  11h1508/06/23 à 11h15](#p250755 "Il y a 1 année, 2 mois"){.date}
-  Modifié

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
good
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [08/06/23 à 11h15](#p250755){.mobile-permalink}
-  Modifié
:::

::: {.message-karma karma-uri="/api/contenus/reactions/250755/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/17f1f81afec2c2fa75468ca7abf6c44c?d=identicon&s=80){.avatar}](/@thelaptopsguide){.avatar-link}
 Banni 
:::

::: {.message}
-  [thelaptopsguide](/@thelaptopsguide){.username},
  [mardi 18 juillet 2023 à
  11h3418/07/23 à 11h34](#p251374 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
I've been playing EverQuest for years, and I must say that the community
is one of the friendliest I've ever come across.
It's always a pleasure
to group up with helpful and kind players.
Also don't forget visit these
blogs.
[Legenda para foto sozinha](https://legendaparafotosozinha.com/)
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [18/07/23 à 11h34](#p251374){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251374/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/17f1f81afec2c2fa75468ca7abf6c44c?d=identicon&s=80){.avatar}](/@thelaptopsguide){.avatar-link}
 Banni 
:::

::: {.message}
-  [thelaptopsguide](/@thelaptopsguide){.username},
  [mardi 18 juillet 2023 à
  11h5418/07/23 à 11h54](#p251375 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
\"Your blog has become my go-to resource for insightful and
well-researched articles.
I appreciate the time and effort you put into
each post.
The depth of your knowledge is evident, and it's a pleasure
to learn from you.\" [поздравление с днем
рождения](https://xn--80aeecaeabbidqg7auldfcngzlt57a.com/)
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [18/07/23 à 11h54](#p251375){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251375/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/d1ee2c01ffbeddf1912ab277727e7277?d=identicon&s=80){.avatar}](/@emmatrump){.avatar-link}
:::

::: {.message}
-  [emmatrump](/@emmatrump){.username},
  [jeudi 20 juillet 2023 à
  04h4520/07/23 à 04h45](#p251392 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
Twitter was hit with global outage with thousands of users complaining
about the social media platform not refreshing their tweets.
The users
of Twitter said that the platform is throwing the '[cannot retrieve
tweets](https://ebuzzpro.com/fix-cannot-retrieve-tweets-at-this-time/)'
error repeatedly.
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [20/07/23 à 04h45](#p251392){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251392/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/f05379088aee2c03a89218c8358255bb?d=identicon&s=80){.avatar}](/@geburtstagsiete){.avatar-link}
 Banni 
:::

::: {.message}
-  [geburtstagsiete](/@geburtstagsiete){.username},
  [jeudi 20 juillet 2023 à
  09h4020/07/23 à 09h40](#p251395 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
If you want to explore some crazy aesthetic instagram captions then
[click here](https://captionigaesthetic.id/) to to visit our site and
explore best captions for your posts
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [20/07/23 à 09h40](#p251395){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251395/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/f05379088aee2c03a89218c8358255bb?d=identicon&s=80){.avatar}](/@geburtstagsiete){.avatar-link}
 Banni 
:::

::: {.message}
-  [geburtstagsiete](/@geburtstagsiete){.username},
  [jeudi 20 juillet 2023 à
  10h0820/07/23 à 10h08](#p251396 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
If you want to explore some best happy birthday wishes for your loved
ones then [click here](https://felizcumpleanoso.com/) to explore our
list of happy best birthday wishes
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [20/07/23 à 10h08](#p251396){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251396/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/f05379088aee2c03a89218c8358255bb?d=identicon&s=80){.avatar}](/@geburtstagsiete){.avatar-link}
 Banni 
:::

::: {.message}
-  [geburtstagsiete](/@geburtstagsiete){.username},
  [jeudi 20 juillet 2023 à
  11h2920/07/23 à 11h29](#p251402 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
If you want to explore some best happy birthday wishes for your loved
ones then [click here](https://geburtstagseite.de/) to explore our list
of happy best birthday wishes
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [20/07/23 à 11h29](#p251402){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251402/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/305f4386f9f7cc1af7d9b151dd324d79?d=identicon&s=80){.avatar}](/@williamliz){.avatar-link}
:::

::: {.message}
-  [williamliz](/@williamliz){.username},
  [lundi 31 juillet 2023 à
  03h5731/07/23 à 03h57](#p251543 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
Very precise, Mastering regular expressions allows you to perform
sorting or filtering tasks more efficiently and in a more complex way.
That is demonstrated and proven through [Five Nights at Freddy's
4](https://fivenightsatfreddys4.com)
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [31/07/23 à 03h57](#p251543){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251543/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/e1b3749da6ccf9f978ea7d7c7b1d9eec?d=identicon&s=80){.avatar}](/@larryellison){.avatar-link}
:::

::: {.message}
-  [larryellison](/@larryellison){.username},
  [lundi 31 juillet 2023 à
  09h4331/07/23 à 09h43](#p251553 "Il y a 1 année, 1 mois"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
À regular expression is a string of characters that describes the
possible sets of another string of characters.
By following this
tutorial you will be able to write your own regular expressions
according to the needs of [geometry dash
bloodbath](https://geometrydashbloodbath.com)
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [31/07/23 à 09h43](#p251553){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251553/karma/"}
 +0 -0 
:::
:::
:::

::: {.user}
[![](https://secure.gravatar.com/avatar/a20c200ea9e3717dd031d999ec8fc366?d=identicon&s=80){.avatar}](/@earingwilted){.avatar-link}
:::

::: {.message}
-  [earingwilted](/@earingwilted){.username},
  [lundi 21 août 2023 à
  04h5821/08/23 à 04h58](#p251729 "Il y a 1 année"){.date}

::: {.message-content}
Cette réponse a été utile

::: {.message-text itemprop="text"}
J'ai parcouru Internet à la recherche d'une explication [geometry dash
lite](https://geometrydashlite.co/) complète des expressions régulières
pour la validation des entrées.
Parfois, je passe une heure ou plus à
essayer de donner un sens à la documentation ailleurs, pour constater
qu'une fois arrivé ici, tout s'enclenche.
En d'autres termes, du bon
travail !
:::
:::

::: {.message-bottom}
::: {.metadata-mobile}
-  [21/08/23 à 04h58](#p251729){.mobile-permalink}
:::

::: {.message-karma karma-uri="/api/contenus/reactions/251729/karma/"}
 +0 -0 
:::
:::
:::

-  1
-  [2](/tutoriels/3651/les-expressions-regulieres-1/?page=2#comments)
-  [3](/tutoriels/3651/les-expressions-regulieres-1/?page=3#comments)
-  [4](/tutoriels/3651/les-expressions-regulieres-1/?page=4#comments)
-  [5](/tutoriels/3651/les-expressions-regulieres-1/?page=5#comments)
-  [ Suivante
  ](/tutoriels/3651/les-expressions-regulieres-1/?page=2#comments){.ico-after
  .arrow-right .blue}

::: {.alert-box .info .alert-box-not-closable}
Connectez-vous pour pouvoir poster un message.\
[Connexion](/membres/connexion/?next=/tutoriels/3651/les-expressions-regulieres-1/){.alert-box-btn
.alert-box-btn-right}
:::

::: {.alert-box .not-member .alert-box-not-closable}


#### Pas encore membre ? {#pas-encore-membre .alert-box-title}

Créez un compte en une minute pour profiter pleinement de toutes les
fonctionnalités de Zeste de Savoir.
Ici, tout est gratuit et sans
publicité.\
[Créer un compte](/membres/inscription/){.alert-box-btn}
:::
:::

::: {.mobile-menu-bloc data-title="Sommaire du contenu"}


### Sommaire

1. [Les différents
  ensembles](#1-les-differents-ensembles){.mobile-menu-link
  .mobile-menu-sublink}
2. [Les opérateurs](#2-les-operateurs){.mobile-menu-link
  .mobile-menu-sublink}
3. [Les groupes](#3-les-groupes){.mobile-menu-link
  .mobile-menu-sublink}
4. [Utilisation en milieu
  professionnel](#4-utilisation-en-milieu-professionnel){.mobile-menu-link
  .mobile-menu-sublink}
5. [Entrainement](#5-entrainement){.mobile-menu-link
  .mobile-menu-sublink}
:::

::: {.mobile-menu-bloc .mobile-all-links .mobile-show-ico data-title="Partager"}


### Partager

-  [Twitter](https://twitter.com/share?url=https://zestedesavoir.com/tutoriels/3651/les-expressions-regulieres-1/&text=Les%20expressions%20régulières){.ico-after
  .twitter .blue}

-  [Facebook](https://www.facebook.com/sharer.php?u=https://zestedesavoir.com/tutoriels/3651/les-expressions-regulieres-1/&t=Les%20expressions%20régulières){.ico-after
  .facebook .blue}

-  [Mastodon](#share-to-mastodon){.open-modal .ico-after .mastodon
  .blue}

  Entrez l'adresse de votre instance Mastodon (ex: https://mamot.fr).

  Partager

-  [Diaspora\*](http://sharetodiaspora.github.io/?url=https://zestedesavoir.com/tutoriels/3651/les-expressions-regulieres-1/&title=Les%20expressions%20régulières){.ico-after
  .diaspora .blue}

-  [Envoyer par
  mail](mailto:?subject=Les%20expressions%20régulières&body=https://zestedesavoir.com/tutoriels/3651/les-expressions-regulieres-1/){.ico-after
  .email .blue}
:::

::: {.mobile-menu-bloc .mobile-all-links .mobile-show-ico data-title="Télécharger"}


### Télécharger

-  [PDF (175,0
  Kio)](/tutoriels/pdf/3651/les-expressions-regulieres-1.pdf){.ico-after
  .download .blue}
-  [LaTeX (26,7
  Kio)](/tutoriels/tex/3651/les-expressions-regulieres-1.tex){.ico-after
  .download .blue}
-  [EPUB (133,6
  Kio)](/tutoriels/epub/3651/les-expressions-regulieres-1.epub){.ico-after
  .download .blue}
-  [Archive (22,4
  Kio)](/tutoriels/zip/3651/les-expressions-regulieres-1.zip){.ico-after
  .download .blue}
:::
:::
:::

::: {.wrapper}
Zeste de Savoir [ • Version :
[v30.6-ostara/2da324a](https://github.com/zestedesavoir/zds-site/tree/2da324a6ecf8d45e007e260e4ec4cc34ef87fc10)
]{.version}

-  [](https://framapiaf.org/@ZesteDeSavoir "Suivez-nous sur Mastodon"){.btn
  .ico-after .mastodon .light .btn-mastodon .btn-holder}
-  [](https://www.facebook.com/ZesteDeSavoir "Aimez notre page Facebook"){.btn
  .ico-after .facebook .light .btn-facebook .btn-holder}
-  [](https://twitter.com/ZesteDeSavoir "Suivez-nous sur Twitter"){.btn
  .ico-after .twitter .light .btn-twitter .btn-holder}
-  [](https://discord.com/invite/ue5MTKq "Discutez avec nous sur Discord"){.btn
  .ico-after .discord .light .btn-discord .btn-holder}
-  [](https://github.com/zestedesavoir/zds-site "Contribuez au développement"){.btn
  .ico-after .github .light .btn-github .btn-holder}

```{=html}
```
-  [API](/api/)
-  [CGU](/pages/cgu/)
-  [Crédits techniques](/pages/technologies/)
-  [L'association](/pages/association/)
-  [Adhérer à l'association Adhérer](https://www.helloasso.com/associations/zeste-de-savoir/adhesions/adhesion-2024-2025)
-  [Contact](/pages/contact/)
-  [Les cookies](/pages/cookies/)
:::
:::
