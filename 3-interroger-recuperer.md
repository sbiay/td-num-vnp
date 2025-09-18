---
mainfont: Alegreya
title: Interroger des ressources, récupérer des données
date: 1^er^ semestre 2025-2026
author: sebastien.biay@univ-nantes.fr
---

Interroger des ressources, récupérer des données
=====

Plan :

1. [Explorer](#t1)
	1. [Des plus anciens… ](#t1-1)
	2. [Aux plus récents ](#t1-2)
	3. [Consulter les ressources en ligne ](#t1-3)
2. [Interroger](#t2)
	1. [POP : la plateforme ouverte du patrimoine ](#t2-1)
	2. [Mérimée : à vous de jouer ! ](#t2-2)
	3. [Exporter les résultats depuis Mérimée ](#t2-3)
	4. [Extraire les données par des expressions régulières ](#t2-4)
	5. [Gertrude : l'Inventaire général des Pays de la Loire ](#t2-5)

<!--FINET-->


<a id='t1'/>

# Explorer
[comment1]: <1> (TITRE1)

<a id='t1-1'/>

## Des plus anciens… 

### <2>

Les ponts dits romains… sont souvent médiévaux !

[comment3]: <2> (Il n'est pas du tout certain que la voie romaine Chartres-Le Mans traversait l'Huisne à cet emplacement ; c'est au Moyen Âge que cet axe devient important pour relier Le Mans et Paris.)

**Image** : [Le pont dit Romain de Montfort-le-Gesnois, Sarthe, 1^re^ moitié XV^e^ s.](img/img_10e0aa33-b8e9-4731-995e-83897f815155.jpg)


### <3>

Le pont le plus anciennement attesté en Pays de la Loire :\
le Grand Pont d'Angers (Grégoire de Tours, 590).

**Image** : [Angiers fait della main du capite Ercules conte de Senfront, v. 1590, Archives de l'État de Turin](img/img_0e1c4490-d6ab-4c9b-bd2a-a5929150ce1c.jpg)


### <4>

[comment4]: <4> (Le plus vieux pont conservé en PDL :)

**Image** : [Vieux Pont de Laval, XIII^e^ s.](img/img_laval.jpg)


### <5>

Et en Loire-Atlantique…

**Image** : [Pont de la Chalandière dit aussi de l'Arche, Thouaré-sur-Loire, Moyen Âge ?](img/img_5528c7dc-9f45-4974-b5c0-bbc262a1f347.jpg)


<a id='t1-2'/>

## Aux plus récents 

### <6>


**Image** : [Construction du pont de Cheviré, Nantes, achevé en 1990](img/img_985b86c3-fa3a-4538-a4da-2adc8c33c00b.jpeg)

**Image** : [Vue depuis le terminal à bois vers les quais de la Roche-Maurice](img/img_ef409199-d761-464b-ac02-eb7a7b37e80b.jpeg)


<a id='t1-3'/>

## Consulter les ressources en ligne 

### <7>

- Quels sont les sites me permettant d'accéder à de l'information sur le sujet ?

- Quelles informations me donnent-ils ?
	
	- Couverture du sujet
	- Quantité de données
	- Qualité des données

- Comment récolter leurs données pour les exploiter ?

Navigateur recommandé : **Firefox**

### <8>

1. Wikipédia : un article [Liste des ponts de France](https://fr.wikipedia.org/wiki/Liste_de_ponts_de_France)

	- Vieux Pont de Laval ? *absent*
	- Pont sur l'Huisne à Montfort-le-Gesnois ? *absent*
	- Pont de Cheviré ? *absent*

	Des données beaucoup trop lacunaires pour être utiles !

2. Wikidata : [point d'entrée sparql](https://query.wikidata.org/)\
	Des données pauvres mais très exhaustives.

3. Site de l'Inventaire général des Pays de la Loire

	- [Notice](https://gertrude.paysdelaloire.fr/dossier/IA49000842)
	- [Notice](https://gertrude.paysdelaloire.fr/dossier/IA85001933)

4. Base Mérimée

	- [Notice](https://pop.culture.gouv.fr/notice/merimee/IA49000843)


<a id='t2'/>

# Interroger
[comment7]: <8> (TITRE1)


<a id='t2-1'/>

## POP : la plateforme ouverte du patrimoine 

### <9>

 [https://pop.culture.gouv.fr/](https://pop.culture.gouv.fr/)


- Collections des musées de France : la base Joconde

- Patrimoine mobilier : la base Palissy

- Photographies : la base Mémoire

- Patrimoine architectural : la base [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)

- Etc.


<a id='t2-2'/>

## Mérimée : à vous de jouer ! 

### <10>

1. Avant de commencer, lire le [bref descriptif](https://www.culture.gouv.fr/espace-documentation/Bases-de-donnees/Fiches-bases-de-donnees/Merimee-une-base-de-donnees-du-patrimoine-monumental-francais-de-la-Prehistoire-a-nos-jours) de la base et de ce qu'elle contient

	- Le domaine **Monuments historiques** (national) : notices PA
	- Le domaine **Inventaire général** des services régionaux : notices IA

2. Chercher tous les ponts de la région Pays de la Loire sur [Mérimée](https://pop.culture.gouv.fr/search/mosaic?base=%5B%22Patrimoine%20architectural%20%28M%C3%A9rim%C3%A9e%29%22%5D)


### <11>

[comment10]: <11> (Si on procède par filtres, on obtient au moins 155 ponts ; mais on obtient aussi Village, Château fort --avec pon comme partie constituante--.)

[comment11]: <11> (Est-il préférable d'avoir trop ou pas assez ? Dans notre cas la différence entre)


**Filtres :**

- Donne un plus grand nombre de réponses

**Recherche avancée :**

- La recherche la plus pertinente pour le type :\
**DENO** (dénomination) *contient* « pont »

[comment12]: <11> (Si l'on utilise le champ **Désignation**, on obtient du bruit, avec des ponts en tant que partie constitutive d'un ensemble plus vaste, comme un village --155 résultats--.)

- La recherche la plus pertinente pour la localisation :\
**REG** (région) *égal à* « Pays de la Loire »

- Utiliser l'opérateur booléen **ET**


Voici les [résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D) !

Pour la recherche sur un département précis, il faut chercher :

- **DPT** (département) *égal à* 85
- ou bien **DPT_LETTRE** (département) *égal à* Vendée.


### <12>

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


<a id='t2-3'/>

## Exporter les résultats depuis Mérimée 

### <13>

[comment14]: <13> (Comment récupérer ces informations pour en faire un tableau de données ?)

- Ajouter quelques résultats de la liste au **Panier**
- Tenter l'export du Panier…

Un export PDF est particulièrement difficile à convertir en tableau…


### <14>

[112 résultats](https://pop.culture.gouv.fr/advanced-search/list/merimee?qb=%5B%7B%22field%22%3A%5B%22DENO.keyword%22%5D%2C%22operator%22%3A%22%2A%22%2C%22value%22%3A%22pont%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A0%7D%2C%7B%22field%22%3A%5B%22REG.keyword%22%5D%2C%22operator%22%3A%22%3D%3D%22%2C%22value%22%3A%22Pays%20de%20la%20Loire%22%2C%22combinator%22%3A%22AND%22%2C%22index%22%3A1%7D%5D) obtenus de la base Mérimée via le site POP sont toujours un ensemble de PDF…

Télécharger les trois fichiers pdf d'export de Mérimée sur Madoc.

Il s'agit à présent de convertir tout ou partie du contenu de ces PDF en un unique tableau de données.


<a id='t2-4'/>

## Extraire les données par des expressions régulières 

### <15>

Extraire des données d'un PDF est l'une des opérations les plus délicates en ingénierie des données…

- Ouvrir les PDF dans **Firefox** (d'autres visualiseurs pourraient donner des résultats inégaux)
- Rassembler par copier-coller le contenu des trois PDF dans un seul **éditeur de texte** : Notepad ++
- Ouvrir aussi un tableau dans LibreOffice Calc pour recevoir les données
- Y créer les en-têtes sur la première ligne : `identifiant`, `nom`, `localisation`


### <16>

Réfléchissons à la meilleure stratégie pour récupérer les données :

- Sur quelle régularité peut-on s'appuyer pour capturer tout ou partie de l'information ?
- Quelles sont les irrégularités qui peuvent poser problème ?


### <17>

Irrégularités :

- Les notices n'ont pas toujours le même nombre de lignes !
- Tous les titres ne commencent pas par « pont »


3 régularités à exploiter :

1. Les identifiants des notices sont toujours formés de la même manière : 10 caractères commençant par `IA` ou `PA`

2. La localisation commence toujours par `Pays de la Loire`

3. Le nom de l'édifice est toujours après un numéro d'identifiant ou après des numéros de pages ; mais attention ! c'est l'identifiant de la notice d'avant !


### <18>

**Récupérer les identifiants**

- Dans l'éditeur de texte Notepad ++, ouvrir la boîte de dialogue de recherche (**Ctrl + F**)
- Accéder à l'onglet **Marquer**
- Vérifier que **Expression régulière** soit activé
- Sélectionner l'option **Purger à chaque fois**
- Chercher : `[I|P]A\d{8}`
- Rechercher tout
- Copier le texte marqué
- Le coller dans le tableau


### <19>

**Récupérer la localisation**

Ce n'est pas le plus difficile, puisque la localisation commence toujours par « Pays de la Loire ».

- Mark All : `Pays de la Loire[^\r]+`\
	(qui signifie `Pays de la Loire` suivi de plusieurs caractères qui ne sont pas un retour à la ligne)


### <20>

Sachant que cette localisation contient plusieus valeurs séparées par `;` on peut l'importer dans le tableau en plusieurs colonnes :

- **Ctrl + Maj + V**
- Choisir **Utiliser le dialogue d'importation**
- Options de séparateur : point-virgule

Ainsi on obtient plusieurs colonnes pour la région, le département et la commune.


### <21>

**Récupérer le nom**

On sait que les noms se trouvent sur les lignes qui suivent celles des identifiants :

- Tester la recherche suivante : `[P|I]A\d{8}\r\n[^\r]+`

	
	L'expression signifie : *un identifiant, suivi d'un retour à la ligne, puis d'une nouvelle ligne avec tous ses caractères (de un à une infinité de caractères sauf un retour à la ligne)*
	

- Rechercher tout
- Parcourir les résultats signalés dans le texte… Est-ce satisfaisant ?


### <22>


On ne capture pas tous les noms correctement.
Il faut procéder à des nettoyages :

- Eliminer les numéros de pages (ils s'interposent entre des identifiants et des noms)

	- Chercher : `\n\d+ / \d+\r`
	- Remplacer par : *vide*


### <23>


Il faut aussi éliminer les titres des documents PDF qui poseront le même problème :

`Panier de notices`\
`50 notices`

- Le faire à la main ou par une expression régulière de votre invention… (le nombre de notices n'est pas de « 50 » dans la dernière partie du fichier)


### <24>

On peut finalement sélectionner tous les noms avec les identifiants qui les précèdent :

- Mark : `[P|I]A\d{8}\r\n[^\r]+`
- Combien a-t-on de résultats ? Il en faut 111
- Coller dans un nouveau document Notepad ++

[comment16]: <24> (110 résultats au lieu de 112 :)
[comment17]: <24> (- Le 1^er^ n'est pas attrapé car il n'est pas précédé d'un identifiant)
[comment18]: <24> (- Les opérations précédentes ont pu créer un retour à la ligne l. 294)


### <25>


- Dans ce nouveau document, on veut éliminer toutes les lignes qui ne sont pas le nom de l'édifice
	- Les lignes contenant `\n----\r`
	- Les identifiants
		
		- Chercher : `\n[P|I]A\d{8}\r`
		- Remplacer par : *vide*

	- Les lignes vides qui peuvent rester

- Copier toutes les lignes restantes et les coller dans le tableau : **Ctrl + Maj + V**

Le résultat est-il satisfaisant ?


### <26>


Le premier nom de la liste n'a pas pu être attrappé par notre méthode !

- Décaler toutes les données de la colonne des noms d'une ligne vers le bas
- Coller à la main le nom du premier enregistrement


### <27>

**Félicitations !**

Vous avez extrait les principales données d'un PDF et les avez rendues exploitables en tant que tableau.

Voir ce [{vademecum}](https://github.com/sbiay/td-num-vnp/blob/main/tuto-regex.md) contenant les fondamentaux sur les expressions régulières


<a id='t2-5'/>

## Gertrude : l'Inventaire général des Pays de la Loire 

### <28>

 [https://gertrude.paysdelaloire.fr/](https://gertrude.paysdelaloire.fr/)


Une compétence régionale depuis 2004

**Même exercice** :

- Chercher tous les ponts de la région Pays de la Loire
	- Il faut aboutir à une liste de 121 résultats
- Tenter d'exporter ces résultats


### <29>

Les critères de la recherche avancée doivent être :\
**(Type de dossier : Œuvre architecture)\
ET\
(Dénomination : pont)**

Voici la [liste des résultats](https://gertrude.paysdelaloire.fr/recherche/experte/results?q=(typeDossiers:(OeuvreArchitecture),blocs:((id:e86ca9bb-906e-4f97-ba74-f1de08f543b3,thematiqueType:TYPE_OEUVRE,operateur:AND,criteres:((id:df7152f4-f47a-4a52-85fb-d9c4ad6d3b4c,champRecherche:TYPE_OEUVRE_DENOMINATION,valeur:http!:%2F%2Fwww.culture.fr%2Fthesaurus%2FL96-2280,operateur:EQUAL,label:pont,ancestorLabels:(g%C3%A9nie+civil,ouvrage+d%27art))),position:0))))


