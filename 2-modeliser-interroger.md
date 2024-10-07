---
mainfont: Alegreya
title: Modéliser et interroger
date: 1^er^ semestre 2024-2025
author: Sébastien Biay
---

Modéliser et interroger
=====

Plan :

1. [Modéliser un objet d'étude](#t1)
	1. [Qu'est-ce que modéliser ? ](#t1-1)
	2. [Rappel : vocabulaire ](#t1-2)
	3. [Prospective ](#t1-3)
	4. [Du modèle conceptuel au m. logique : cardinalité ](#t1-4)
2. [Interroger les ressources numériques](#t2)
	1. [Consulter les sites web ](#t2-1)
	2. [POP : la plateforme ouverte du patrimoine ](#t2-2)
	3. [Mérimée : à vous de jouer ! ](#t2-3)
	4. [Exporter les résultats depuis Mérimée ](#t2-4)
	5. [Extraire les données par des expressions régulières ](#t2-5)
	6. [Gertrude : l'Inventaire général des Pays de la Loire ](#t2-6)

[comment]: <> (FINET)


<a id='t1'/>

# Modéliser un objet d'étude
[comment1]: <1> (TITRE1)


<a id='t1-1'/>

## Qu'est-ce que modéliser ? 

### <2>

**Modéliser** : opération qui consiste à créer la représentation d'un objet ou d'un système complexe afin de pouvoir l'analyser par des techniques d'ingénierie documentaire.

**Étapes de la modélisation** :

1. *Exploration* : définir l'objet

	- Quel objet ?
	- Quel périmètre d'étude ?
		
		- Quelle chronologie ?
		- Quel espace ?
		- Quelles sources ?


### <3>

2. *Modèle conceptuel* : analyser les éléments constitutifs de l'objet
	
	- Quels éléments ?
	- Quelles relations des éléments entre-eux ?

3. *Prospective* : poser des objectifs
	
	- Conservation
	- Etude : questions que l'on posera à l'objet
	- Valorisation


### <4>

Les ponts dits romains… sont souvent médiévaux !

[comment3]: <4> (Il n'est pas du tout certain que la voie romaine Chartres-Le Mans traversait l'Huisne à cet emplacement ; c'est au Moyen Âge que cet axe devient important pour relier Le Mans et Paris.)

**Image** : [Le pont dit Romain de Montfort-le-Gesnois, Sarthe, 1^re^ moitié XV^e^ s.<a date='sans'/>](img/img_10e0aa33-b8e9-4731-995e-83897f815155.jpg)


### <5>

Le pont le plus anciennement attesté en Pays de la Loire :\
le Grand Pont d'Angers (Grégoire de Tours, 590).


**Image** : [Angiers fait della main du capite Ercules conte de Senfront, v. 1590, Archives de l'État de Turin](img/img_0e1c4490-d6ab-4c9b-bd2a-a5929150ce1c.jpg)


### <6>

[comment4]: <6> (Le plus vieux pont conservé en PDL :)

**Image** : [Vieux Pont de Laval, XIII^e^ s.](img/img_laval.jpg)


### <7>

Et en Loire-Atlantique…

**Image** : [Pont de la Chalandière dit aussi de l'Arche, Thouaré-sur-Loire, Moyen Âge ?](img/img_5528c7dc-9f45-4974-b5c0-bbc262a1f347.jpg)


### <8>


Jusqu'aux **ouvrages d'art** les plus récents…


**Image** : [Construction du pont de Cheviré, Nantes, achevé en 1990](img/img_985b86c3-fa3a-4538-a4da-2adc8c33c00b.jpeg)

**Image** : [Vu depuis le terminal à bois vers les quais de la Roche-Maurice](img/img_ef409199-d761-464b-ac02-eb7a7b37e80b.jpeg)


### <9>

1. Site de l'Inventaire général des Pays de la Loire

	- [Notice 1](https://gertrude.paysdelaloire.fr/dossier/IA49000842)
	- [Notice 2](https://gertrude.paysdelaloire.fr/dossier/IA85001933)

2. Base Mérimée

	- [Notice 3](https://pop.culture.gouv.fr/notice/merimee/IA49000843)

**Questions :**

- Quelles sont les informations essentielles qui permettront de caractériser un pont ? (7 max.)
- Quelles sont les entités (ou concepts) principales qui vont graviter autour ? Quels attributs (ou informations) vont les caractériser à leur tour ? (5 max.)

[comment5]: <9> (Remarque : un pont est-il une architecture ou un point --immatériel-- de franchissement ?)

[comment6]: <9> (- architecture : base orientée objet archéologique ; selon les sources, on pourra documenter plusieurs architectures consécutives ; on aura donc potentiellement plusieurs items au même point de franchissement)

[comment7]: <9> (- point de franchissement : on rassemblera les données de différentes époques dans autour du même item)

[comment8]: <9> (Il faut donc se demander ce qui est le plus important pour nous.)

[comment9]: <9> (Revenons à l'idée du phasage : le cas du Grand Pont d'Angers est intéressant. On peut rattacher à chaque entité *pont* des entités *phases*, qui se distinguent par la date, les matériaux, les sources qui s'y rattachent --icono par exemple--. On voit que le site de l'inventaire comme la base POP --uniquement l'API-- font plus simple : rassembler toutes les données de phase et d'histoire dans une seule notice : l'utilisateur interprétera lui-même l'information « Haut Moyen Âge » en lisant l'ensemble de la notice.)


### <10>


**Image** : [Schéma **yEd**<a date='sans'/>](img/bdd-ponts_01-initial.gif)

\vskip -1em

Exemple de données dans un [premier tableur](https://github.com/sbiay/td-num-vnp/raw/main/tableurs/angers-saumur.ods)

[comment10]: <10> (Il présente dans une première feuille ou table les données « à plat », toutes ensemble.)


<a id='t1-2'/>

## Rappel : vocabulaire 

### <11>

- **Entité** : type d'objet pouvant être décrits par une même liste fermée d'attributs
	- Egalement dénommé : classe, *record type*
	- Exemples : pont, personne, lieu, source iconographique, source bibliographique, source archivistique, etc.

- **Attribut** : caractéristique d'une entité permettant de distinguer des enregistrements
	
	- Egalement dénommé : champ, *field*
	- Exemples : 
		- Pour une entité *personne* : nom, prénom, date de naissance, etc.


<a id='t1-3'/>

## Prospective 

### <12>

- Etablir une cartographie des ponts conservés
- Interroger le corpus par les personnes (architectes)
- Interroger le corpus par les matériaux
- Interroger le corpus par la chronologie
- …


<a id='t1-4'/>

## Du modèle conceptuel au m. logique : cardinalité 

### <13>

[comment14]: <13> (Rien qu'avec 8 ponts, on a dès données déjà encombrantes :)

[comment15]: <13> (1. Pénibles à visualiser, car il faut voyager entre les colonnes)
[comment16]: <13> (2. Risqué pour ajouter des données)

[comment17]: <13> (J'ajoute un pont à Angers, ce sont quatre champs de localisation que je dois copier et coller.)

[comment18]: <13> (Les lieux sont un problème simple parce qu'on va admettre qu'un pont n'est rattaché qu'à une seule commune.)

[comment19]: <13> (Un lieu est une **clé étrangère** dans la table pont.)

[comment20]: <13> (**Passons aux matériaux** : ils sont regroupés dans un seul champ --C--, mais on voit que les valeurs sont multiples.)

[comment21]: <13> (Tous les ponts de ces exemples sont constitués de plusieurs matériaux. Est-ce un problème de les organiser ainsi ? Cela permet de trouver l'information, mais si l'on veut porter une attention particulière aux matériaux dans notre corpus, si on a pour objectif de permettre de trier des résultats de notre base par facettes selon les matériaux, alors il faut leur donner une table séparée.)

[comment22]: <13> (Maintenant, comment mettre en relation plusieurs ponts avec plusieurs matériaux ?)

[comment23]: <13> (Il sera nécessaire de créer une **table de relation**.)

**Image** : [Diagramme entité-association](img/bdd-ponts_01-cardinalites.gif)


### <14>

Pour aller plus loin sur le diagramme entité-association, voir [cette page](https://www.lucidchart.com/pages/fr/diagramme-entite-association)


<a id='t2'/>

# Interroger les ressources numériques
[comment24]: <14> (TITRE1)

[comment25]: <14> (L'un des enjeux majeurs de ce TD est de vous apprendre à récolter le plus de données possibles de manière automatisée, plutôt que de faire 10 000 copier-coller.)


<a id='t2-1'/>

## Consulter les sites web 

### <15>

- Quels sont les sites me permettant d'accéder à de l'information sur le sujet ?
- Quelles informations me donnent-ils ?
	- Couverture du sujet
	- Quantité de données
	- Qualité des données
- Comment récolter leurs données pour les exploiter ?

Navigateur recommandé : **Firefox**


### <16>

Un article [Liste des ponts de France](https://fr.wikipedia.org/wiki/Liste_de_ponts_de_France)

- Vieux Pont de Laval ? *absent*
- Pont sur l'Huisne à Montfort-le-Gesnois ? *absent*
- Pont de Cheviré ? *absent*

Des données beaucoup trop lacunaires pour être utiles !


<a id='t2-2'/>

## POP : la plateforme ouverte du patrimoine 

### <17>

 [https://pop.culture.gouv.fr/](https://pop.culture.gouv.fr/)


\vskip 2em

- Collections des musées de France : la base Joconde

- Patrimoine mobilier : la base Palissy

- Photographies : la base Mémoire

- Patrimoine architectural : la base [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)

- Etc.


<a id='t2-3'/>

## Mérimée : à vous de jouer ! 

### <18>

1. Avant de commencer, lire le [bref descriptif](https://www.culture.gouv.fr/espace-documentation/Bases-de-donnees/Fiches-bases-de-donnees/Merimee-une-base-de-donnees-du-patrimoine-monumental-francais-de-la-Prehistoire-a-nos-jours) de la base et de ce qu'elle contient

	- Le domaine **Monuments historiques** (national) : notices PA
	- Le domaine **Inventaire général** des services régionaux : notices IA

2. Chercher tous les ponts de la région Pays de la Loire sur [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)

	- Il faut aboutir à une liste de 112 résultats
	- Et pour l'instant on ne va pas voir la solution dans la suite du diaporama !
	- Si vous trouvez très vite : cherchez les ponts du seul département de la Vendée (14 résultats)


### <19>

**Il faut comprendre comment fonctionne la recherche avancée** :

- Par une recherche simple, trouver n'importe quelle notice de pont

- Identifier les champs pertinents pour croiser le type de monument cherché et la localisation

- Examiner le menu déroulant des champs interrogeables en recheche avancée : les premiers sont multiples, puis ce sont des champs simples classés par ordre alphabétique de leurs abréviations


### <20>

- La recherche la plus pertinente pour le type :\
**DENO** (dénomination) *contient* « pont »

[comment29]: <20> (Si l'on utilise le champ **Désignation**, on obtient du bruit, avec des ponts en tant que partie constitutive d'un ensemble plus vaste, comme un village --155 résultats--.)

- La recherche la plus pertinente pour la localisation :\
**REG** (région) *égal à* « Pays de la Loire »

- Utiliser l'opérateur booléen **ET**


Voici les [résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D) !

Pour la recherche sur un département précis, il faut chercher :

- **DPT** (département) *égal à* 85
- ou bien **DPT_LETTRE** (département) *égal à* Vendée.


### <21>

**On sauvegarde la recherche** dans son navigateur avec un marque-page :

- Ouvrir le volet des marque-pages : Ctrl + B
- Dans le Menu des marque-pages créer des dossiers :

`TD-ponts/`

- => `Ponts`\
- =>	=> `Sites`

- Ajouter la page des résultats comme marque-page : Ctrl + D
- Trouver le dossier via **Choisir**
- Renommer le marque-page, par exemple :\
`rech Mérimée PDL`


<a id='t2-4'/>

## Exporter les résultats depuis Mérimée 

### <22>

[comment31]: <22> (Comment récupérer ces informations pour en faire un tableau de données ?)

- Ajouter quelques résultats de la liste au **Panier**
- Tenter l'export du Panier…

Un export PDF est particulièrement difficile à convertir en tableau…


### <23>

Les [112 résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D) obtenus de la base Mérimée via le site POP sont toujours un ensemble de PDF…

Vous pouvez les télécharger [ici](https://github.com/sbiay/td-num-vnp/tree/main/pdf)

Il s'agit à présent de convertir tout ou partie du contenu de ces PDF en un unique tableau de données.


<a id='t2-5'/>

## Extraire les données par des expressions régulières 

### <24>

Extraire des données d'un PDF est l'une des opérations les plus délicates en ingénierie des données…

- Ouvrir les PDF dans **Firefox** (d'autres visualiseurs pourraient donner des résultats inégaux)
- Rassembler par copier-coller le contenu des trois PDF dans un seul **éditeur de texte**
- Ouvrir un tableau dans LibreOffice Calc pour recevoir les données
- Y créer les en-têtes sur la première ligne : `identifiant`, `nom`, `localisation`


### <25>

Réfléchissons à la meilleure stratégie pour récupérer les données :

- Dans quelle mesure sont-elles régulières ou irrégulières ?
- Quelles sont les irrégularités qui peuvent poser problème ?
- Sur quelle régularité peut-on s'appuyer pour capturer tout ou partie de l'information ?


### <26>

Irrégularités :

- Les notices n'ont pas toujours le même nombre de lignes !
- Tous les titres ne commencent pas par « pont »


3 régularités à exploiter :

1. Les identifiants des notices sont toujours formés de la même manière : 10 caractères commençant par `IA` ou `PA`

2. La localisation commence toujours par `Pays de la Loire`

3. Le nom de l'édifice est toujours après un numéro d'identifiant ou après des numéros de pages ; mais attention ! c'est l'identifiant de la notice d'avant !

Essayez de composer des expressions régulières pour sélectionner ces éléments.


### <27>

**Récupérer les identifiants**

- Dans l'éditeur de texte, ouvrir la boîte de dialogue de recherche (**Ctrl + F**)
- Accéder à l'onglet **Marquer**
- Vérifier que les expressions régulières sont activées
- Chercher : `[I|P]A[\d]{8}`
- Rechercher tout
- Copier le texte marqué
- Coller (Ctrl + Maj + V) dans la 1^re^ colonne du tableau à partir de la 2^e^ ligne (on mettra en 1^re^ ligne : `identifiant`)


### <28>

**Récupérer le nom**

On sait que les noms se trouvent sur les lignes qui suivent celles des identifiants :

- Tester la recherche suivante : `[P|I]A[\d]{8}\n[^\n]+`

	
	L'expression signifie : *un identifiant, suivi d'un retour à la ligne, puis d'une ligne avec tous ses caractères (de un à une infinité de caractères sauf un retour à la ligne)*
	

- Rechercher tout
- Parcourir les résultats signalés dans le texte… Est-ce satisfaisant ?


### <29>

**Récupérer le nom**

On ne capture pas tous les noms correctement.
Il faut procéder à des nettoyages :

- Eliminer les numéros de pages (ils s'interposent entre des identifiants et des noms)

	- Chercher : `\n\d+ / \d+`
	- Remplacer par : *vide*


### <30>

**Récupérer le nom**

Il faut aussi éliminer les titres des documents PDF qui poseront le même problème :

`Panier de notices`\
`50 notices`

- Le faire à la main ou par une expression régulière de votre invention… (le nombre de notices n'est pas de « 50 » dans la dernière partie du fichier)


### <31>

**Récupérer le nom**

- Ouvrir un second document vide dans l'éditeur de textes (Ctrl + N)

- Chercher : `[P|I]A[\d]{8}\n[^\n]+`

- Coller dans le nouveau document


### <32>

**Récupérer le nom**

- Dans ce nouveau document, on veut éliminer toutes les lignes qui ne sont pas le nom de l'édifice
	- Les lignes contenant `----`
	- Les identifiants
		- Chercher : `[P|I]A[\d]{8}\n`
		- Remplacer par : *vide*

- Copier toutes les lignes restantes et les coller dans le tableau : **Ctrl + Maj + V**

Le résultat est-il satisfaisant ?


### <33>

**Récupérer le nom**

Le premier nom de la liste n'a pas pu être attrappé par notre méthode !

- Décaler toutes les données de la colonne des noms d'une ligne vers le bas
- Coller à la main le nom du premier enregistrement


### <34>

**Récupérer la localisation**

Ce n'est pas le plus difficile, puisque la localisation commence toujours par « Pays de la Loire ».

À vous de composer l'expression régulière pour capturer toute cette ligne et la coller dans le tableau.

L'information « Pays de la Loire » n'étant pas utile pour nous, on peut ensuite l'éliminer de la colonne C du tableau :

- Cliquer sur **C** pour sélectionner toute la colonne
- Ouvrir la boîte de dialogue pour chercher-remplacer : **Ctrl + H**
- Bien cocher : Autres options > Sélection active seulement
- Compléter judicieusement les champs **Rechercher** et **Remplacer**


### <35>

**Félicitations !**

Vous avez extrait les principales données d'un PDF et les avez rendues exploitables en tant que tableau.

Le résultat peut se retrouver dans [ce fichier](https://github.com/sbiay/td-num-vnp/raw/main/csv/merimee-export-manuel.csv)


<a id='t2-6'/>

## Gertrude : l'Inventaire général des Pays de la Loire 

### <36>

 [https://gertrude.paysdelaloire.fr/](https://gertrude.paysdelaloire.fr/)


Une compétence régionale depuis 2004

**Même exercice** :

- Chercher tous les ponts de la région Pays de la Loire
	- Il faut aboutir à une liste de 121 résultats
- Tenter d'exporter ces résultats


### <37>

Les critères de la recherche avancée doivent être :\
**(Type de dossier : Oeuvre architecture)\
ET\
(Dénomination : pont)**

Voici la [liste des résultats](https://gertrude.paysdelaloire.fr/recherche/experte/results?q=(typeDossiers:(OeuvreArchitecture),blocs:((id:e86ca9bb-906e-4f97-ba74-f1de08f543b3,thematiqueType:TYPE_OEUVRE,operateur:AND,criteres:((id:df7152f4-f47a-4a52-85fb-d9c4ad6d3b4c,champRecherche:TYPE_OEUVRE_DENOMINATION,valeur:http!:%2F%2Fwww.culture.fr%2Fthesaurus%2FL96-2280,operateur:EQUAL,label:pont,ancestorLabels:(g%C3%A9nie+civil,ouvrage+d%27art))),position:0))))

